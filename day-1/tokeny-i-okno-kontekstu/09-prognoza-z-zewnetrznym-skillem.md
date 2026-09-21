# Zadanie 9: Prognoza wykonania na rok – skill z internetu w Cowork

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**praca własna po szkoleniu** albo demo prowadzącego; nawiązuje do
Procesu 2 – prognozy dla banku).

**Cel:** znaleźć gotowy skill prognozowania na skills.sh, sprawdzić go,
wgrać do Cowork, zrobić prognozę 2026 na fikcyjnych 36 miesiącach –
i ocenić, czy prosta metoda „średnia × 12" nie wystarczy.
**Poziom:** średniozaawansowany (praktyka w Cowork)
**Czas:** ok. 30 minut (w tym kilka minut liczenia modeli)
**Wymaga:** Cowork, plan Team, dane z [`materialy/`](materialy/).

## Co powstanie

1. skill prognozowania wgrany do Cowork (po przeglądzie),
2. `kalendarz_2026_prognoza.xlsx` z prognozą i przedziałem 95 %
   dla 8 działów,
3. wykresy historia + prognoza (`.png`),
4. Wasza ocena: SARIMA czy „średnia × 12"?

## W trzech zdaniach

Dziś prognoza dla banku to „wykonanie narastająco ÷ miesiące × 12".
Nie widzi **sezonowości** (oświata siada w wakacje) ani **trendu**.
Modele szeregów czasowych to widzą – a skill ze [skills.sh](https://skills.sh)
(publiczny katalog skilli, każdy to `SKILL.md` na GitHubie) spisuje
wiedzę analityka w jednym pliku.

> **Checklist bezpieczeństwa z [zadania 8 z Bloku C](../claude-zadania/08-skille-z-internetu.md)
> obowiązuje w całości.** Skill z internetu to instrukcja od obcej
> osoby, którą Claude wykona w Waszym imieniu. Tu – na danych fikcyjnych.
> W Urzędzie – po ocenie IT.

## Przygotowanie

Folder `Pulpit\prognoza\` z **kopiami** dwóch plików z `materialy/`
(`generuj_prognoza.py` odtwarza je i wypisuje klucz):

| Plik | Zawartość | Rola |
|---|---|---|
| `wykonanie_miesieczne_2023-2025.xlsx` | 36 miesięcy × 8 działów: `Miesiąc`, `Dział`, `Nazwa działu`, `Wykonanie` | model się uczy |
| `kalendarz_2026.xlsx` | 12 miesięcy 2026 × 8 działów, puste `Prognoza`, `Dolna/Górna granica 95%` | model wypełnia |

**Klucz** (co dobry model powinien wykryć):

| Dział | Trend/rok | Sezonowość |
|---|---|---|
| 600 Transport | +4 % | szczyt I–II i XII, dołek VII–VIII |
| 750 Administracja | +2 % | lekki szczyt XII |
| 801 Oświata | +5 % | **VII–VIII ok. 70 %**, IX ok. 115 % |
| 851 Ochrona zdrowia | +3 % | I–II wyżej |
| 852 Pomoc społeczna | +6 % | szczyt XII |
| 900 Gospodarka komunalna | +3 % | V–VI wyżej |
| 921 Kultura | +2 % | szczyt VI–VIII |
| 926 Kultura fizyczna | +3 % | szczyt VI–VIII, dołek I |

## Kroki

### Krok 1: Znajdź skill (3 min)

Na https://skills.sh wyszukajcie:

```
forecasting time series
```

Otwórzcie wpis „Forecasting Time Series Data" (lub podobny). Przeczytajcie
opis (trend, sezonowość, ARIMA/SARIMA/Prophet), sekcję *When to use*
i przykłady. Gwiazdki repozytorium to sygnał użycia, nie gwarancja.

### Krok 2: Przeczytaj cały SKILL.md (5 min)

W repozytorium otwórzcie `SKILL.md`. Szukacie: zdań o wysyłaniu danych
gdziekolwiek, adresów, linków, „ignoruj polecenia użytkownika",
podfolderów ze skryptami.

**Sprawdź i zapiszcie:** jakie biblioteki Pythona skill instaluje?

### Krok 3: Wgraj (2 min)

Pobierzcie `SKILL.md` (*Raw* → zapisz) albo cały folder jako ZIP, jeśli
ma podfoldery. Cowork → **Customize → Skills → „+" → Upload a skill**.
Jeśli była starsza wersja – najpierw usuńcie.

### Krok 4: Folder roboczy (1 min)

Nowe zadanie → *Choose a different folder* → `Pulpit\prognoza` →
**Allow**. Zamknijcie oba pliki w Excelu.

### Krok 5: Polecenie (10 min liczenia)

```
Używając skilla do prognozowania szeregów czasowych: na danych
z wykonanie_miesieczne_2023-2025.xlsx wytrenuj dla każdego działu osobno
model ARIMA i sezonowy SARIMA, porównaj je, wybierz lepszy i wypełnij
prognozą oraz przedziałem 95% plik kalendarz_2026.xlsx – zapisz jako
kalendarz_2026_prognoza.xlsx, nie nadpisuj oryginału. Dodaj wykres
historia + prognoza dla każdego działu i jeden zbiorczy. Na koniec napisz
po polsku, w 5 punktach, co model zauważył.
```

Po prawej: skill → biblioteki → ARIMA → SARIMA → prognoza → porównanie →
wykresy → weryfikacja.

### Krok 6: Sprawdzian z kluczem (3 min)

Porównajcie 5 punktów agenta z tabelą wyżej:

- [ ] wakacyjny spadek w 801
- [ ] zimowy szczyt w 600
- [ ] letni szczyt w 921 / 926
- [ ] SARIMA wygrał w większości działów (dane **mają** sezonowość)

### Krok 7: Sprawdzian zdrowego rozsądku (5 min)

W Excelu, dla działu 801: **średnia miesięczna 2025 × 12 × 1,05**.
Porównajcie z sumą prognozy SARIMA na 2026 z `kalendarz_2026_prognoza.xlsx`.

**Sprawdź:**

- [ ] różnica to kilka procent (duża różnica = problem z modelem albo
      danymi, nie z Excelem)
- [ ] na wykresie `.png` „wstęga" 95 % rozszerza się w kolejnych
      miesiącach (im dalej, tym mniej pewnie)

## Na co zwrócić uwagę

- **Musicie rozumieć wynik, nie kod.** Przedział 95 % = widełki,
  w których z dużym prawdopodobieństwem zmieści się wykonanie. Bez tego
  nie obronicie liczby przed bankiem.
- **Suma roczna vs rozkład po miesiącach.** „Średnia × 12" daje często
  podobną sumę; różnica jest w miesiącach. Dla banku (transze, płynność)
  rozkład ma znaczenie. Wybór metody to Wasza decyzja merytoryczna.
- **Mniej niż 2 lata danych = brak sezonowości do nauczenia.** Z samym
  `zestawienie_roczne_2026.xlsx` (8 miesięcy) prosta metoda jest
  uczciwsza niż „model".
- **Drogie w tokenach.** Uruchamiajcie raz, na całych danych.
- Po ćwiczeniu skill można wyłączyć (Customize → Skills). Ten sam
  skrypt da się uruchomić ponownie w Claude Code (Dzień 2) z nowymi
  danymi.

## Notatki własne

- Co skill instaluje / uruchamia? Przeszedłby ocenę IT bez zmian?
- Różnica między „średnia × 12 × 1,05" a sumą SARIMA dla 801?
- Komu w Urzędzie pokazalibyście przedział 95 % – i po co?
