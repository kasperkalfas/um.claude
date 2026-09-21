# Zadanie 6: Proces 1 – z eksportu ERP do zestawienia miesięcznego

**Cel:** „brudny" eksport z ERP → uporządkowane zestawienie miesięczne
wg działów (Plik 1). Claude Code czyści, agreguje i wypełnia szablon –
Ty sprawdzasz sumy i zapisujesz przepis.
**Poziom:** średni
**Czas:** ok. 30 minut
**Blok:** Dzień 1 — automatyzacja procesu

## Materiały

- `eksport_erp_2026-09.csv` – 25 wierszy; kolumny: data, dział, rozdział,
  paragraf, nazwa, kontrahent, kwota, nr dokumentu. **Pułapki:** daty
  w 2 formatach, kwoty w 4 formatach, duplikat `FV/2026/09/0142`, brak
  paragrafu w `FV/2026/09/0210`, spacje na końcu nazw.
- `zestawienie_miesieczne_SZABLON.xlsx` – docelowy Plik 1 (jeśli zmieniony
  w zad. 5, skopiuj świeży z pendrive'a).
- Klucz sum – [README](README.md#klucz-odpowiedzi).

## Kroki

1. ```powershell
   cd C:\Szkolenie\dzien-1\praca
   claude
   ```

   ```
   Skopiuj zestawienie_miesieczne_SZABLON.xlsx do kopie z datą i godziną.
   ```

### Część 1: Diagnoza eksportu

2. ```
   Przeanalizuj eksport_erp_2026-09.csv. Wypisz wszystkie problemy
   z jakością danych, które uniemożliwiają prostą sumę kolumny Kwota,
   z numerami wierszy. Nic nie zmieniaj.
   ```

   **Sprawdź:**

   - [ ] 2 formaty dat
   - [ ] 4 formaty kwot
   - [ ] duplikat `FV/2026/09/0142`
   - [ ] brak paragrafu w `FV/2026/09/0210`
   - [ ] spacje na końcu nazw

   Czego nie znalazł – dopytaj bez podpowiedzi:

   ```
   Czy któryś dokument występuje więcej niż raz?
   ```

3. ```
   Ile wynosi suma kwot: (a) jeśli po prostu zsumować wszystkie wiersze,
   (b) po usunięciu duplikatu? Pokaż obie liczby.
   ```

   **Sprawdź:** (a) 14 470 000, (b) 13 230 000, różnica **1 240 000 zł**
   = kwota duplikatu.

### Część 2: Czyszczenie do osobnego pliku

4. ```
   Zapisz oczyszczoną wersję jako eksport_erp_2026-09_czysty.csv: daty
   RRRR-MM-DD, kwoty jako liczby z kropką dziesiętną, bez spacji na końcu
   nazw, bez duplikatu (zostaw pierwsze wystąpienie), a wiersz bez
   paragrafu zostaw, ale dodaj kolumnę Uwagi z tekstem „brak paragrafu".
   Oryginału nie zmieniaj.
   ```

5. **Sprawdź w Excelu** (Dane → Z tekstu/CSV, separator `;`): 24 wiersze,
   kwoty jako liczby, oryginał nietknięty.

### Część 3: Agregacja i szablon

6. ```
   Policz sumę kwot wg działu z czystego pliku i pokaż tabelę: dział,
   liczba dokumentów, suma.
   ```

   **Sprawdź z kluczem:** 600: 2 150 000 · 750: 1 480 000 · 801: 5 210 000
   · 851: 265 000 · 852: 1 720 000 · 900: 1 340 000 · 921: 610 000 ·
   926: 455 000 · **Razem 13 230 000**.

7. ```
   Wpisz te sumy do zestawienie_miesieczne_SZABLON.xlsx, kolumna D
   (Wykonanie w miesiącu), dopasowując po kodzie działu w kolumnie A,
   nie po kolejności. Wpisz B2 = „wrzesień". Jeśli jakiś dział z eksportu
   nie występuje w szablonie albo odwrotnie – zatrzymaj się i powiedz.
   ```

8. **Sprawdź w Excelu:** D6:D13 wypełnione, **D14 = 13 230 000 zł**.
   Kolumna F pokazuje 0,0 % – liczy z E (narastająco), które uzupełnimy
   w zadaniu 7.

### Część 4: Zapisz przepis

9. ```
   Zapisz w pliku przepis_proces1.md po polsku, krok po kroku, co
   zrobiłeś od surowego eksportu do wypełnionego szablonu – tak, żeby
   w przyszłym miesiącu wystarczyło powiedzieć „zrób to samo dla
   października".
   ```

10. **Sprawdź** `przepis_proces1.md`: są reguły – duplikaty po nr
    dokumentu, formaty kwot i dat, dopasowanie po kodzie działu, czysty
    plik obok oryginału? Brakujące dopisz poleceniem. To zalążek
    zadania 10.

## Na co zwrócić uwagę

- **Duplikat to decyzja księgowa, nie techniczna.** Claude zaproponuje
  „usuń" – Wy wiecie, czy to podwójne zaksięgowanie, czy dwie faktury
  o tym samym numerze. Dlatego czysty plik powstaje **obok** oryginału.
- **Suma kontrolna (krok 3)** to najprostszy test: (a) − (b) = kwota
  duplikatu.
- „Po kodzie działu, nie po kolejności" chroni przed przesunięciem
  o wiersz – najczęstszym błędem ręcznego kopiowania.
- Prawdziwy eksport ma więcej kolumn i wierszy, ale kroki są te same:
  diagnoza → czyszczenie obok → agregacja → wpis do szablonu.

## Notatki własne

- Czy sumy zgadzały się z kluczem? Jeśli nie – na którym etapie powstała
  różnica?
- Jakie reguły czyszczenia z Waszego prawdziwego eksportu trzeba by dopisać
  do przepisu?
