# Zadanie 3: Bezpieczna analiza arkusza budżetowego z Claude

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok C, 60 min: Claude Czat w przeglądarce**).

**Cel:** przećwiczyć na fikcyjnym przykładzie – wzorowanym na Waszym
realnym procesie miesięcznego zestawienia budżetowego – jak Claude czyta
arkusz Excel, wykrywa błędy i pomaga przygotować podsumowanie, zanim w
Dniu 2 zrobimy to samo w Claude Code.
**Poziom:** podstawowy
**Czas:** ok. 20 minut

> **Zasada bezpieczeństwa (z Bloku B):** w tym i każdym kolejnym zadaniu
> pracujemy wyłącznie na danych fikcyjnych/zanonimizowanych, wzorowanych na
> Waszych procesach – nigdy na prawdziwych danych z ERP urzędu, bez
> pisemnej zgody Zamawiającego.

## Materiały

- Konto na [claude.ai](https://claude.ai).
- Plik `../materialy/zestawienie_miesieczne_PRZYKLAD.xlsx` – wzorowany na
  Procesie 1 (eksport z ERP → zestawienie miesięczne), z wymyślonymi
  kwotami i nazwami wydziałów. Plik celowo zawiera trzy typowe błędy z
  Bloku B: pusty wiersz (5), niespójny format daty w kolumnie Miesiąc
  (wiersze 4 i 8: „2026-09" i „09.2026" zamiast „wrzesień 2026") oraz
  scaloną komórkę w kolumnie Miesiąc (wiersze 9–10), przez co ostatni
  wiersz zostaje bez wartości w tej kolumnie.
- Plik `../materialy/zestawienie_miesieczne_PODSUMOWANIE.xlsx` – do Części
  2. Czyste, bez błędów, ale celowo **10 wydziałów** (więcej niż limit „max
  6 wierszy" z prompta w kroku 5) – 7 z nich przekracza plan, od +112 000 do
  +7 000 zł, więc Claude musi realnie wybrać i posortować, a nie tylko
  przepisać wszystko.

## Kroki

### Część 1: Claude jako pierwsza para oczu

1. Rozpocznij nową rozmowę i wgraj plik `zestawienie_miesieczne_PRZYKLAD.xlsx`.
2. Poproś o ogólny przegląd:
   *"Przeanalizuj ten arkusz i powiedz, co zawiera: jakie kolumny, ile
   wierszy, za jaki okres."*
3. Poproś o wskazanie problemów – konkretnie, tak jak w checkliście z
   Bloku B:
   *"Sprawdź ten arkusz pod kątem: scalonych komórek, niespójnych formatów
   dat i liczb, brakujących nagłówków, pustych wierszy. Wypisz, co
   znalazłeś, wskazując konkretną komórkę lub wiersz."*
4. Otwórz plik równolegle w Excelu i sprawdź, czy wskazane miejsca się
   zgadzają. Zwróć uwagę, czy Claude coś pominął albo błędnie zinterpretował.

### Część 2: Podsumowanie promptem P.K.Z.O.

5. Rozpocznij **nową rozmowę** i wgraj plik
   `zestawienie_miesieczne_PODSUMOWANIE.xlsx` (10 wydziałów, bez błędów z
   Części 1 – tu skupiamy się na samym prompcie i Artifact, nie na
   wyszukiwaniu usterek). Zbuduj prompt według formuły z
   [zadania 1](01-formula-pkzo.md), np.:

   > **P:** Jesteś analitykiem finansowym przygotowującym materiał dla
   > przełożonej.
   > **K:** Mam zestawienie miesięczne wydatków kilku (fikcyjnych)
   > wydziałów urzędu.
   > **Z:** Przygotuj krótkie podsumowanie: które działy przekroczyły plan
   > i o ile.
   > **O:** Format tabeli, maksymalnie 6 wierszy, kwoty w PLN, jedno zdanie
   > komentarza pod tabelą.

6. Sprawdź, czy tabela pojawiła się jako Artifact (osobny panel) – jeśli
   tak, poproś o jedną modyfikację, np. posortowanie według wielkości
   przekroczenia.

### Część 3: Test na "brudnych" danych

7. Celowo popsuj jedną komórkę w pliku (np. wpisz kwotę jako tekst zamiast
   liczby albo scal dwie komórki) i wgraj plik ponownie.
8. Poproś: *"Porównaj ten plik z poprzednią wersją – co się zmieniło i czy
   to wpływa na wynik podsumowania?"*
9. Zobacz, czy Claude samodzielnie zauważy problem, czy trzeba go było o to
   wprost zapytać – to ważna wskazówka na przyszłość: precyzyjne pytanie
   (Ograniczenia w P.K.Z.O.) działa lepiej niż liczenie na to, że AI samo
   wszystko wyłapie.

## Na co zwrócić uwagę

- **To dokładnie mechanika Procesu 1 i 2**, tylko na małą skalę i na
  fikcyjnych danych – w Dniu 2 przećwiczycie to samo na zanonimizowanym
  przykładzie bliższym Waszej codziennej pracy, a w Claude Code (nie w
  czacie) zbudujecie z tego powtarzalny "przepis".
- Claude dobrze wskazuje **kategorie** problemów (niespójne formaty,
  braki), ale zawsze zweryfikuj wskazaną komórkę w samym Excelu – to Wy
  odpowiadacie za liczby, nie AI.
- Im bardziej precyzyjnie opiszesz, czego szukasz (Ograniczenia w P.K.Z.O.),
  tym mniej rzeczy Claude pominie.
- Ten sam schemat – wgraj plik, poproś o analizę, poproś o podsumowanie w
  P.K.Z.O. – zadziała później na Waszym prawdziwym zestawieniu rocznym
  (Proces 2) i przy przygotowaniu materiału dla banku (Proces 3, Dzień 3).

## Notatki własne

- Ile z pięciu typowych błędów z Bloku B Claude znalazło samodzielnie, a
  ile trzeba było wskazać wprost?
- Czy podsumowanie w tabeli nadawało się do wysłania dalej bez poprawek?
