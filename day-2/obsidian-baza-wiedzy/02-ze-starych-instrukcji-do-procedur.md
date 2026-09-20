# Zadanie 2: Ze starej instrukcji, maila i CSV do procedur – notatki, które się linkują

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
**Dzień 2, Blok D** lub praca własna; kontynuacja
[zadania 1](01-obsidian-i-claude-code-w-jednym-folderze.md)).

**Cel:** zamienić trzy nieuporządkowane źródła (instrukcja z 2019 r.,
mail Skarbnika z 2026 r., słownik działów) w **procedurę zamknięcia
miesiąca** i **osiem notatek słownikowych** – z frontmatterem, listą
kontrolną kroków i linkami – tak, żeby Claude **nie wybrał po cichu**
między starą a nową wersją, tylko pokazał obie i oznaczył obowiązującą.
Potem obejrzeć wynik w grafie Obsidiana.
**Poziom:** podstawowy / średni
**Czas:** ok. 20 minut
**Wymaga:** vault z zadania 1 (Claude Code otwarty w folderze vaulta,
Obsidian obok).

## Problem, który to rozwiązuje

Instrukcja z 2019 r. mówi „do 10. dnia miesiąca, wydrukować, zanieść
do podpisu". Mail z 2026 r. mówi „do 7. dnia roboczego, nie drukujemy,
podpis to komentarz w pliku". Obie leżą na dysku wspólnym, obie mają
status „instrukcja". Nowa osoba trafi na tę pierwszą. Baza wiedzy ma
mieć **jedną obowiązującą procedurę** z jawnym śladem, co się zmieniło
i skąd to wiadomo – a nie trzecią wersję pisaną z pamięci.

## Materiały

- `80-Zrodla/instrukcja_zamkniecia_miesiaca_2019.txt`,
  `80-Zrodla/email_skarbnik_terminy_2026.txt`,
  `80-Zrodla/slownik_dzialow.csv`.
- Szablony `90-Szablony/procedura.md` i `pojecie.md`.
- Klucz różnic 2019 → 2026 (dla prowadzącego, do sprawdzenia kroku 2):

  | Element | 2019 | 2026 (obowiązuje) |
  |---|---|---|
  | Kiedy eksport z ERP | „po ostatnim księgowaniu" | 3. dzień roboczy |
  | Termin zestawienia miesięcznego | 10. dzień kalendarzowy | **7. dzień roboczy** |
  | Prognoza dla banku | brak | do 15. |
  | Dział 851 | z eksportu ERP | **mail z Wydziału Zdrowia**; brak → wartość z poprz. miesiąca na żółto |
  | Próg wyjaśnień odchyleń | brak | 5 %; **dla 801 – 3 %** |
  | Podpis | wydruk, parafa, Skarbnik | komentarz „OK – Skarbnik" w pliku |
  | Archiwum pliku rocznego | ręcznie, kopia z datą | historia wersji dysku; **nazwa pliku stała** |
  | Bez zmian | kolejność działów, Plan z uchwały (nie z eksportu), kontrola „Razem", 921/926 na 2. stronie eksportu, grudzień – niewygasające | |

## Kroki

1. **Najpierw porównanie, nie pisanie.** *„Porównaj instrukcję z 2019 r.
   z mailem Skarbnika z 2026 r. Wypisz w tabeli: co się zmieniło, co
   zostało bez zmian, co jest tylko w jednym źródle. Nic jeszcze nie
   twórz."* Sprawdźcie z kluczem: 7 zmian, 5 elementów bez zmian.
   Typowe braki: Claude pomija „Plan z uchwały, nie z eksportu" (bo to
   uwaga w nawiasie) albo nie zauważa, że prognoza dla banku w ogóle nie
   występuje w 2019 r.
2. **Procedura – jedna, obowiązująca, ze śladem.** *„Utwórz
   `10-Procedury/Zamknięcie miesiąca.md` według szablonu procedury:
   kroki jako lista kontrolna, wersja obowiązująca wg maila z 2026 r.;
   tam, gdzie 2019 mówiło inaczej, dopisz w sekcji »Wyjątki i pułapki«
   jedno zdanie »do 2025: …«. W `zrodla:` oba pliki. Linkuj działy,
   pliki i role."*
   Zatwierdźcie plan, obejrzyjcie notatkę w Obsidianie. Klucz:
   - kroki zaczynają się od eksportu **3. dnia roboczego**, kończą na
     prognozie dla banku do 15.;
   - dział 851 ma **osobny krok** (mail z Wydziału Zdrowia + co robić,
     gdy nie ma);
   - w „Kontrola": suma Razem vs eksport, próg 5 % / 3 % dla 801;
   - w „Wyjątki i pułapki": 921/926 na drugiej stronie, grudzień,
     „do 2025: termin 10. dnia, wydruk do podpisu";
   - **nie ma** kroku „wydrukuj i zanieś" jako obowiązującego.
   Jeśli Claude wpisał 10. dzień albo wydruk jako aktualne – zasada 4 z
   `CLAUDE.md` nie zadziałała; poproście o poprawkę **z podaniem, które
   źródło jest nowsze**.
3. **Słownik z CSV – osiem notatek jednym poleceniem.** *„Dla każdego
   wiersza `slownik_dzialow.csv` utwórz notatkę w `20-Slownik/` według
   szablonu pojęcia, nazwa `Dział KOD – Nazwa.md`. Notatka o 851 już
   jest – uzupełnij ją, nie nadpisuj. W »Powiązane« link do
   [[Zamknięcie miesiąca]] i do działów o podobnych uwagach (sezonowe,
   druga strona eksportu)."* Klucz: 8 notatek; 600 i 926 linkują się
   wzajemnie (sezonowość), 921 i 926 (druga strona eksportu), 801 ma
   uwagę o progu 3 %. Sprawdźcie w Obsidianie, czy notatka 851 z
   zadania 1 zachowała sekcję „Terminy".
4. **Graf.** W Obsidianie kliknijcie *Open graph view* (ikona po lewej).
   Powinniście zobaczyć: `Zamknięcie miesiąca` w środku, 8 działów wokół,
   kilka **szarych** węzłów – linki do notatek, których nie ma
   (`Eksport ERP`, `Plik roczny`, `Wydział Zdrowia`, `Skarbnik`…).
   Zapytajcie Claude: *„Wypisz wszystkie linki do nieistniejących
   notatek w vaultcie, posortowane wg liczby wystąpień."* – to Wasza
   kolejka na zadanie 3.
5. **Dwie brakujące notatki – na próbę.** Wybierzcie dwie najczęstsze z
   listy (zwykle `Plik roczny` i `Eksport ERP`) i poproście o notatki
   pojęciowe **wyłącznie na podstawie źródeł**. Klucz: w `Plik roczny`
   ma być „nazwa stała cały rok – bank ma link", „historia wersji na
   dysku", „arkusz Wykonanie, kolumna miesiąca", „w grudniu kolumna
   niewygasające"; jeśli Claude dopisał np. „plik zawiera 12 arkuszy" –
   tego nie ma w żadnym źródle → „(do potwierdzenia)" albo usunąć.

## Na co zwrócić uwagę

- **Porównanie przed pisaniem** (krok 1) to najważniejszy nawyk tej
  ścieżki. Gdy Claude dostaje sprzeczne źródła i polecenie „napisz
  procedurę", zwykle pisze gładką syntezę – a gładka synteza dwóch
  sprzecznych instrukcji to trzecia, nieprawdziwa. Tabela różnic
  zajmuje minutę i pokazuje, gdzie trzeba **decyzji**, nie tekstu.
- **Ślad zmiany zostaje w notatce.** „Do 2025: 10. dzień" w sekcji
  wyjątków to nie bałagan – to odpowiedź na pytanie audytora „od kiedy
  obowiązuje 7. dzień roboczy i skąd to wiadomo". `zrodla:` z dwoma
  plikami to to samo w metadanych.
- **Jedna notatka = jedno pojęcie** – dlatego 8 notatek działów zamiast
  jednej tabeli. Tabela jest wygodna do czytania; osobne notatki są
  wygodne do **linkowania** (procedura → dział 851 → Wydział Zdrowia) i
  do pytań w zadaniu 3. Tabelę zawsze można wygenerować z notatek;
  odwrotnie – nie.
- **Szare węzły to plan, nie wstyd.** Baza wiedzy nigdy nie jest
  „skończona". Lista nieistniejących linków posortowana po
  wystąpieniach to najlepsza możliwa lista priorytetów – bo pokazuje,
  o czym procedury mówią najczęściej, a co nie ma jeszcze opisu.
- **Claude dopisuje fakty spoza źródeł** – zwłaszcza „oczywiste"
  („plik ma 12 arkuszy", „eksport w formacie xlsx"). W bazie wiedzy
  Wydziału każde takie zdanie to potencjalna instrukcja dla nowej
  osoby. Zasada 3 z `CLAUDE.md` + kontrola w kroku 5 = nawyk.
- **Te same dane, trzeci raz.** Osiem działów z `slownik_dzialow.csv`
  to te same działy, co w zestawieniach Dnia 1 i w prezentacji
  budżetowej (`../claude-w-powerpoincie/`). W realnym Wydziale baza
  wiedzy jest miejscem, gdzie **opis** tych działów (skąd dane, jakie
  progi) żyje niezależnie od plików z liczbami.

## Notatki własne

- Ile z 7 zmian Claude wychwycił w kroku 1 bez podpowiedzi?
- Czy w procedurze został jakiś krok z 2019 r. jako obowiązujący?
- Które trzy pojęcia z Waszej realnej pracy nie mają dziś **żadnej**
  spisanej definicji – a wszyscy „wiedzą, o co chodzi"?
