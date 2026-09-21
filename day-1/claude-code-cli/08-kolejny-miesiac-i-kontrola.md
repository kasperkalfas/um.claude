# Zadanie 8: Kolejny miesiąc od początku do końca + raport kontrolny

**Cel:** zamknąć październik z przepisów z zadań 6–7 (Proces 1 → Proces 2)
i dołożyć raport kontrolny miesiąc do miesiąca i do planu. Test, czy
przepisy naprawdę są powtarzalne.
**Poziom:** zaawansowany
**Czas:** ok. 30 minut
**Blok:** Dzień 1 — automatyzacja procesu (lub praca własna)

## Materiały

- `eksport_erp_2026-10.csv` – czysty eksport (bez pułapek).
- `zestawienie_miesieczne_SZABLON.xlsx` z wrześniem, `zestawienie_roczne_2026.xlsx`
  z wpisanym wrześniem (zad. 7).
- `przepis_proces1.md`, `proces2.py`.

## Kroki

1. ```powershell
   cd C:\Szkolenie\dzien-1\praca
   claude
   ```

### Część 1: Proces 1 dla października – z przepisu

2. ```
   Przeczytaj przepis_proces1.md i wykonaj go dla eksport_erp_2026-10.csv.
   Wynik wpisz do NOWEGO pliku zestawienie_miesieczne_2026-10.xlsx
   utworzonego z kopii szablonu (wyczyść w nim D i E, B2 = „październik").
   Września nie ruszaj.
   ```

   **Sprawdź z kluczem:** 600: 1 980 000 · 750: 1 510 000 · 801: 5 340 000
   · 851: 240 000 · 852: 1 690 000 · 900: 1 415 000 · 921: 585 000 ·
   926: 480 000 · **Razem 13 240 000**.

   Czy przepis przeszedł **bez dopytywania**? Każde pytanie Claude'a =
   luka w `przepis_proces1.md` – dopisz regułę.

3. ```
   Czy w eksporcie za październik były jakieś problemy z jakością?
   Jeśli nie – napisz to wprost.
   ```

   (Nie było – ale Claude ma sprawdzić, nie zakładać.)

### Część 2: Proces 2 dla października – ze skryptu

4. Skrypt czyta z `SZABLON.xlsx`, a październik jest w nowym pliku:

   ```
   Zmień proces2.py tak, żeby nazwę pliku miesięcznego przyjmował jako
   drugi parametr. Potem uruchom:
   proces2.py październik zestawienie_miesieczne_2026-10.xlsx
   ```

5. **Sprawdź w Excelu:** `Wykonanie!M14` = 13 240 000 zł, `Prognoza!B2`
   = 10, kontrola OK.

### Część 3: Raport kontrolny

6. ```
   Wygeneruj kontrola_2026-10.md z trzema sekcjami:
   1) Porównanie październik vs wrzesień wg działów: kwota, różnica,
      różnica w % – posortowane malejąco po |różnicy|;
   2) Wykonanie narastająco po 10 miesiącach vs plan: % planu i ile
      powinno być „teoretycznie" (10/12 = 83,3%); zaznacz działy powyżej
      i poniżej;
   3) Lista kontroli: suma miesięczna = kolumna roczna (OK/BŁĄD), liczba
      działów w obu plikach, brakujące wartości.
   Kwoty w PLN z separatorem tysięcy. Bez nazwisk. Jeśli czegoś nie
   wiesz – napisz „do potwierdzenia", nie zgaduj.
   ```

7. **Sprawdź** dwie liczby w Excelu. Dział 801 po październiku:
   50 674 000 = **81,7 %** planu (poniżej 83,3 %).

8. ```
   Dopisz do przepis_proces1.md sekcję „Po Procesie 2" z krokiem:
   wygeneruj raport kontrolny jak wyżej.
   ```

### Część 4: Test „nowej osoby"

9. ```
   /exit
   ```

   ```powershell
   claude
   ```

   Nowa sesja nie pamięta rozmowy.

10. ```
    Mam zamknąć listopad. Przeczytaj przepis_proces1.md i proces2.py
    i powiedz, jakich plików potrzebujesz ode mnie i co zrobisz krok
    po kroku. Nie wykonuj jeszcze.
    ```

    **Sprawdź:** plan kompletny i zrozumiały → przepis gotowy do użycia
    co miesiąc. Jeśli nie – widzisz dokładnie, czego brakuje.

## Na co zwrócić uwagę

- **Nowy plik miesięczny zamiast nadpisywania szablonu** – każdy miesiąc
  ma swój plik, szablon zostaje czysty.
- Raport liczy dwie rzeczy, których ręcznie nikt nie robi co miesiąc:
  zmianę m/m i tempo wykonania planu. Gotowy materiał na Dzień 3
  (DataPOV).
- **Test nowej osoby** to najlepszy sprawdzian przepisu: jeśli Claude
  w świeżej sesji wie, co robić, będzie wiedziała też koleżanka
  z wydziału.
- Claude nie pamięta sesji, ale pamięta **pliki**. Co ma przetrwać, musi
  być w pliku – o tym zadanie 10.

## Notatki własne

- Czy Proces 1 dla października przeszedł bez dopytywania?
- Które działy raport wskazał powyżej tempa planu?
- Czego zabrakło w przepisie w teście „nowej osoby"?
