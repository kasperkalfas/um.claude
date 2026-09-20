# Zadanie 6: Proces 1 – z eksportu ERP do zestawienia miesięcznego

**Cel:** odwzorować Wasz Proces 1 na fikcyjnych danych: „brudny" eksport z
ERP (wiele wierszy, różne formaty, duplikat) → uporządkowane zestawienie
miesięczne wg działów (Plik 1). Claude Code czyści dane, agreguje i
wypełnia szablon – Ty sprawdzasz sumy.
**Poziom:** średni
**Czas:** ok. 30 minut
**Blok:** Dzień 1 — automatyzacja procesu

## Materiały

- `eksport_erp_2026-09.csv` – 25 wierszy, kolumny: data, dział, rozdział,
  paragraf, nazwa, kontrahent, kwota, nr dokumentu. Celowo: daty w dwóch
  formatach, kwoty w czterech (`1 240 000,00`, `310000.00`, `600 000,00 zł`,
  `980000`), jeden dokument **powtórzony dwa razy**, jeden wiersz **bez
  paragrafu**, spacje na końcu niektórych nazw.
- `zestawienie_miesieczne_SZABLON.xlsx` – docelowy Plik 1 (jeśli
  modyfikowałeś/aś go w zadaniu 5, skopiuj świeży z pendrive'a).
- Klucz odpowiedzi (sumy wg działów) – [README](README.md#klucz-odpowiedzi).

## Kroki

1. `cd C:\Szkolenie\dzien-1\praca`, `claude`, kopia szablonu do `kopie`.

### Część 1: Diagnoza eksportu

2. *„Przeanalizuj `eksport_erp_2026-09.csv`. Wypisz wszystkie problemy z
   jakością danych, które uniemożliwiają prostą sumę kolumny Kwota, z
   numerami wierszy. Nic nie zmieniaj."*
   Oczekiwane: 2 formaty dat, 4 formaty kwot, duplikat `FV/2026/09/0142`,
   brak paragrafu w `FV/2026/09/0210`, spacje w nazwach. Jeśli czegoś nie
   znalazł – dopytaj bez podpowiedzi („czy któryś dokument występuje
   więcej niż raz?").
3. *„Ile wynosi suma kwot: (a) jeśli po prostu zsumować wszystkie
   wiersze, (b) po usunięciu duplikatu? Pokaż obie liczby."*
   Różnica powinna wynosić dokładnie 1 240 000 zł.

### Część 2: Czyszczenie do osobnego pliku

4. *„Zapisz oczyszczoną wersję jako `eksport_erp_2026-09_czysty.csv`:
   daty RRRR-MM-DD, kwoty jako liczby z kropką dziesiętną, bez spacji na
   końcu nazw, bez duplikatu (zostaw pierwsze wystąpienie), a wiersz bez
   paragrafu zostaw, ale dodaj kolumnę `Uwagi` z tekstem »brak
   paragrafu«. Oryginału nie zmieniaj."*
5. Otwórz czysty plik w Excelu (Dane → Z tekstu/CSV, separator `;`) i
   przejrzyj. 24 wiersze? Kwoty jako liczby?

### Część 3: Agregacja i wypełnienie szablonu

6. *„Policz sumę kwot wg działu z czystego pliku i pokaż tabelę: dział,
   liczba dokumentów, suma."* Porównaj z kluczem odpowiedzi.
7. *„Wpisz te sumy do `zestawienie_miesieczne_SZABLON.xlsx`, kolumna D
   (Wykonanie w miesiącu), dopasowując po kodzie działu w kolumnie A, nie
   po kolejności. Wpisz B2 = »wrzesień«. Jeśli jakiś dział z eksportu nie
   występuje w szablonie albo odwrotnie – zatrzymaj się i powiedz."*
8. Otwórz szablon: D6:D13 wypełnione, D14 = 13 230 000 zł? Kolumna F
   pokazuje na razie 0,0% – bo liczy z E (narastająco), które uzupełnimy
   w zadaniu 7.

### Część 4: Zapisz przepis

9. *„Zapisz w pliku `przepis_proces1.md` po polsku, krok po kroku, co
   zrobiłeś od surowego eksportu do wypełnionego szablonu – tak, żeby w
   przyszłym miesiącu wystarczyło powiedzieć »zrób to samo dla
   października«."*
10. Przeczytaj `przepis_proces1.md`. Czy zawiera reguły (duplikaty po nr
    dokumentu, formaty kwot, dopasowanie po kodzie działu)? Popraw
    poleceniem, jeśli czegoś brakuje. Ten plik to zalążek zadania 10.

## Na co zwrócić uwagę

- **Duplikat to decyzja księgowa, nie techniczna.** Claude może
  zaproponować „usuń", ale to Wy wiecie, czy to podwójne zaksięgowanie,
  czy dwie prawdziwe faktury o tym samym numerze. Dlatego czysty plik
  powstaje **obok** oryginału, a nie zamiast.
- Suma kontrolna (krok 3) to Wasz najprostszy test poprawności: różnica
  (a)–(b) musi równać się kwocie duplikatu.
- Dopasowanie „po kodzie działu, nie po kolejności" chroni przed
  najczęstszym błędem ręcznego kopiowania – przesunięciem o wiersz.
- Przy prawdziwym eksporcie ERP kolumn i wierszy będzie więcej, ale
  kroki są identyczne. Najpierw diagnoza, potem czyszczenie obok, potem
  agregacja, na końcu wpis do szablonu.

## Notatki własne

- Czy sumy wg działów zgadzały się z kluczem? Jeśli nie – na którym
  etapie powstała różnica?
- Jakie reguły czyszczenia z Waszego prawdziwego eksportu ERP trzeba by
  dopisać do przepisu?
