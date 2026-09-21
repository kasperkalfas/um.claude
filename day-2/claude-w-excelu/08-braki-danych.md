# Zadanie 8: Braki danych – znaleźć, policzyć i zdecydować, co z nimi zrobić

**Dzień 2, Blok B** · ok. 12 min · dodatek Claude w Excelu, **świeża kopia**
`Human_Resources.xlsx` (np. `_zad8`); Opus lub Sonnet. Zadanie czyta cały
arkusz – zużywa wyraźnie więcej limitu niż zad. 5–7.

**Cel:** znaleźć puste komórki, a potem – zamiast „uzupełnij" – przejść
przez opcje i wiedzieć, **których komórek nie wolno uzupełniać**.

## Polecenia

### 1. Ile i gdzie

> Ile pustych komórek jest w tych danych? Podaj rozbicie na kolumny i
> adresy.

Klucz: **13 pustych w 10 kolumnach, 7 wierszy**:

| Kolumna | Puste | Wiersze |
|---|---|---|
| `B` MonthlyIncome | 3 | 3, 8, 949 |
| `F` Department | 1 | 9 |
| `I` EducationField | 1 | 8 |
| `K` EmployeeNumber | 1 | 8 |
| `M` Gender | 1 | 8 |
| `Q` JobRole | 1 | 8 |
| `S` MaritalStatus | 1 | 19 |
| `T` MonthlyRate | 2 | 25, 105 |
| `X` PercentSalaryHike | 1 | 8 |
| `Y` PerformanceRating | 1 | 8 |

Kontrola: `=LICZ.PUSTE(A2:AI1471)` → 13. Wiersz **8** ma 7 pustych, w tym
`EmployeeNumber`.

### 2. Opcje, nie wykonanie

> Jak mogę obsłużyć te braki? Wypisz opcje, nic jeszcze nie zmieniaj.

Oczekiwane: (a) usunąć wiersze, (b) uzupełnić średnią/najczęstszą, (c)
oznaczyć do weryfikacji. **Nie wybierajcie jeszcze.**

### 3. Co dałoby usunięcie

7 z 1 470 = 0,5 % – statystycznie do przeżycia. Ale wiersz 8 to konkretny
pracownik; w budżecie wiersz to pozycja planu. Nie usuwa się ich dlatego,
że brakuje jednej kwoty.

### 4. Co dałoby uzupełnienie – bez zmiany danych

> Pokaż w tabeli, jaką wartość wstawiłbyś do każdej pustej komórki przy
> opcji „średnia / najczęstsza wartość" – ale jeszcze nic nie wpisuj.

Cztery pułapki do znalezienia:

| Komórka | Claude wstawiłby | Dlaczego źle |
|---|---|---|
| `K8` EmployeeNumber | ≈ 1 026 | wymyślony identyfikator, w dodatku **już istnieje** |
| `M8` Gender | Male | wymyślona cecha osoby |
| `Q8` JobRole | Sales Executive | wiersz 8 to R&D, tam tego stanowiska **nie ma** |
| `B8` MonthlyIncome | 6 505 | JobLevel 1, mediana grupy **2 670** – zawyżenie 2,4× |

`F9` Department → `Research & Development` – akurat prawda (JobRole =
`Laboratory Technician`, tylko R&D), ale trafił, nie wywnioskował:

> Dla F9 wywnioskuj dział ze stanowiska, nie z najczęstszej wartości.

### 5. Właściwa decyzja – selektywnie

> Nie uzupełniaj żadnych braków. Dodaj kolumnę `Uwagi` (AJ) i w siedmiu
> wierszach z brakami wpisz, których kolumn brakuje. Pokoloruj puste
> komórki na żółto (formatowanie warunkowe). W F9 wpisz `Research &
> Development` z komentarzem w komórce, że wywnioskowano ze stanowiska.

Kontrola: `=LICZ.PUSTE(A2:AI1471)` → **12**; 7 wpisów w `AJ`; 12 żółtych;
komentarz w `F9`.

### 6. Wariant „do analizy" – osobny arkusz

> Skopiuj dane do nowego arkusza `Analiza` i tam uzupełnij tylko kolumny
> liczbowe medianą w ramach tego samego JobLevel; pozostaw puste:
> EmployeeNumber, Gender, JobRole, EducationField, MaritalStatus. W
> arkuszu z danymi nic nie zmieniaj.

Klucz: `B8` → **2 670**, `B3` → **5 343**, `B949` → **9 980**.

## Pamiętaj

- Nawyk: *wypisz opcje* → *pokaż, co byś wstawił* → dopiero polecenie
  wykonawcze.
- **Nigdy nie uzupełniamy:** identyfikatorów, cech osób (płeć, stan
  cywilny), kwot w zestawieniach sprawozdawczych. Puste = „do wyjaśnienia
  u źródła".
- Jeśli już uzupełniacie – **w grupie** (poziom, dział, rozdział), w kopii
  oznaczonej jako szacunkowa.
- Puste ≠ zero ≠ „–" ≠ `n/d`. W realnych eksportach:
  > Które komórki w kolumnie B zawierają tekst zamiast liczby albo zero?
- Zużycie limitu: *Ustawienia → Zużycie*. Jedna rozmowa na plik; do
  prostych operacji Sonnet.
