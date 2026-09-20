# Zadanie 7: Kolorowanie komórek słowami – tak/nie na zielono i czerwono, skala kolorów dla liczb

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
**Dzień 2, Blok B: Praca na komórkach i strukturze danych w Excelu**;
kontynuacja [zadania 6](06-filtrowanie.md)).

**Cel:** pokolorować komórki według warunku dwoma poleceniami po polsku
– najpierw kolumnę tekstową (tak → jeden kolor, nie → drugi), potem
kolumnę liczbową ciągłą skalą (od najmniejszej do największej wartości)
– i zobaczyć, że Claude zakłada **regułę formatowania warunkowego**
Excela, a nie maluje komórek na stałe. Po drodze: sprawdzenie reguły w
*Zarządzaj regułami*, dobór kolorów, który nie wprowadza w błąd, i próg
z Waszych zestawień.
**Poziom:** podstawowy
**Czas:** ok. 10 minut
**Wymaga:** dodatek Claude w Excelu, kopia `Human_Resources.xlsx` (np.
`Human_Resources_zad7.xlsx`; może być plik z zadania 6 – filtry
zdjęte); Sonnet wystarczy.

## Problem, który to rozwiązuje

W zestawieniu, które ogląda przełożony, kolor działa szybciej niż
liczba: „co przekroczyło plan", „gdzie brakuje danych", „które pozycje
są największe". W Excelu to *Narzędzia główne → Formatowanie
warunkowe*, wybór typu reguły, wpisanie warunku, wybór formatu – dla
każdej reguły osobno, a przy skali kolorów jeszcze trzy pola z
progami. Claude robi to z jednego zdania; Wy odpowiadacie za to, **co
kolor ma znaczyć**.

## Materiały

- Kopia `Human_Resources.xlsx` z panelem Claude.
- Ściągawka kolumn: `A` = `Age` (wiek), `B` = `MonthlyIncome`
  (wynagrodzenie miesięczne), `C` = `Attrition` (czy pracownik odszedł:
  `Yes`/`No`). Dane w wierszach 2–1471.

## Kroki

1. **Dwa kolory dla tak/nie.** *„W kolumnie Attrition pokoloruj
   komórki: Yes na zielono, No na czerwono."*
   Claude powinien założyć **dwie reguły formatowania warunkowego** na
   `C2:C1471` (nie wypełniać komórek ręcznie) i napisać, co zrobił.
   Klucz: **237** zielonych, **1 233** czerwonych. Sprawdzian, że to
   reguła, a nie farba: *Narzędzia główne → Formatowanie warunkowe →
   Zarządzaj regułami → Ten arkusz* – mają być dwie pozycje z warunkiem
   typu „Wartość komórki równa Yes" i zakresem `$C$2:$C$1471`. Drugi
   sprawdzian: wpiszcie w `C2` `No` zamiast `Yes` – kolor ma się
   zmienić sam. Cofnijcie (`Ctrl+Z`).
2. **Zatrzymajcie się przy znaczeniu.** `Attrition = Yes` to pracownik,
   który **odszedł** – a dostał zielony. Polecenie było wykonane
   dosłownie; Claude nie zapytał, czy zielony ma oznaczać „dobrze".
   Poproście: *„Zamień kolory: odejścia na czerwono, pozostali na
   zielono."* – i zapamiętajcie, że o znaczeniu koloru decydujecie Wy,
   nie narzędzie.
3. **Skala kolorów dla liczby.** *„Pokoloruj kolumnę Age według
   wartości: najmłodsi na biało, najstarsi na czarno, pośrednie odcienie
   szarości."*
   Claude powinien założyć **jedną** regułę typu *skala kolorów* (2
   kolory: minimum → biały, maksimum → czarny) na `A2:A1471`. Klucz:
   biel = **18 lat** (8 osób), czerń = **60 lat** (5 osób), 50 %
   szarości = **39 lat** (środek między 18 a 60 – skala dwukolorowa jest
   liniowa względem **wartości**, nie względem liczby osób; mediana wieku
   to 36). W oryginalnej kolejności wierszy kolumna
   wygląda jak szum – przewińcie kilka ekranów, żeby zobaczyć
   pojedyncze ciemne komórki (50+). Dopiero posortowanie rosnąco po
   wieku (zadanie 5) zamienia szum w gradient od bieli do czerni – to
   test, że skala jest ciągła, a nie „dwa kolory z progiem".
4. **Czarny tekst na czarnym tle.** W komórkach z 55+ liczba jest
   nieczytelna. Poproście: *„Zmień skalę na biały → ciemnoniebieski i
   ustaw biały tekst dla najciemniejszych komórek"* albo prościej:
   *„Zmień skalę na zielony–żółty–czerwony."* Zobaczcie w *Zarządzaj
   regułami*, że reguła została **zmodyfikowana**, a nie dopisana obok
   (dwie skale na tej samej kolumnie nakładają się i pierwsza wygrywa).
5. **Próg, jak w Waszych zestawieniach.** *„W kolumnie MonthlyIncome
   podświetl na pomarańczowo komórki powyżej 15 000."* Klucz: **133**
   komórek. Sprawdźcie formułą: `=LICZ.JEŻELI(B2:B1471;">15000")` →
   133. Dopytajcie: *„A puste komórki w tej kolumnie – jak są
   potraktowane?"* – trzy puste (`B3`, `B8`, `B949`) nie dostają koloru,
   bo pusta komórka nie jest „powyżej 15 000". W zestawieniu, w którym
   brak danych jest problemem, poproście o **osobną regułę**: *„Puste
   komórki w B2:B1471 zaznacz na szaro."*
6. **Kolor po sortowaniu i filtrze.** Posortujcie malejąco po
   wynagrodzeniu (*„Posortuj malejąco według MonthlyIncome"*) –
   pomarańczowe komórki mają zebrać się u góry, kolory w `A` i `C` mają
   wędrować **razem ze swoimi wierszami**. Reguła jest przypięta do
   zakresu i warunku, nie do konkretnych komórek – dlatego przeżywa
   sortowanie i filtr, w odróżnieniu od ręcznie pomalowanej komórki.

## Na co zwrócić uwagę

- **Reguła, nie farba.** Ręczne wypełnienie zostaje na komórce także po
  zmianie wartości i po sortowaniu jedzie w złe miejsce. Jeśli Claude
  pomalował komórki na stałe (w *Zarządzaj regułami* pusto), poproście:
  *„Zamień na regułę formatowania warunkowego."* Ta sama zasada, co
  „formuła, nie wartość" z zadania 3.
- **Kolor ma znaczenie, którego narzędzie nie zna.** Zielony = dobrze,
  czerwony = źle – to konwencja, a nie własność danych (krok 2).
  W zestawieniu budżetowym „przekroczenie planu" po stronie dochodów
  jest dobre, po stronie wydatków złe. Mówcie Claude, **co** ma być na
  czerwono, zamiast liczyć, że się domyśli.
- **Czerwony–zielony to najgorsza para dla ok. 8 % mężczyzn** (daltonizm
  czerwono-zielony). Dla zestawień wysyłanych dalej: niebieski–
  pomarańczowy albo kolor + symbol (zestaw ikon, pogrubienie). Dzień 3
  (DataPOV) wróci do tego przy slajdach.
- **Skala kolorów rozciąga się od minimum do maksimum – jedna wartość
  odstająca psuje całość.** Ta sama reguła na kolumnie z 141 zamiast 41
  w `A2` (test z zadania 3) rozciągnie skalę do 141 i zrobi z całej
  reszty niemal jednolitą biel. Skala
  nadaje się do „gdzie są największe/najmniejsze", nie do „co
  przekroczyło próg" – do progu jest reguła z kroku 5.
- **Reguł przybywa niezauważalnie.** Każde „zmień kolor" może dodać
  nową regułę zamiast poprawić starą. Raz na jakiś czas: *Zarządzaj
  regułami → Ten arkusz* i porządek – albo *„Wypisz wszystkie reguły
  formatowania warunkowego w arkuszu."*
- **Puste komórki nie łapią się na warunek liczbowy** (krok 5). W
  zestawieniu z ERP brak wartości bywa ważniejszy niż wartość poza
  progiem – osobna reguła na puste to nawyk, nie dodatek.
- **Dane fikcyjne, reguły prawdziwe.** Reguły formatowania możecie
  skopiować do własnego pliku (*Malarz formatów* albo *Zarządzaj
  regułami → zakres*) bez otwierania go z dodatkiem – to jeden ze
  sposobów przeniesienia efektu pracy z Claude na realne dane bez
  wysyłania ich do dostawcy.

## Notatki własne

- Ile reguł było w *Zarządzaj regułami* po kroku 4 – jedna czy dwie
  skale na `A`?
- Czy Claude sam zwrócił uwagę, że „Yes na zielono" oznacza odejścia
  na zielono?
- Która kolumna w Waszym zestawieniu miesięcznym zasługuje na próg z
  kolorem – i jaki to próg?
