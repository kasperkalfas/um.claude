# Zadanie 15: Podgląd wielu plików naraz

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok D, 60 min: Claude Code – pierwszy kontakt**).

**Cel:** poprosić o zestawienie informacji z kilku plików jednocześnie –
bez otwierania każdego z osobna w Excelu.
**Poziom:** podstawowy
**Czas:** ok. 7 minut

## Materiały

- Folder `test-claude-code` po zadaniach 13–14: 6 plików `.xlsx` (4 w
  `Wrzesien/`+`Pazdziernik/`, 2 w `archiwum/`), wszystkie o tej samej
  strukturze (Dział, Kwota planowana, Kwota wykonana, Miesiąc). Klucz
  odpowiedzi z tabelą per miesiąc: `../materialy/test-claude-code/README.md`.

## Kroki

1. Poproście o zbiorcze zestawienie: *„Przejrzyj wszystkie pliki .xlsx w
   tym folderze i powiedz mi, w którym miesiącu suma przekroczeń budżetu
   (wykonanie minus plan) była największa."*
2. Zwróćcie uwagę, że Claude Code samodzielnie **otwiera po kolei każdy
   plik**, liczy potrzebne wartości i dopiero na końcu podaje jedną,
   zbiorczą odpowiedź.
3. Poproście o rozwinięcie: *„Pokaż to w formie krótkiej tabeli: miesiąc,
   suma planu, suma wykonania, różnica."*
4. Zapytajcie, ile plików trzeba by otworzyć ręcznie w Excelu i ile
   czasu zajęłoby przepisanie tych samych liczb na kartkę – dla
   porównania z jednym poleceniem, które właśnie wykonaliście.

## Na co zwrócić uwagę

- To jest właśnie „automatyzacja" z drugiej strony: nie tylko
  przenoszenie/zmiana plików, ale też **czytanie i łączenie danych z
  wielu plików naraz**.
- Im więcej plików o podobnej strukturze, tym większa przewaga nad
  ręcznym przeglądaniem – to bezpośrednio zapowiada Proces 1 i 2 z
  Dnia 2.
- Zawsze warto poprosić o **rozbicie na pojedyncze liczby** (jak w kroku
  3), żeby móc zweryfikować, skąd wzięła się ostateczna odpowiedź.
