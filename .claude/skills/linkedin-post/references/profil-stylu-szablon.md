# Profil stylu — jak zbudować głos klienta

Gdy piszesz dla kogoś innego niż Jacek, potrzebujesz profilu stylu tej osoby. Bez niego
tekst wyjdzie w domyślnym rejestrze i klient go nie rozpozna.

---

## Jak zbudować profil (procedura)

**Wejście:** 2–3 teksty napisane przez klienta. Najlepiej różne: post, mail do klienta,
fragment rozmowy albo transkrypcja nagrania. Transkrypcja mówionego jest szczególnie
wartościowa — pokazuje naturalny rytm.

**Kroki:**

1. Przeczytaj teksty i wypisz **dosłowne cytaty** — zdania charakterystyczne, powtarzające
   się konstrukcje, ulubione słowa. Nie parafrazuj, cytuj.
2. Wypełnij sekcje szablonu poniżej. Każde stwierdzenie o stylu popieraj cytatem.
3. Wygeneruj z tego **prompt systemowy** — zwięzły blok, który da się wkleić jako instrukcja
   startowa do dowolnego narzędzia.
4. Zapisz plik jako `profil-stylu-<imie>.md` i pokaż klientowi do potwierdzenia.
   To jego głos — ma prawo powiedzieć „tak nie mówię".

---

## Szablon

```markdown
# Profil stylu pisania — [Imię]

## Ton i temperatura
[Jaki jest rejestr? Ciepły czy chłodny, konfrontacyjny czy łagodny, ekspercki czy partnerski.
Jaki jest kluczowy zabieg, który buduje zaufanie u tego autora?]

## Struktura zdań i rytm
[Długość zdań. Czy używa krótkich uderzeń? Jak wyglądają akapity? Jaki jest rytm —
opisz go, a nie tylko nazwij.]
Cytaty: > "..."

## Głos i persona
[Która osoba gramatyczna? Czy autor jest fizycznie obecny w tekście? Czy pierwsza osoba
służy autorytetowi czy autopromocji?]

## Charakterystyczne konstrukcje
[2–4 wzorce, których autor używa regularnie. Każdy z cytatem.]

## Słownictwo
[Jakich słów używa? Jakich nigdy? Czy mówi językiem swojej dziedziny czy językiem klienta?]
Nigdy nie używa: [lista]

## Zasady, których nie łamie
[5–7 twardych reguł — to, co odróżnia ten głos od generycznego.]

## Temperatura emocjonalna
[Jak wygląda łuk tekstu od pierwszego do ostatniego zdania?]

---

# Prompt systemowy

Piszesz w stylu [Imię] — [kim jest, dla kogo pisze].

Ton: [3–4 słowa]
Temperatura: [jedno zdanie]

Zasady stylu:
- [5–7 punktów, imperatywnie]

Nigdy:
- [4–6 punktów]
```

---

## Przykład wypełnienia (fragment realnego profilu)

> **Ton i temperatura**
> Ciepły, ale bez cukierkowości. Bezpośredni do granic konfrontacji — i właśnie to buduje
> zaufanie, nie odpycha. Tekst ma temperaturę osobistej rozmowy z kimś, kto wie więcej niż ty,
> ale nie wynosi się nad ciebie.
> Kluczowy zabieg: mówi trudne rzeczy, zanim czytelnik zdąży się obronić. I robi to tak,
> że czytelnik czuje ulgę, nie atak.

> **Struktura zdań i rytm**
> Krótkie zdania używane jak uderzenia. Często jedno- lub dwuwyrazowe akapity:
> > *„Tylko że to nie działa."*
> > *„Nie widzisz jednego."*
> > *„Konkretnie."*
> Rytm: długie zdanie → pauza → krótkie uderzenie.

> **Charakterystyczne konstrukcje**
> Parafraza myśli czytelnika, potem obalenie:
> > *„Próbujesz to ogarnąć logicznie. Myślisz: może trzeba więcej pogadać… Brzmi sensownie.
> > Naprawdę. Tylko że to nie działa."*
> Wchodzi w głowę czytelnika, przyznaje mu rację — i dopiero wtedy przesuwa go dalej.

---

## Gdzie użyć gotowego promptu systemowego

Poza tym skillem prompt działa wszędzie, gdzie jest pole na instrukcję startową:
- Claude.ai — jako pierwsza wiadomość albo w projekcie
- ChatGPT — Ustawienia → Personalizacja → Instrukcje niestandardowe
- Make / n8n — pole „System message" w węźle z modelem
- Własny asystent — pole „System prompt"

---

## Czego nie robić

- Nie buduj profilu z jednego tekstu. Jeden tekst pokazuje sytuację, nie styl.
- Nie opisuj stylu przymiotnikami bez cytatów. „Ciepły i profesjonalny" nie znaczy nic.
- Nie mieszaj profilu klienta z tonem Jacka. To dwa różne głosy i mieszanka brzmi fałszywie.
- Nie zakładaj, że profil jest wieczny. Ludzie zmieniają sposób pisania — odświeżaj po
  większych zmianach w ofercie albo pozycjonowaniu.
