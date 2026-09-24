# Zadanie 6: Filtrowanie słowami – jeden warunek, dwa warunki naraz

**Dzień 2, Blok B** · ok. 8 min · dodatek Claude w Excelu, kopia
`materialy/Human_Resources_zad6.xlsx` w **oryginalnej kolejności**
(zapisana z [`materialy/Human_Resources.xlsx`](materialy/Human_Resources.xlsx), nie z pliku po zadaniu 5);
Sonnet wystarczy.

**Cel:** filtr jednym zdaniem (jeden warunek, potem dwa) i policzenie
widocznych wierszy formułą. Filtr – w odróżnieniu od sortowania – niczego
nie zmienia.

**Ściągawka kolumn:** `C` Attrition · `F` Department (`Research &
Development`, `Sales`, `Human Resources`) · `K` EmployeeNumber ·
`AF` YearsAtCompany.

## Polecenia

### 1. Jeden warunek

> Przefiltruj dane tak, żeby zostały tylko osoby z działu R&D.

Skrót `R&D` → pełna nazwa w `F`. Lejki we **wszystkich** nagłówkach; pasek
stanu: *Znaleziono 960 z 1470*. Klucz: **960**.

### 2. Liczba widocznych – formułą

> Wpisz pod danymi formułę, która liczy tylko widoczne (przefiltrowane)
> wiersze.

Klucz: `=SUMY.CZĘŚCIOWE(103;A2:A1471)` → **960**. Zwykłe
`ILE.NIEPUSTYCH` da 1 470.
**Pułapka:** na kolumnie `K` wyjdzie **959** – `K8` jest puste. Liczcie na
kolumnie bez braków (`A`).

### 3. Dwa warunki naraz

> Przefiltruj dane tak, żeby zostały tylko osoby z działu R&D, które
> pracują w firmie co najmniej 30 lat.

Klucz: **10** wierszy (m.in. 128 / EmployeeNumber 165 / 40 lat; 192 / 259
/ 33). Formuła z kroku 2 → 10.

### 4. Kontrola niezależna od filtru

`=LICZ.WARUNKI(F2:F1471;"Research & Development";AF2:AF1471;">=30")` → **10**.

### 5. „Co najmniej" ≠ „ponad"

> …którzy pracują w firmie ponad 30 lat.

Klucz: **9** (wypada EmployeeNumber 1606 – dokładnie 30). Przy progach
piszcie granicę wprost.

### 6. Zdjęcie filtru

> Wyczyść wszystkie filtry.

1 470 wierszy wraca, wiersz 128 jest znowu wierszem 128. Sprawdźcie, czy
wiersz 9 (pusty `Department`) jest widoczny – po filtrze był ukryty.

## Pamiętaj

- Filtr = widok, sortowanie = zmiana.
- Dwa filtry = „i". „Lub" zwykły filtr nie umie – Claude zaproponuje
  kolumnę pomocniczą (`=LUB(...)`); klucz: R&D lub ≥ 30 lat = **967**.
- Ukryte wiersze wciąż są w pliku. Wycinek do wysłania:
  > Skopiuj widoczne wiersze do nowego arkusza Wynik.
- Po filtrze liczcie `SUMY.CZĘŚCIOWE` (103 = licz, 109 = suma) – nie
  `SUMA`/`ILE.NIEPUSTYCH`.
