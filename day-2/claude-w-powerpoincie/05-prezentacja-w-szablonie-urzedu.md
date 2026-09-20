# Zadanie 5: Prezentacja w szablonie Urzędu – Claude ma się dopasować, nie narzucać

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
**Dzień 2**, ścieżka „Claude w PowerPoincie"; kontynuacja
[zadania 4](04-slajd-ze-zrodla-i-zmiana-tonu.md)).

**Cel:** wygenerować krótką prezentację (3 slajdy) **wewnątrz
istniejącego szablonu** – Waszego szablonu Urzędu albo dowolnego
szablonu PowerPointa – i sprawdzić, czy Claude naprawdę użył jego
układów, czcionek i kolorów, czy tylko położył własne pola tekstowe na
wierzchu. Różnica jest niewidoczna na pierwszy rzut oka i decyduje o
tym, czy prezentacja „przeżyje" zmianę szablonu.
**Poziom:** podstawowy
**Czas:** ok. 12 minut
**Wymaga:** dodatek Claude w PowerPoincie, szablon (patrz Materiały),
tryb zgód „pytaj". Trzy slajdy – celowo: to najtańszy sposób
sprawdzenia, jak Claude radzi sobie z szablonem, zanim zlecicie mu 20.

## Problem, który to rozwiązuje

Każda prezentacja Urzędu na zewnątrz idzie w szablonie: herb, kolory,
stopka, numeracja, określone układy. Prezentacje z zadań 2–4 miały
motyw „od Claude" – ładny, ale nie Wasz. W realnym Procesie 3 pytanie
brzmi: **czy AI potrafi pracować w naszym szablonie**, tak żeby
wystarczyło zmienić treść, a nie przeklejać ją slajd po slajdzie do
właściwego pliku.

## Materiały

- **Szablon** – jedna z opcji:
  - pusty szablon Urzędu (`.pptx` / `.potx` z herbem, kolorami i
    układami – to wygląd, nie dane, można go używać);
  - jeśli nie macie go pod ręką: *Plik → Nowy* → dowolny szablon
    PowerPointa z wyraźnym stylem (ciemne tło, nietypowa czcionka) –
    im bardziej charakterystyczny, tym łatwiej ocenić, czy Claude go
    uszanował.
- Treść: temat ogólny, jak w zadaniu 2 (*budżet obywatelski*), albo
  pięć punktów z Excela. Tu chodzi o formę, więc treść ma być prosta.

## Kroki

1. **Poznajcie szablon, zanim pozna go Claude.** Otwórzcie szablon i
   wejdźcie w *Widok → Wzorzec slajdów*. Policzcie układy (tytułowy,
   tytuł i zawartość, sam tytuł, dwie kolumny, sekcja…) i zwróćcie
   uwagę na stałe elementy: herb/logo, stopka, numer slajdu, kolory
   motywu, czcionki. Zamknijcie widok wzorca. Zapiszcie plik jako
   `szablon_test_zad5.pptx`.
2. **Polecenie.** W panelu: *„Stwórz krótką prezentację o budżecie
   obywatelskim – dokładnie 3 slajdy – **używając istniejącego
   szablonu i jego układów**. Nie zmieniaj motywu, kolorów ani
   czcionek."*
3. **Obserwujcie panel.** Claude powinien najpierw **przejrzeć
   szablon** („sprawdzam slajd 1 pod kątem stylu", tło, czcionki,
   dostępne układy), zaplanować: slajd 1 = układ tytułowy, slajdy 2–3 =
   tytuł i zawartość, i **poprosić o zgodę** na usunięcie pustych
   symboli zastępczych („Kliknij, aby dodać tytuł") – *pozwól raz*.
   Potem wstawia treść.
4. **Test 1 – czy to układy, czy pola na wierzchu.** Kliknijcie tytuł
   slajdu 2. Jeśli to **symbol zastępczy układu**, w *Narzędzia główne →
   Slajdy* przycisk **Resetuj** przywraca jego pozycję i format z
   wzorca, a obramowanie pola ma charakterystyczny, „układowy" styl.
   Jeśli Claude wstawił **własne pole tekstowe**, Resetuj nic nie
   zrobi – tekst leży na szablonie, ale nie jest jego częścią.
5. **Test 2 – zmiana motywu.** *Projektowanie → Warianty → Kolory* –
   wybierzcie inny zestaw kolorów. Jeśli slajdy Claude zmieniają kolory
   razem z resztą – używają motywu. Jeśli zostają w swoich kolorach –
   Claude „przyniósł" własne formatowanie. Cofnijcie (`Ctrl+Z`).
6. **Test 3 – stałe elementy.** Herb, stopka, numer slajdu – są na
   slajdach 2–3? Nie zasłonięte polem tekstowym? Nie przesunięte?
7. **Poprawka słowem, jeśli trzeba.** Jeśli któryś test nie przeszedł:
   *„Slajdy 2–3 przebuduj tak, żeby tytuł i treść były w symbolach
   zastępczych układu 'Tytuł i zawartość', bez dodatkowych pól
   tekstowych, z zachowaniem stopki i numeru slajdu."* Powtórzcie test
   1.
8. **Zapiszcie wynik w Notatkach:** który szablon, ile z trzech testów
   przeszło za pierwszym razem, ile po poprawce.

## Na co zwrócić uwagę

- **„W szablonie" znaczy „w układach", nie „na tle".** Prezentacja,
  która wygląda dobrze, ale składa się z pól tekstowych położonych na
  szablonie, rozsypie się przy pierwszej zmianie motywu, przy
  „Resetuj", przy kopiowaniu slajdu do innej prezentacji Urzędu.
  Trzy testy z kroków 4–6 zajmują minutę i mówią prawdę.
- **Nazywajcie ograniczenia wprost.** „Użyj szablonu" to za mało –
  „użyj układów szablonu, nie zmieniaj motywu, kolorów ani czcionek"
  daje Claude jasną granicę. Im bardziej charakterystyczny szablon,
  tym więcej pokus, żeby go „poprawić".
- **Trzy slajdy to test, nie oszczędność.** Generowanie w szablonie
  kosztuje tyle samo tokenów co bez niego; robimy 3 slajdy, żeby
  sprawdzić zachowanie, zanim zlecicie prezentację na 20 slajdów dla
  Rady. Jeśli 3 przechodzą testy – 20 też przejdzie.
- **Szablon = wygląd, treść = dane.** Pusty szablon Urzędu wolno
  otworzyć z dodatkiem. Ale w chwili, gdy wklejacie do polecenia realne
  kwoty, nazwiska, treść uchwały – to już dane Zamawiającego (Dzień 1,
  Blok B). Na szkoleniu: szablon prawdziwy, treść fikcyjna.
- **Docelowy przepływ Procesu 3** wygląda tak: dane (Excel, Dzień 2) →
  notatka/raport w Wordzie (własny albo z pomocą Claude) → **prezentacja
  z tego dokumentu, w szablonie Urzędu** (zadanie 8 z planu). To
  zadanie sprawdza ostatni krok; zadanie 8 – przedostatni.
- **Szablon też zajmuje okno kontekstu.** Rozbudowany wzorzec (wiele
  układów, grafiki) to więcej tokenów przy każdym pytaniu w tej
  rozmowie. Jeśli szablon Urzędu ma 30 układów, a używacie 3 – warto
  mieć „odchudzoną" wersję do pracy z AI.

## Notatki własne

- Który szablon testowaliście i ile testów (układy / motyw / stałe
  elementy) przeszło za pierwszym razem?
- Czy Wasz szablon Urzędu ma „odchudzoną" wersję z 3–5 układami? Kto
  mógłby ją przygotować?
- Która cykliczna prezentacja Wydziału byłaby pierwszą kandydatką do
  generowania w szablonie – i z jakiego dokumentu Word powstaje dziś?
