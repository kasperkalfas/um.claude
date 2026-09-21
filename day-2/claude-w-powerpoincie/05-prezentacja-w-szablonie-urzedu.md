# Zadanie 5: Prezentacja w szablonie Urzędu – Claude ma się dopasować, nie narzucać

**Dzień 2** · ok. 12 min · dodatek Claude w PowerPoincie, tryb „pytaj".

**Cel:** 3 slajdy **wewnątrz istniejącego szablonu** i trzy testy, czy
Claude użył jego układów, czy tylko położył własne pola tekstowe na
wierzchu.

**Szablon:** pusty szablon Urzędu (`.pptx` / `.potx` – wygląd, nie dane)
albo *Plik → Nowy* → dowolny szablon z wyraźnym stylem (im bardziej
charakterystyczny, tym łatwiej ocenić). Treść: temat z zadania 2.

## Polecenia

### 0. Poznajcie szablon

*Widok → Wzorzec slajdów*: policzcie układy, zwróćcie uwagę na herb,
stopkę, numer slajdu, kolory, czcionki. Zapiszcie jako
`szablon_test_zad5.pptx`.

### 1. Polecenie

> Stwórz krótką prezentację o budżecie obywatelskim – dokładnie 3 slajdy –
> używając istniejącego szablonu i jego układów. Nie zmieniaj motywu,
> kolorów ani czcionek.

Claude przegląda szablon, planuje (1 = tytułowy, 2–3 = tytuł i zawartość),
prosi o zgodę na usunięcie pustych symboli zastępczych → *pozwól raz*.

### 2. Test 1 – układy czy pola na wierzchu

Kliknijcie tytuł slajdu 2 → *Narzędzia główne → Slajdy → Resetuj*. Symbol
zastępczy układu wraca na pozycję z wzorca; własne pole tekstowe – nic.

### 3. Test 2 – zmiana motywu

*Projektowanie → Warianty → Kolory* → inny zestaw. Slajdy Claude zmieniają
kolory razem z resztą? `Ctrl+Z`.

### 4. Test 3 – stałe elementy

Herb, stopka, numer slajdu na 2–3: są, nie zasłonięte, nie przesunięte?

### 5. Poprawka słowem

> Slajdy 2–3 przebuduj tak, żeby tytuł i treść były w symbolach
> zastępczych układu „Tytuł i zawartość", bez dodatkowych pól tekstowych,
> z zachowaniem stopki i numeru slajdu.

Powtórzcie test 1.

## Pamiętaj

- „W szablonie" = „w układach", nie „na tle". Pola na wierzchu rozsypią
  się przy zmianie motywu i kopiowaniu slajdu.
- „Użyj szablonu" to za mało – nazywajcie ograniczenia: układy, motyw,
  kolory, czcionki.
- 3 slajdy to test przed zleceniem 20 dla Rady.
- Szablon też zajmuje okno kontekstu – warto mieć „odchudzoną" wersję
  (3–5 układów) do pracy z AI.
- Docelowy Proces 3: dane (Excel) → notatka w Wordzie → **prezentacja z
  dokumentu, w szablonie** (zad. 8 z planu).
