# Zadanie 8: Od analizy do prezentacji dla przełożonego – skill statystyczny i PowerPoint

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**demo prowadzącego na koniec Bloku D** albo praca własna po szkoleniu;
kontynuacja [zadania 7](07-dashboard-z-wtyczka-data.md)).

**Cel:** uruchomić skill analizy statystycznej na danych z zadania 7,
zamienić wszystko w prezentację PowerPoint dla przełożonego i sprawdzić,
ile to kosztowało.
**Poziom:** średni (praktyka w Cowork)
**Czas:** ok. 20 minut
**Wymaga:** Cowork z wtyczką **Data**, folder `Pulpit\analiza-danych`
z wynikami zadania 7.

## Co powstanie

1. raport statystyczny z 3–5 „najsilniejszymi ustaleniami",
2. `wykonanie_2026_prezentacja.pptx` (maks. 8 slajdów),
3. zapis zużycia limitu przed i po (Settings → Usage).

## Skill a komenda

W zadaniu 7 używaliście **komend** – sztywnych przepływów krok po kroku.
**Skill** (np. `statistical-analysis`) to wiedza: agent sam planuje
podzadania i często uruchamia kilku subagentów równolegle. Po wpisaniu
`/` widać jedne i drugie, uruchamia się tak samo.

## Kroki

### Krok 0: Zapiszcie stan licznika (1 min)

Cowork → **Settings → Usage** → zapiszcie procent limitu tygodniowego
i sesji. W **Settings → Capabilities** sprawdźcie, że włączone są *code
execution* i *file creation* – bez nich skille Excel/PowerPoint nie
zadziałają.

### Krok 1: Analiza statystyczna (6 min)

W folderze `analiza-danych`: `/` → `statistical-analysis`:

```
Na pliku zestawienie_roczne_2026.xlsx, arkusz Wykonanie: statystyki
opisowe wykonania miesięcznego po działach, trend I–VIII, wartości
odstające, które działy odbiegają od reszty.
```

Po prawej podzadania (statystyki → odstające → różnice między działami
→ raport); równolegle skill Excel czyta arkusz.

### Krok 2: Sprawdźcie jeden wniosek ręcznie (3 min)

Agent pokaże 3–5 „najsilniejszych ustaleń". Wybierzcie jeden (np.
„dział 801 ma najwyższą zmienność miesięczną") i policzcie w Excelu
min/max w tym wierszu.

**Sprawdź:** jeśli wniosek jest ostrzejszy, niż uzasadniają liczby –
zapiszcie; użyjecie tego w kroku 4.

### Krok 3: Prezentacja (6 min)

Jedno polecenie, bez komendy:

```
Podsumuj wszystko, co wygenerowałeś w tym folderze (profil danych,
walidacja, dashboard, analiza statystyczna), w prezentacji PowerPoint
dla mojego przełożonego: maks. 8 slajdów, każdy slajd jedna myśl,
liczby w PLN z separatorem tysięcy, te same wykresy co w dashboardzie
(jako obrazy), na końcu wnioski i proponowane następne kroki.
Zapisz jako wykonanie_2026_prezentacja.pptx w tym folderze.
```

Jeśli macie pusty szablon Urzędu w folderze, dopiszcie:

```
Użyj szablonu szablon_UM.pptx.
```

Po prawej: projekt slajdów → plik → **konwersja do obrazów i kontrola
wizualna** → poprawki → oddanie. Agent ogląda własne slajdy, zanim Wy.

### Krok 4: Odbiór (3 min)

Otwórzcie `.pptx`. **Sprawdź:**

- [ ] min. 2 liczby ze slajdów zgadzają się z arkuszem
- [ ] wykresy mają podpisane osie i jednostki
- [ ] „zbyt ostry" wniosek z kroku 2 nie trafił na slajd bez złagodzenia
- [ ] slajd „następne kroki" proponuje coś, co sami byście zaproponowali

Poprawki zlecajcie konkretnie:

```
Na slajdzie 4 zamień wykres kołowy na słupkowy i dodaj wartości.
```

### Krok 5: Ile to kosztowało (1 min)

**Settings → Usage** – porównajcie z krokiem 0. Zapiszcie różnicę.

## Na co zwrócić uwagę

- **Model = jakość = koszt.** Opus daje najlepsze raporty i zużywa
  najwięcej. Do jednej tabeli czy wykresu wystarczy Sonnet/Haiku. Wybór
  *przed* uruchomieniem.
- **Jedno pełne przejście zadań 7–8 potrafi zjeść kilkanaście procent
  tygodniowego limitu.** Uruchamiajcie, gdy naprawdę robicie
  zestawienie.
- **Prezentacja od agenta = pierwsza wersja.** Dzień 3 (DataPOV) pokaże,
  jak z poprawnych slajdów zrobić przekonującą prezentację.
- **Szablon to nie dane** – pusty `.pptx` Urzędu można dać agentowi.
  Prezentacja z prawdziwymi liczbami – tylko za pisemną zgodą.
- **Na później:** Cowork → **Scheduled** – np. 1. dnia miesiąca „uruchom
  `/validate` na nowym eksporcie i przygotuj prezentację". Temat na
  koniec Dnia 2.

## Notatki własne

- Który wniosek sprawdziliście ręcznie i czy się potwierdził?
- Ile procent limitu tygodniowego zużyły zadania 7–8 razem?
- Co z prezentacji zostawilibyście, a co przepisali po swojemu?
