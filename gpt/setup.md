# Instrukcja konfiguracji Custom GPT

## Dlaczego GPT może zostać zablokowany publicznie

OpenAI blokuje publiczne GPT które zawierają:

| Trigger | Przykład | Rozwiązanie |
|---|---|---|
| Znaki towarowe w nazwie GPT | „LinkedIn Carousel Generator", „Instagram Creator" | Użyj neutralnej nazwy: „Carousel Post Creator" |
| Znaki towarowe w opisie publicznym | „karuzele LinkedIn", „posty na Instagram" | Opisuj funkcję: „karuzele do postów", „slajdy edukacyjne" |
| Imiona realnych osób jako wzorce | „styl Nicolasa Cole'a", „jak Justin Welsh" | Opisuj styl anonimowo: „styl minimalistyczny, typografia jako główny element" |
| Treści chronione prawem autorskim | Cytaty z książek, fragmenty cudzych postów | Parafrazuj lub usuń |
| Sugerowanie oficjalnego powiązania | „Oficjalny generator LinkedIn" | Nigdy nie używaj słów: oficjalny, autoryzowany, certyfikowany |

Zasada: **nazwy platform mogą pojawić się w system promptcie** (jako opis gdzie trafi wyjście), ale **nie w nazwie ani opisie publicznym GPT**.

---

## Co wgrać i gdzie

### 1. System Prompt

Otwórz ChatGPT → Explore GPTs → Create → Configure.

W polu **Instructions** wklej całą zawartość pliku `gpt/system-prompt.md`.

### 2. Baza wiedzy (Knowledge)

W sekcji **Knowledge** wgraj **4 pliki**:

| Plik do wgrania | Skąd | Rola |
|---|---|---|
| `instrukcje.md` | `gpt/knowledge/instrukcje.md` | **Plik sterujący** — pełne instrukcje działania |
| `hooki.md` | `references/hooki.md` | 6 formuł hooków z matrycą |
| `struktura.md` | `references/struktura.md` | Szablony slajdów i łuki narracyjne |
| `render.md` | `references/render.md` | Szablon HTML→PDF |

> **Dlaczego taki podział?** System prompt GPT ma limit znaków i jest skanowany pod kątem zasad (brand names, real persons). Plik `instrukcje.md` w Knowledge omija oba problemy — trafia do bazy wiedzy, nie do pola Instructions.

### 3. Capabilities

Włącz **Code Interpreter** (wymagane do generowania pliku HTML).

Wyłącz **Web Search** (nie jest potrzebne, może rozpraszać).

### 4. Nazwa i opis GPT

**Nazwa:** Carousel Post Creator

> Unikaj nazw zawierających znaki towarowe platform (LinkedIn, Instagram, TikTok) — OpenAI blokuje publiczne GPT z takimi nazwami. Użyj neutralnej nazwy opisującej funkcję.

**Opis (publiczny):**
> Tworzę profesjonalne karuzele do postów — czysty tekst, mocny kontrast typograficzny, zero grafik. Podaj temat lub zacznij od brainstormu. Dostajesz gotowy plik HTML → eksportujesz do PDF → wgrywasz jako dokument.

> Unikaj w opisie nazw platform (LinkedIn, Instagram) — to drugi najczęstszy trigger blokady. Opisuj funkcję, nie platformę docelową.

**Conversation starters** (opcjonalne, ułatwiają start):
- „Zrób karuzelę o [temat]"
- „Zacznijmy od brainstormu"
- „Karuzela o nawykach dla przedsiębiorców, 10 slajdów"
- „Mam pomysł na karuzelę, pomóż mi go rozwinąć"

---

## Jak działa baza wiedzy w GPT

GPT nie czyta plików jak Claude (przez ścieżki). Przeszukuje je semantycznie — gdy system prompt mówi „przeszukaj bazę wiedzy (plik: hooki)", GPT szuka treści związanej z hookami we wszystkich wgranych plikach.

Dlatego pliki referencyjne mają wyraźne nagłówki i sekcje — to poprawia trafność retrieval.

---

## Testowanie po konfiguracji

Po zapisaniu GPT przetestuj 3 scenariusze:

**Test 1 — Tryb generate:**
> „Zrób karuzelę o prokrastynacji dla właścicieli firm, 10 slajdów"

Oczekiwany wynik: wybór hooka + łuku → JSON → plik HTML do pobrania → instrukcja eksportu.

**Test 2 — Tryb brainstorm:**
> „Chcę zrobić karuzelę ale nie wiem od czego zacząć"

Oczekiwany wynik: 4 pytania jedno po jednym → propozycja łuku → generowanie.

**Test 3 — Kolor marki:**
> „Karuzela o sprzedaży B2B, mój kolor to #E63946, jestem Jan Kowalski"

Oczekiwany wynik: HTML z kolorem #E63946 jako accent i „Jan Kowalski" w podpisach.

---

## Różnice Claude vs GPT

| Element | Claude Code (skill) | Custom GPT |
|---|---|---|
| Trigger | `/linkedin-carousel` | Naturalna rozmowa |
| Pliki referencyjne | Ścieżki bezpośrednie | Knowledge (semantic search) |
| Render HTML | Generuje plik w repo | Code Interpreter → plik do pobrania |
| Brainstorm | Wbudowany w skill | Wbudowany w system prompt |
| Aktualizacja | Edytuj pliki w repo | Edytuj Instructions w GPT |
