# Zadanie 4: Wykresy jednym zdaniem – histogram, słupki, punkty, koło (i kiedy którego nie robić)

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
**Dzień 2, Blok B: Praca na komórkach i strukturze danych w Excelu**;
kontynuacja [zadania 3](03-statystyki-i-szukanie-wierszy.md)).

**Cel:** poprosić Claude o cztery różne wykresy prosto w arkuszu –
histogram, wykres liczności, punktowy i kołowy – zobaczyć, że dodatek
najpierw buduje **tabelę pomocniczą**, a potem **natywny wykres Excela**
(edytowalny, zakotwiczony w komórce), i nauczyć się dwóch rzeczy:
sprawdzać tabelę pod wykresem oraz odmawiać wykresu kołowego, gdy nie
ma sensu.
**Poziom:** podstawowy
**Czas:** ok. 15 minut
**Wymaga:** dodatek Claude w Excelu, kopia `Human_Resources.xlsx`
(np. `Human_Resources_zad4.xlsx`), model Opus lub Sonnet.

## Problem, który to rozwiązuje

Wykres w Excelu to zwykle: zaznacz zakres → Wstawianie → wybierz typ →
popraw tytuł, osie, kolory → przesuń. Przy 1 470 wierszach najpierw
trzeba jeszcze policzyć liczności (tabela przestawna) albo przedziały
(histogram). Claude robi obie rzeczy z jednego zdania i zostawia
**zwykły wykres Excela** – taki, który możecie potem sami poprawić,
skopiować do PowerPointa (Dzień 3) albo usunąć.

## Materiały

- Kopia `Human_Resources.xlsx` z panelem Claude.
- Ściągawka kolumn: `A` = `Age`, `B` = `MonthlyIncome`, `C` = `Attrition`
  (odejścia), `D` = `BusinessTravel` (podróże służbowe).

## Kroki

1. **Histogram.** *„Narysuj histogram wieku pracowników (kolumna Age)."*
   Obserwujcie panel: Claude (a) ustala zakres wieku i przedziały,
   (b) buduje **tabelę liczności** (przedział → liczba osób) w wolnym
   miejscu arkusza, (c) tworzy wykres i podaje **adres zakotwiczenia**
   jako link. Kliknijcie link → wykres. Kliknijcie wykres → to natywny
   wykres Excela: ma uchwyty, karta *Projekt wykresu*, da się zmienić
   tytuł. Klucz (przedziały 5-letnie): 30–34 lata = 325 osób
   (najliczniejszy), 35–39 = 297, 25–29 = 229; skrajne: 18–19 = 17,
   60 lat = 5. Sprawdźcie **jedną liczbę z tabeli liczności** formułą,
   np. `=LICZ.WARUNKI(A2:A1471;">=30";A2:A1471;"<=34")` → 325.
2. **Poprawka bez klikania.** *„Zmień przedziały histogramu na 10-letnie."*
   Claude przebuduje tabelę i wykres. Zwróćcie uwagę: **nie musicie
   otwierać okna formatowania osi** – mówicie, co ma się zmienić.
3. **Liczności – kto został, kto odszedł.** *„Pokaż wykres słupkowy:
   ilu pracowników zostało, a ilu odeszło z firmy."*
   W poleceniu **nie ma** słowa `Attrition` – Claude ma sam skojarzyć
   kolumnę `C`. Klucz: zostało **1 233 (83,9 %)**, odeszło **237
   (16,1 %)** – te same liczby, które w zadaniu 2 sprawdzaliście
   formułą. Jeśli wykres pokazuje procenty, sprawdźcie, czy sumują się
   do 100.
4. **Zależność dwóch kolumn.** *„Wykres punktowy: wiek (Age) na osi X,
   wynagrodzenie miesięczne (MonthlyIncome) na osi Y."*
   Klucz: chmura punktów z **umiarkowaną dodatnią zależnością**
   (współczynnik korelacji ok. **0,50** – możecie go sprawdzić:
   `=WSP.KORELACJI(A2:A1471;B2:B1471)`). Dopytajcie: *„Czy dodać linię
   trendu i opisać, co pokazuje?"* – i przeczytajcie opis krytycznie:
   „starsi zarabiają więcej" to obserwacja, nie reguła płacowa.
5. **Koło – i dlaczego nie.** *„Wykres kołowy: podział pracowników wg
   częstotliwości podróży służbowych."* Klucz: rzadko 1 043 (71,0 %),
   często 277 (18,8 %), wcale 150 (10,2 %). Wykres wyjdzie poprawny –
   trzy kategorie, jedna dominująca, koło jest tu do przyjęcia. **Teraz
   test:** *„Zrób wykres kołowy podziału wg stanowiska (JobRole)."*
   9 kategorii, kilka po 5–7 % – koło jest nieczytelne. Sprawdźcie, czy
   Claude to zauważy i zaproponuje słupki; jeśli nie – poproście:
   *„Zamień na wykres słupkowy poziomy, posortowany malejąco."*
6. **Porządek.** Zapytajcie: *„Wypisz, gdzie w arkuszu są tabele
   pomocnicze i wykresy, które utworzyłeś."* – i zdecydujcie, czy mają
   zostać w arkuszu z danymi, czy przenieść je do nowego arkusza
   `Wykresy` (*„Przenieś wszystkie wykresy i ich tabele do nowego
   arkusza Wykresy."*).

## Na co zwrócić uwagę

- **Wykres stoi na tabeli – sprawdzajcie tabelę, nie obrazek.** Błąd w
  tabeli liczności (zły przedział, pominięty wiersz, nagłówek policzony
  jako dana) daje ładny, ale fałszywy wykres. Jedna formuła kontrolna na
  wykres – tak jak jedna liczba na wniosek w zadaniu 2.
- **Dobór typu wykresu to Wasza decyzja.** Histogram = rozkład jednej
  liczby; słupki = porównanie kategorii; punkty = zależność dwóch liczb;
  koło = udziały, **tylko gdy 2–4 kategorie i wyraźne różnice**.
  Claude zrobi, o co poprosicie – także zły wykres. Dzień 3 (DataPOV)
  rozwinie to w stronę „jaki wykres przekonuje odbiorcę".
- **Natywny wykres Excela = Wasz wykres.** Po utworzeniu jest Wasz:
  format, kolory, tytuł po polsku, wklejenie do prezentacji. Nie
  potrzebujecie Claude, żeby go poprawić – ale możecie go poprosić.
- **Claude „domyśla się" kolumn – i to jest ryzyko.** W kroku 3 nie
  podaliście nazwy kolumny; skojarzył `Attrition`. Przy Waszych
  zestawieniach z nagłówkami typu „Kw. plan." może skojarzyć źle.
  W zestawieniach roboczych **nazywajcie kolumny wprost**.
- **Kosztuje mniej niż analiza, ale nie zero.** Każdy wykres to
  ponowne przejrzenie kolumny i kilka operacji na arkuszu. Cztery
  wykresy w jednej rozmowie są tańsze niż cztery rozmowy – dane są już w
  oknie kontekstu (Dzień 1).
- **Dane fikcyjne, wykresy prawdziwe.** Wykres z realnych danych
  kadrowych to nadal dane osobowe w agregacji – zwykle bezpieczne do
  pokazania, ale **powstały przez wysłanie surowych wierszy do
  dostawcy**. Zasada z Bloku B dotyczy wejścia, nie wyjścia.

## Notatki własne

- Czy liczba z tabeli liczności (krok 1) zgadzała się z formułą?
- Czy przy 9 kategoriach Claude sam zaproponował słupki zamiast koła?
- Jakie trzy wykresy powtarzacie co miesiąc w swoich zestawieniach – i
  który z nich powinien być czymś innym niż jest?
