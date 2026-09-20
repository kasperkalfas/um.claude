# Zadanie 9: Prognoza wykonania na rok – skill z internetu w Cowork

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**praca własna po szkoleniu** albo demo prowadzącego, jeśli zostanie czas;
nawiązuje do Procesu 2 – prognozy dla banku).

**Cel:** znaleźć gotowy skill w katalogu skills.sh, sprawdzić go, wgrać do
Cowork i użyć do prognozy miesięcznego wykonania wydatków na 2026 r. –
a potem ocenić, czy wynik nadaje się dla banku, czy prosta metoda
„średnia × 12" wystarczy.
**Poziom:** średniozaawansowany (praktyka w Cowork)
**Czas:** ok. 30 minut (w tym kilka minut liczenia modeli)
**Wymaga:** Cowork, konto w planie Team Urzędu; dane fikcyjne z
[`materialy/`](materialy/) (patrz niżej).

## Problem, który to rozwiązuje

W Procesie 2 prognoza roczna dla banku liczy się dziś prosto: wykonanie
narastająco ÷ liczba miesięcy × 12. Działa, ale nie widzi **sezonowości**
(oświata „siada" w wakacje, transport rośnie zimą) ani **trendu** (koszty
rosną rok do roku). Modele szeregów czasowych to widzą – tylko do tej pory
wymagały analityka z Pythonem. Skill w Cowork spisuje jego wiedzę w
jednym pliku, a Wy podajecie dane i pytanie.

## Skąd brać skille: katalog skills.sh

[skills.sh](https://skills.sh) to publiczny katalog skilli (dziesiątki
tysięcy pozycji: prezentacje, prognozy finansowe, kod, projektowanie…).
Każdy wpis prowadzi do repozytorium na GitHubie z plikiem `SKILL.md` –
tym samym formatem, który znacie z [zadania 7 z Bloku C](../claude-zadania/07-skill-notatka-budzetowa.md)
(nazwa i opis w nagłówku, potem: jak działa, kiedy się włącza, przykłady).

> **Checklist bezpieczeństwa z [zadania 8 z Bloku C](../claude-zadania/08-skille-z-internetu.md)
> obowiązuje w całości.** Skill ze skills.sh to instrukcja od obcej osoby,
> którą Claude wykona w Waszym imieniu. Na szkoleniu testujemy ją na
> danych fikcyjnych; w Urzędzie przed użyciem na czymkolwiek realnym
> skill (zwłaszcza ze skryptami `.py`) ocenia IT.

## Materiały

Folder roboczy na Pulpicie `Pulpit\prognoza\` z **kopiami** dwóch plików
z [`materialy/`](materialy/) (fikcyjne; `generuj_prognoza.py` odtwarza je
i wypisuje klucz odpowiedzi dla prowadzącego):

| Plik | Zawartość | Rola |
|---|---|---|
| `wykonanie_miesieczne_2023-2025.xlsx` | 36 miesięcy × 8 działów (600–926): `Miesiąc`, `Dział`, `Nazwa działu`, `Wykonanie` | dane historyczne – **na nich model się uczy** |
| `kalendarz_2026.xlsx` | 12 miesięcy 2026 × 8 działów, puste kolumny `Prognoza`, `Dolna/Górna granica 95%` | przyszłość – **to model ma wypełnić** |

W danych są celowe wzorce: sezonowość (np. 801 Oświata: VII–VIII ok. 70%
normy, IX ok. 115%; 600 Transport: I–II i XII wyżej), trend +2…+6% rocznie
zależnie od działu. Klucz: `python generuj_prognoza.py`.

## Kroki

1. **Znajdź skill.** Wejdźcie na https://skills.sh i wyszukajcie
   *forecasting time series*. Otwórzcie wpis „Forecasting Time Series
   Data" (lub podobny): przeczytajcie opis (analiza trendu i sezonowości,
   wybór modelu – ARIMA, SARIMA, Prophet – generowanie prognozy), sekcję
   *When to use* i przykłady. Zwróćcie uwagę na liczbę gwiazdek
   repozytorium – to nie gwarancja jakości, ale sygnał, że ktoś to
   używa.
2. **Sprawdź go (checklist).** Przejdźcie do repozytorium, otwórzcie
   `SKILL.md` i przeczytajcie **cały**: szukacie zdań o wysyłaniu danych
   gdziekolwiek, adresów, linków, instrukcji „ignoruj polecenia
   użytkownika". Zajrzyjcie, czy są podfoldery ze skryptami. Zapiszcie w
   „Notatkach", co skill instaluje (biblioteki Pythona) – to Cowork zrobi
   sam, ale warto wiedzieć, co.
3. **Pobierz i wgraj.** Pobierzcie `SKILL.md` (przycisk *Download* /
   *Raw* → zapisz). W Cowork: **Customize → Skills → „+" → Upload a
   skill** → przeciągnijcie plik. Jeśli skill ma podfoldery (skrypty,
   przykłady), pobierzcie cały folder i wgrajcie go jako ZIP – tak jak w
   zadaniu 8 z Bloku C. Po chwili skill pojawi się na liście z krótkim
   opisem. Jeśli był już wgrany wcześniej – najpierw usuńcie starą
   wersję.
4. **Folder roboczy.** Nowe zadanie → *Choose a different folder* →
   `Pulpit\prognoza` → **Allow**. Zamknijcie oba pliki w Excelu.
5. **Polecenie.** Wpiszcie (dokładnie tak, po polsku):
   *„Używając skilla do prognozowania szeregów czasowych: na danych z
   `wykonanie_miesieczne_2023-2025.xlsx` wytrenuj dla każdego działu
   osobno model ARIMA i sezonowy SARIMA, porównaj je, wybierz lepszy i
   wypełnij prognozą oraz przedziałem 95% plik `kalendarz_2026.xlsx` –
   zapisz jako `kalendarz_2026_prognoza.xlsx`, nie nadpisuj oryginału.
   Dodaj wykres historia + prognoza dla każdego działu i jeden zbiorczy.
   Na koniec napisz po polsku, w 5 punktach, co model zauważył."*
   Po prawej zobaczycie: wczytanie skilla → instalacja bibliotek →
   trenowanie ARIMA → SARIMA → prognoza → porównanie → wykresy →
   weryfikacja. Potrwa kilka minut.
6. **Sprawdzian z kluczem.** Gdy skończy, porównajcie 5 punktów agenta z
   kluczem z `generuj_prognoza.py`: czy wykrył wakacyjny spadek w 801?
   zimowy szczyt w 600? letni w 921/926? Czy SARIMA (sezonowy) wygrał w
   większości działów – tak powinno być, bo dane **mają** sezonowość.
7. **Sprawdzian zdrowego rozsądku.** W Excelu policzcie dla działu 801
   prostą prognozę: średnia miesięczna 2025 × 12 × 1,05. Porównajcie z
   sumą prognozy SARIMA na 2026 z `kalendarz_2026_prognoza.xlsx`. Różnica
   powinna być mała (kilka procent) – jeśli jest duża, coś jest nie tak
   **z modelem albo z danymi**, nie z Excelem. Otwórzcie też jeden wykres
   `.png` i sprawdźcie, czy „wstęga" przedziału 95% rozszerza się w
   kolejnych miesiącach (tak ma być: im dalej, tym mniej pewnie).

## Na co zwrócić uwagę

- **Skill ≠ kod, który musicie rozumieć.** Ale musicie rozumieć **wynik**:
  co to jest przedział 95% (widełki, w których z dużym prawdopodobieństwem
  zmieści się wykonanie), po co sezonowość, i kiedy prostsza metoda
  wystarcza. Bez tego nie obronicie liczby przed bankiem.
- **Roczna suma vs rozkład po miesiącach.** Prosta metoda „średnia × 12"
  daje często podobną **sumę roczną** co SARIMA – różnica jest w
  **miesiącach**. Dla banku (płynność, transze) rozkład miesięczny ma
  znaczenie; dla zestawienia „ile na koniec roku" – niekoniecznie.
  Wybór metody to Wasza decyzja merytoryczna.
- **Skill z internetu = obcy kod w Waszym imieniu.** Cowork instaluje
  biblioteki i uruchamia skrypty na Waszym komputerze. Na danych
  fikcyjnych – ćwiczenie; na realnych – dopiero po ocenie IT i za
  pisemną zgodą Zamawiającego (Blok B). Po ćwiczeniu skill można
  wyłączyć (Customize → Skills).
- **To drogie ćwiczenie w tokenach.** Trenowanie modeli dla 8 działów,
  wykresy i weryfikacja zużywają sporo limitu (zadanie 8, Settings →
  Usage). Uruchamiajcie raz, na całych danych – nie po kawałku.
- **Wszystko zostaje w folderze.** Prognoza `.xlsx`, wykresy `.png`,
  ewentualne skrypty `.py` – obok oryginałów. Jeśli chcecie powtórzyć za
  miesiąc z nowymi danymi, ten sam skrypt można uruchomić ponownie w
  Claude Code (Dzień 2) – bez ponownego „wymyślania" modelu.
- **Mniej niż 2 lata danych = nie ma sezonowości do nauczenia.** Dlatego
  w materiałach są 3 lata. Z samym `zestawienie_roczne_2026.xlsx`
  (8 miesięcy) SARIMA nie ma czego się uczyć – wtedy prosta metoda z
  Procesu 2 jest uczciwsza niż „model".

## Notatki własne

- Co skill instaluje / uruchamia (z kroku 2)? Czy w Urzędzie przeszedłby
  ocenę IT bez zmian?
- Ile wyniosła różnica między „średnia × 12 × 1,05" a sumą SARIMA dla
  działu 801?
- Do której sytuacji w Waszej pracy przedział 95% naprawdę by się przydał
  – i komu byście go pokazali?
