# Instrukcja konfiguracji Custom GPT

## Co wgrać i gdzie

### 1. System Prompt

Otwórz ChatGPT → Explore GPTs → Create → Configure.

W polu **Instructions** wklej całą zawartość pliku `gpt/system-prompt.md`.

### 2. Baza wiedzy (Knowledge)

W sekcji **Knowledge** wgraj 3 pliki:

| Plik do wgrania | Skąd |
|---|---|
| `hooki.md` | `references/hooki.md` |
| `struktura.md` | `references/struktura.md` |
| `render.md` | `references/render.md` |

Możesz je wgrać pod oryginalnymi nazwami — GPT będzie je przeszukiwał semantycznie.

### 3. Capabilities

Włącz **Code Interpreter** (wymagane do generowania pliku HTML).

Wyłącz **Web Search** (nie jest potrzebne, może rozpraszać).

### 4. Nazwa i opis GPT

**Nazwa:** LinkedIn Carousel Generator

**Opis (publiczny):**
> Tworzę profesjonalne karuzele LinkedIn w stylu typograficznym — tekst, kontrast, zero grafik. Podaj temat lub zacznij od brainstormu. Dostajesz gotowy plik HTML → eksportujesz do PDF → wgrywasz na LinkedIn.

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
