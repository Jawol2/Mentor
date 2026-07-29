# Skille w tym repo

## linkedin-post

Pipeline pisania postów na LinkedIn: **TEMAT → DRAFT → KRYTYKA**.

Zbudowany na bazie istniejących dokumentów roboczych z Dysku Google (mapa źródeł:
`linkedin-post/references/zrodla.md`).

### Instalacja

Skill działa automatycznie w sesjach Claude Code uruchomionych w tym repo — pliki
w `.claude/skills/` są wykrywane same.

Żeby był dostępny wszędzie, nie tylko w tym repo:

```bash
cp -r .claude/skills/linkedin-post ~/.claude/skills/
```

### Użycie

Wywołaj przez `/linkedin-post` albo po prostu poproś o post — skill uruchomi się sam
na frazach typu „napisz post na LinkedIn", „przerób to na posta", „zhumanizuj ten tekst".

### Czego skill nie robi

Nie publikuje. Nie ma connectora do LinkedIna — wyjściem jest tekst do wklejenia
plus instrukcja publikacji (rytm, pierwszy komentarz, obrazek).

### Powiązane skille

- `adwokat-diabla` — etap 3 pipeline'u wywołuje go dla postów sprzedażowych (protokół TEKST)
- `rada-mentorek`, `projektowanie-szkolen` — źródła surowca na etapie 1
