# Zadanie 4: Wykresy jednym zdaniem – histogram, słupki, punkty, koło

**Dzień 2, Blok B** · ok. 15 min · dodatek Claude w Excelu, kopia
`Human_Resources.xlsx` (np. `_zad4`), Opus lub Sonnet.

**Cel:** cztery wykresy z jednego zdania każdy; Claude buduje **tabelę
pomocniczą**, potem **natywny wykres Excela**. Sprawdzamy tabelę, nie
obrazek – i odmawiamy koła, gdy nie ma sensu.

**Ściągawka kolumn:** `A` Age · `B` MonthlyIncome · `C` Attrition ·
`D` BusinessTravel · `Q` JobRole.

## Polecenia

### 1. Histogram

> Narysuj histogram wieku pracowników (kolumna Age).

Kliknijcie link → wykres (natywny: uchwyty, karta *Projekt wykresu*).
Klucz (przedziały 5-letnie): 30–34 = **325**, 35–39 = 297, 25–29 = 229,
18–19 = 17, 60 = 5.
Kontrola: `=LICZ.WARUNKI(A2:A1471;">=30";A2:A1471;"<=34")` → 325.

### 2. Poprawka bez klikania

> Zmień przedziały histogramu na 10-letnie.

### 3. Słupki – bez nazwy kolumny w poleceniu

> Pokaż wykres słupkowy: ilu pracowników zostało, a ilu odeszło z firmy.

Claude ma sam skojarzyć `Attrition`. Klucz: zostało **1 233 (83,9 %)**,
odeszło **237 (16,1 %)**.

### 4. Punkty – zależność dwóch kolumn

> Wykres punktowy: wiek (Age) na osi X, wynagrodzenie miesięczne
> (MonthlyIncome) na osi Y.

Klucz: umiarkowana dodatnia zależność, korelacja ok. **0,50**
(`=WSP.KORELACJI(A2:A1471;B2:B1471)`).

> Dodaj linię trendu i opisz, co pokazuje.

„Starsi zarabiają więcej" to obserwacja, nie reguła płacowa.

### 5. Koło – kiedy tak, kiedy nie

> Wykres kołowy: podział pracowników wg częstotliwości podróży służbowych.

Klucz: rzadko 1 043 (71,0 %), często 277 (18,8 %), wcale 150 (10,2 %) –
3 kategorie, koło OK.

> Zrób wykres kołowy podziału wg stanowiska (JobRole).

9 kategorii, kilka po 5–7 % – nieczytelne. Czy Claude sam zaproponuje
słupki? Jeśli nie:

> Zamień na wykres słupkowy poziomy, posortowany malejąco.

### 6. Porządek

> Wypisz, gdzie w arkuszu są tabele pomocnicze i wykresy, które utworzyłeś.

> Przenieś wszystkie wykresy i ich tabele do nowego arkusza Wykresy.

## Pamiętaj

- Wykres stoi na tabeli – **jedna formuła kontrolna na wykres**.
- Histogram = rozkład; słupki = porównanie kategorii; punkty = zależność;
  koło = udziały **tylko przy 2–4 kategoriach**. Claude zrobi też zły
  wykres, jeśli o niego poprosicie.
- W kroku 3 Claude „domyślił się" kolumny. W Waszych zestawieniach
  nazywajcie kolumny wprost.
