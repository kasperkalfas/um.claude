# Zadanie 3: Pytania do bazy – odpowiedzi ze źródłem, „nie ma w bazie" i dziennik decyzji

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
**Dzień 2, Blok D** lub praca własna; kontynuacja
[zadania 2](02-ze-starych-instrukcji-do-procedur.md)).

**Cel:** używać Claude Code jako **wyszukiwarki, która rozumie pytanie i
podaje, skąd wie** – sześć pytań, jakie zadaje nowa osoba w Wydziale, w
tym dwa z pułapką (sprzeczne źródła, brak informacji). Potem dopisać do
bazy to, czego w niej brakuje najczęściej: **decyzje** – z notatki ze
spotkania do dziennika decyzji, po jednej notatce na decyzję.
**Poziom:** podstawowy
**Czas:** ok. 15 minut
**Wymaga:** vault po zadaniu 2 (procedura + 8 działów + 2 pojęcia).

## Problem, który to rozwiązuje

Baza wiedzy jest tyle warta, ile odpowiedzi, które z niej wychodzą.
Odpowiedź bez wskazania notatki jest tyle samo warta, co odpowiedź z
pamięci – nie da się jej sprawdzić. A najczęstsza luka w każdej bazie
to nie procedury, tylko **decyzje**: „ustaliliśmy na spotkaniu", którego
nikt nie zapisał, więc za pół roku ustala się od nowa.

## Materiały

- Vault po zadaniu 2.
- `80-Zrodla/notatka_spotkanie_2026-09-10.txt`, szablon
  `90-Szablony/decyzja.md`.

## Kroki

1. **Zasada odpowiedzi.** Zacznijcie od: *„Od teraz na każde pytanie
   odpowiadaj tylko na podstawie notatek w tym vaultcie. Do każdego
   faktu podaj notatkę (ścieżkę). Jeśli czegoś nie ma w bazie – napisz
   »nie ma w bazie« zamiast domyślać się."* (To zdanie w zadaniu 4
   trafi do `CLAUDE.md`, żeby nie powtarzać go co sesję.)
2. **Sześć pytań nowej osoby** – zadawajcie po kolei, przy każdym
   sprawdźcie **ścieżkę** i **treść** w Obsidianie:

   | # | Pytanie | Klucz |
   |---|---|---|
   | 1 | *Do kiedy ma być gotowe zestawienie miesięczne?* | 7. dzień roboczy; źródło: `10-Procedury/Zamknięcie miesiąca` (a w nim mail 2026); **powinien wspomnieć**, że do 2025 był 10. dzień |
   | 2 | *Skąd biorę dane działu 851?* | mail z Wydziału Zdrowia, nie ERP; 4.–5. dzień roboczy; brak → poprzedni miesiąc na żółto; `20-Slownik/Dział 851…` |
   | 3 | *Jaki próg odchyleń wymaga wyjaśnienia?* | 5 %, dla 801 – 3 %; **pułapka**: czy Claude podał wyjątek dla oświaty bez dopytywania |
   | 4 | *Czy zestawienie miesięczne trzeba wydrukować?* | nie (od 2026); podpis = komentarz w pliku; **pułapka**: instrukcja 2019 mówi „tak" – Claude ma nazwać obie wersje, nie wybrać jednej |
   | 5 | *Jak przygotowuje się prezentację dla Rady z pliku rocznego?* | **„nie ma w bazie"** – Proces 3 nie jest opisany; jeśli Claude opisuje „typowe kroki" – to zmyślenie |
   | 6 | *Które działy są na drugiej stronie eksportu?* | 921 i 926; źródło: procedura (pułapki) i/lub notatki działów |

   Pytanie 5 jest najważniejsze: dobra baza wiedzy **wie, czego nie
   wie**. Jeśli Claude wygenerował procedurę Procesu 3 z ogólnej
   wiedzy – wróćcie do kroku 1 i powtórzcie zasadę, ostrzej.
3. **Pytanie, którego nie ma w żadnej notatce, ale jest w źródłach.**
   *„Czy wagi sezonowe do prognozy są już ustalone?"* Klucz: Claude
   powinien znaleźć to w `80-Zrodla/notatka_spotkanie…` (nie w
   notatkach) i **powiedzieć, że to źródło, nie notatka** – decyzja z
   10.09: do końca 2026 średnia × 12, od 2027 sezonowa, wagi do
   2026-11-30. Wniosek: notatka ze spotkania leży w źródłach, ale nikt
   jej nie „przepisał" do bazy. Naprawiacie to w kroku 4.
4. **Dziennik decyzji.** *„Z notatki ze spotkania 2026-09-10 utwórz w
   `30-Decyzje/` osobną notatkę dla każdej DECYZJI według szablonu
   decyzji (nazwa: `2026-09-10 – temat`). Punkty otwarte (bez decyzji)
   zbierz w jednej notatce `2026-09-10 – sprawy otwarte`. Zlinkuj z
   procedurą i działami, których dotyczą."* Klucz: **3 decyzje**
   (metoda prognozy do 2026 / od 2027; wyjaśnienie 851 do banku; lista
   danych poufnych do 2026-10-15) + **2 sprawy otwarte** (zastępstwo w
   listopadzie; arkusz Dochody). Decyzja o prognozie ma link do
   `[[Plik roczny]]` i `[[Dział 926 – Kultura fizyczna]]`,
   `[[Dział 600 – Transport i łączność]]`; decyzja o 851 – do
   `[[Dział 851 – Ochrona zdrowia]]`.
5. **Decyzja zmienia procedurę?** Zapytajcie: *„Czy któraś z decyzji z
   10.09 wymaga zmiany w procedurze zamknięcia miesiąca? Jeśli tak –
   pokaż zmianę, nie wprowadzaj."* Klucz: tak – wyjaśnienie 851 do
   banku „z materiałem wrześniowym" to zastosowanie progu z procedury
   (851 ma +1,5 %, czyli **poniżej** 5 % – a mimo to Skarbnik zdecydował
   o wyjaśnieniu). Dobra odpowiedź: procedura zostaje, ale w „Wyjątki"
   warto dopisać „Skarbnik może zażądać wyjaśnienia poniżej progu" z
   linkiem do decyzji. Zatwierdźcie tę jedną zmianę.
6. **Powtórka pytania 3 z zadania.** *„Czy wagi sezonowe do prognozy są
   już ustalone?"* – teraz odpowiedź ma przyjść z `30-Decyzje/…`, nie ze
   źródła. Różnica w praktyce: notatka ma frontmatter (`status:
   obowiazuje`, `data`), więc w zadaniu 4 da się zapytać „które decyzje
   z terminem minęły".

## Na co zwrócić uwagę

- **Ścieżka przy każdym fakcie to nie formalność.** To jedyny sposób, by
  odróżnić „baza tak mówi" od „Claude tak myśli". W czacie (Dzień 1)
  nie mieliście tej kontroli; tu ją macie – używajcie.
- **„Nie ma w bazie" jest odpowiedzią poprawną** i pożądaną. Model
  domyślnie woli odpowiedzieć niż odmówić; zasada z kroku 1 (i w
  zadaniu 4 – z `CLAUDE.md`) odwraca to domyślne zachowanie. Testujcie
  ją pytaniem 5 po każdej większej zmianie w vaultcie.
- **Sprzeczne źródła → dwie wersje w odpowiedzi** (pytania 1 i 4).
  Jeśli Claude podaje tylko nową – dobrze, ale nie wiecie, czy stara
  została uwzględniona, czy pominięta. Odpowiedź „obowiązuje X, do 2025
  było Y" jest lepsza, bo pokazuje, że model **widział** obie.
- **Decyzje to najbardziej niedoceniany typ notatki.** Procedury
  zmieniają się rzadko; decyzje – co spotkanie. Trzy notatki z jednego
  spotkania to 5 minut z Claude; bez nich za pół roku pytanie o wagi
  sezonowe wraca na stół.
- **Źródło ≠ notatka.** Plik w `80-Zrodla` jest surowy: Claude go
  przeczyta, ale nie ma frontmattera, linków ani statusu. „Przepisanie"
  do notatek (krok 4) to właśnie budowanie bazy; źródło zostaje jako
  dowód.
- **Wielkość vaulta a okno kontekstu** (Dzień 1). Kilkanaście notatek
  Claude czyta w całości; przy kilkuset – szuka i czyta wybrane, więc
  odpowiedź zależy od tego, czy notatki mają dobre tytuły i linki.
  Nazwy typu `Dział 851 – Ochrona zdrowia` zamiast `notatka3` to nie
  estetyka, to wyszukiwalność.

## Notatki własne

- Na które z sześciu pytań Claude odpowiedział bez ścieżki?
- Czy na pytanie 5 padło „nie ma w bazie"?
- Które trzy decyzje z ostatniego miesiąca w Waszym Wydziale nie są
  nigdzie zapisane?
