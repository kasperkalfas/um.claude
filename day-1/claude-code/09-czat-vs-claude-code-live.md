# Zadanie 9: To samo zadanie w czacie i w Claude Code – porównanie na żywo

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok D, 60 min: Claude Code – pierwszy kontakt**).

**Cel:** zobaczyć obok siebie tę samą operację w Claude Czat i w Claude
Code – żeby różnica przestała być teoretyczna.
**Poziom:** podstawowy
**Czas:** ok. 8 minut

## Materiały

- Dwa okna na ekranie prowadzącego: przeglądarka z Claude Czat i Claude
  Code w folderze `test-claude-code`.
- Plik `zestawienie_przykladowe.xlsx` w obu miejscach.

## Kroki

1. **W Claude Czat:** wgrajcie plik (ikona wgrywania) i wyślijcie:

   ```
   Dodaj na dole wiersz „Razem" z formułą sumującą kolumny Kwota
   planowana i Kwota wykonana. Zwróć plik do pobrania.
   ```

   Po odpowiedzi trzeba **pobrać** plik i podmienić go na dysku.

2. **W Claude Code:** bez wgrywania, to samo polecenie:

   ```
   Dodaj w pliku zestawienie_przykladowe.xlsx wiersz „Razem" z formułą
   sumującą kolumny Kwota planowana i Kwota wykonana.
   ```

3. Claude Code pokaże, co zamierza zmienić, i poprosi o zgodę –
   zatwierdźcie.
4. **Sprawdź:** otwórzcie plik w Excelu. Wiersz „Razem" jest, a w komórce
   z sumą widać **formułę** (`=SUMA(...)`), nie wpisaną liczbę.

## Na co zwrócić uwagę

- Czat: wgraj → poczekaj → pobierz → podmień. Claude Code: poproś →
  gotowe, w tym samym miejscu.
- Przy jednym pliku różnica jest mała. Przy dwudziestu – to cały Dzień 2.
- Formuła zamiast liczby to zasada wspólna dla obu narzędzi.
