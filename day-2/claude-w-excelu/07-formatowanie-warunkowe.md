# Zadanie 7: Kolorowanie komórek słowami – tak/nie, skala kolorów, próg

**Dzień 2, Blok B** · ok. 10 min · dodatek Claude w Excelu, kopia
`materialy/Human_Resources_zad7.xlsx` (z
[`materialy/Human_Resources.xlsx`](materialy/Human_Resources.xlsx); może być zapisana z
pliku z zad. 6, filtry zdjęte); Sonnet wystarczy.

**Cel:** Claude ma założyć **regułę formatowania warunkowego**, nie
pomalować komórek na stałe. O znaczeniu koloru decydujecie Wy.

**Ściągawka kolumn:** `A` Age · `B` MonthlyIncome · `C` Attrition.

## Polecenia

### 1. Dwa kolory dla tak/nie

> W kolumnie Attrition pokoloruj komórki: Yes na zielono, No na czerwono.

Klucz: **237** zielonych, **1 233** czerwonych.
Kontrola: *Narzędzia główne → Formatowanie warunkowe → Zarządzaj regułami →
Ten arkusz* – dwie reguły na `$C$2:$C$1471`. Wpiszcie w `C2` `No` – kolor
zmienia się sam. `Ctrl+Z`.

### 2. Znaczenie koloru

`Yes` = pracownik **odszedł** – i dostał zielony. Claude wykonał
dosłownie.

> Zamień kolory: odejścia na czerwono, pozostali na zielono.

### 3. Skala kolorów dla liczby

> Pokoloruj kolumnę Age według wartości: najmłodsi na biało, najstarsi na
> czarno, pośrednie odcienie szarości.

Klucz: **jedna** reguła typu skala; biel = 18 lat, czerń = 60, 50 %
szarości = 39 (skala jest liniowa względem wartości, nie liczby osób).
Posortujcie rosnąco po wieku – szum zamienia się w gradient.

### 4. Czarny tekst na czarnym tle

> Zmień skalę na zielony–żółty–czerwony.

Sprawdźcie w *Zarządzaj regułami*: reguła **zmodyfikowana**, nie dopisana
obok (dwie skale nakładają się, pierwsza wygrywa).

### 5. Próg

> W kolumnie MonthlyIncome podświetl na pomarańczowo komórki powyżej
> 15 000.

Klucz: **133** (`=LICZ.JEŻELI(B2:B1471;">15000")`).

> A puste komórki w tej kolumnie – jak są potraktowane?

Trzy puste (`B3`, `B8`, `B949`) bez koloru. Osobna reguła:

> Puste komórki w B2:B1471 zaznacz na szaro.

### 6. Kolor po sortowaniu

> Posortuj malejąco według MonthlyIncome.

Pomarańczowe zbierają się u góry; kolory w `A` i `C` jadą **ze swoimi
wierszami** – reguła jest przypięta do zakresu i warunku, nie do komórki.

## Pamiętaj

- Jeśli *Zarządzaj regułami* jest puste – Claude pomalował na stałe:
  > Zamień na regułę formatowania warunkowego.
- Mówcie Claude, **co** ma być na czerwono; w budżecie przekroczenie planu
  po stronie dochodów jest dobre, po stronie wydatków złe.
- Czerwony–zielony: ok. 8 % mężczyzn nie rozróżnia. Do wysyłki:
  niebieski–pomarańczowy albo kolor + symbol.
- Skala rozciąga się od min do max – jedna wartość odstająca psuje całość.
  Do progów – reguła z kroku 5.
- Porządek w regułach:
  > Wypisz wszystkie reguły formatowania warunkowego w arkuszu.
