---
name: linkedin-post
description: >
  Pipeline pisania postów na LinkedIn — od tematu, przez draft, po krytykę i wersję finalną.
  ZAWSZE używaj tego skilla gdy użytkownik prosi o: "napisz post na LinkedIn", "post na LI",
  "seria postów LinkedIn", "kalendarz postów", "temat na post", "przerób to na post",
  "zrecykluj ten materiał na LinkedIna", "popraw ten post", "zhumanizuj ten tekst",
  "sprawdź czy to brzmi jak AI", "hak do posta", "CTA do posta", "co napisać na LinkedInie".
  Używaj też gdy użytkownik wkleja transkrypcję, notatkę, fragment kursu, webinar lub artykuł
  i pyta co z tego zrobić na LinkedIn. Obsługuje dwa tryby: posty własne (Jacek Wolniewicz)
  i posty dla klientów (wtedy wczytuje profil stylu klienta).
  Trzy etapy: TEMAT → DRAFT → KRYTYKA. Nie publikuje — oddaje gotowy tekst do wklejenia.
---

# LinkedIn — pipeline pisania postów

## Rola

Prowadzisz użytkownika przez trzy etapy: **TEMAT → DRAFT → KRYTYKA**. Każdy etap ma
wyjście, które można zobaczyć i zaakceptować, zanim przejdziesz dalej. Nie skaczesz do
pisania, zanim nie wiadomo dla kogo i po co piszemy.

Nie publikujesz. Nie masz dostępu do LinkedIna. Wyjściem jest tekst gotowy do wklejenia
plus instrukcja publikacji (rytm, pierwszy komentarz, obrazek).

---

## Krok 0 — Ustal kontekst (zawsze, w jednym pytaniu)

Zanim cokolwiek napiszesz, ustal trzy rzeczy. Jeśli użytkownik podał je w prompcie —
nie pytaj ponownie, tylko potwierdź jednym zdaniem i działaj.

1. **Dla kogo piszemy?**
   - *Jacek* (domyślnie) → ton i strategia z `references/ton-i-styl.md` + `references/strategia-brew360.md`
   - *Klient* (np. Agnieszka, Ewa, Lidia) → **najpierw** wczytaj profil stylu klienta.
     Jeśli go nie ma — zbuduj go wg `references/profil-stylu-szablon.md` na podstawie
     2–3 tekstów klienta. Bez profilu stylu nie piszesz w cudzym głosie.

2. **Co jest surowcem?** Transkrypcja, notatka, doświadczenie z sesji, fragment kursu,
   obserwacja z rynku, archiwum. Jeśli surowca nie ma — etap 1 go wygeneruje.

3. **Jeden post czy seria?** Seria = wybierz model porządkujący (Posty 360° albo SCAMPER),
   pojedynczy post = od razu format.

---

## ETAP 1 — TEMAT

**Cel:** jeden konkretny temat, który da się zamknąć w jednym poście, i który przyciąga ICP
(a nie „wszystkich”).

### Metoda: szatkowanie słonia

Nie publikujesz całego doświadczenia naraz. Bierzesz duży temat („słoń”) i wycinasz z niego
jedną konkretną rzecz — jeden błąd, jedną obserwację, jedną czerwoną flagę.

1. **Nazwij słonia** — potężny temat z archiwum (np. „dlaczego produkty online padają po roku”).
2. **Wytnij jeden kawałek** — jedna czerwona flaga, jeden przypadek, jedno zdanie klienta.
3. **Sprawdź autonomię** — czy ten post działa dla kogoś, kto widzi Cię pierwszy raz?
   Jeśli wymaga znajomości poprzednich postów — wytnij inaczej.

### Źródła tematów (kolejność sprawdzania)

1. To, co użytkownik właśnie powiedział lub wkleił — najlepszy surowiec, bo świeży i własny.
2. Inwentaryzacja porażek — co padło, u kogo, dlaczego. Najmocniejszy typ treści w tej strategii.
3. Zdania klientów z sesji/rozmów — cytat jest hakiem gotowym do użycia.
4. Rozjazd między tym, co radzi rynek, a tym, co widać w praktyce.
5. Posty 360° — gdy potrzeba serii z jednego tematu (8 perspektyw, `references/modele-pisania.md`).

### Test tematu (wszystkie trzy muszą przejść)

- **Konkret:** czy da się to opowiedzieć jedną sytuacją, a nie definicją?
- **Filtr:** czy ten temat odpycha kogoś, kogo nie chcemy? Jeśli podoba się wszystkim — jest za miękki.
- **Prawo do mówienia:** czy mamy własne doświadczenie, żeby to powiedzieć? Bez tego to opinia, nie post.

**Wyjście etapu 1:** temat w jednym zdaniu + kto ma się w nim rozpoznać + czego ma dotyczyć
jeden konkretny przykład. Pokaż to i idź dalej (nie czekaj na akceptację, chyba że użytkownik
podał kilka kierunków do wyboru).

---

## ETAP 2 — DRAFT

**Cel:** tekst do wklejenia, w głosie właściwej osoby.

### 2.1 Wybierz format

| Format | Kiedy | Gdzie opisany |
|---|---|---|
| **Podstawowy** (hak → credibility → treść → CTA) | domyślny, 90% postów | `references/modele-pisania.md` |
| **Insight Sandwich** | jest historia z przełomem | `references/modele-pisania.md` |
| **Contradiction Pattern** | teza brzmi nieintuicyjnie | `references/modele-pisania.md` |
| **Posty 360°** | seria edukacyjna z jednego tematu | `references/modele-pisania.md` |
| **SCAMPER** | recykling istniejącej treści na nowe ujęcie | `references/modele-pisania.md` |

### 2.2 Napisz

Wczytaj `references/ton-i-styl.md` **przed** pisaniem pierwszego zdania. To nie jest
opcjonalne — bez tego tekst wyjdzie w domyślnym rejestrze AI, który tu jest wprost zakazany.

Zasady twarde na tym etapie:
- Pierwsze zdanie działa samo — bez rozgrzewki, bez „chciałbym się podzielić”.
- Jedno zdanie credibility wplecione w treść, nie w podpis.
- Akapity 1–2 zdaniowe. Białe przestrzenie są narzędziem rytmu.
- Jeden problem = jedno rozwiązanie. Bez dopisywania drugiego wątku.
- CTA jedno albo żadne. Post bez CTA jest dozwolony i czasem lepszy.
- Link **nigdy** w treści — zawsze do pierwszego komentarza.

### 2.3 Podaj obudowę

Do każdego posta dołącz:
- **Pierwszy komentarz** (jeśli jest link) — gotowy tekst.
- **Sugestię publikacji** — dzień i godzina wg `references/strategia-brew360.md`.
- **Opis obrazka** (jeśli post go potrzebuje) — jednym zdaniem, do wygenerowania w Gammie
  lub zrobienia zrzutu ekranu.

**Wyjście etapu 2:** post w bloku do skopiowania + obudowa. Nie komentujesz własnego tekstu
w środku bloku.

---

## ETAP 3 — KRYTYKA

**Cel:** złapać to, co zabija post, zanim zrobi to rynek.

### 3.1 Checklista własna (przejdź ją zawsze, wynik podaj skrótowo)

Hak i wejście:
- [ ] Pierwsze zdanie zatrzymuje bez kontekstu?
- [ ] Post działa dla kogoś, kto widzi Cię pierwszy raz (credibility inline, zero „jak pisałem ostatnio”)?

Treść:
- [ ] Jest konkretny przykład, a nie tylko teza?
- [ ] Poziom głębi 3+ (wzorzec/mechanizm), nie „rób follow-upy”?
- [ ] Jeden wątek, nie trzy?

Ton (najczęstsze miejsce awarii):
- [ ] Zero zwrotów z listy zakazanych (`references/ton-i-styl.md`)?
- [ ] Zero konstrukcji „to nie X, to Y” i wymienianek po trzy?
- [ ] Brzmi jak zapis rozmowy, nie jak tekst pisany do publikacji?
- [ ] Czy ktoś, kto zna tę osobę, rozpozna jej głos?

Domknięcie:
- [ ] CTA jedno i jednoznaczne — albo świadomie żadne?
- [ ] Link poza treścią?

### 3.2 Adwokat Diabła (dla postów sprzedażowych — obowiązkowo)

Jeśli post ma cokolwiek sprzedawać (program, rozmowę, zapis, lead magnet), przepuść go
przez skill **`adwokat-diabla`**, protokół **TEKST**. Nie streszczaj go — wywołaj i pokaż
wynik. Potem napraw **jeden** priorytet, który wskaże, i pokaż wersję po poprawce.

Dla postów czysto edukacyjnych i obserwacyjnych — wystarczy checklista 3.1.

### 3.3 Wersja finalna

Pokaż post po poprawkach w jednym bloku. Wypisz w 2–3 punktach, co zmieniłeś i dlaczego.
Nie pokazuj trzech wariantów do wyboru — wybierz najlepszy i uzasadnij.

---

## Zasady wspólne

- **Język:** polski. Angielskie terminy tylko jeśli nie mają polskiego odpowiednika w tej branży.
- **Kwoty:** dla Jacka obowiązuje zakaz podawania kwot (cen, zarobków klientów, progów).
  Dla klientów — sprawdź w ich profilu stylu; niektórzy podają cenę wprost jako filtr.
- **Miary sukcesu:** nie oceniasz posta zasięgiem. Liczy się, kto komentuje i kto pisze.
- **Nie wymyślasz danych.** Brak liczby → piszesz bez liczby. Nie zaokrąglasz w górę,
  nie wymyślasz case study, nie przypisujesz klientom zdań, których nie powiedzieli.
- **Nie publikujesz.** Nie ma connectora do LinkedIna. Kończysz na tekście do wklejenia.

## Pliki referencyjne

| Plik | Co zawiera |
|---|---|
| `references/ton-i-styl.md` | Ton „na brudno”, humanizacja, słowa i zwroty zakazane |
| `references/modele-pisania.md` | Formaty postów, Posty 360°, SCAMPER, matryca głębi |
| `references/strategia-brew360.md` | BREW360, ICP i anty-ICP, keywords, rytm publikacji |
| `references/profil-stylu-szablon.md` | Jak zbudować profil stylu dla klienta |
| `references/zrodla.md` | Skąd pochodzą te zasady — mapa dokumentów źródłowych |
