# Zadanie 4: „Proszę" i „dziękuję" też kosztują – jak pisać oszczędnie

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
wstęp do **Bloku D: Claude Code – pierwszy kontakt**).

**Cel:** porównać na liczniku trzy wersje tego samego polecenia
i odróżnić słowa, które coś wnoszą, od słów, które tylko zajmują okno.
**Poziom:** podstawowy
**Czas:** ok. 6 minut

## W dwóch zdaniach

Piszemy do Claude jak pisma: „uprzejmie proszę", „z góry dziękuję".
W pojedynczej rozmowie to nic – ale w `CLAUDE.md`, komendzie
`/zamknij-miesiac` czy skillu każde zbędne słowo jest wczytywane przy
**każdym** uruchomieniu i mnoży się przez liczbę uruchomień.

## Materiały

- https://platform.openai.com/tokenizer

## Kroki

1. **Wersja rzeczowa:**

   ```
   Podaj sumę wydatków działu 750 za sierpień 2026.
   ```

   Zapiszcie liczbę tokenów. Kropka to osobny token, „750" i „2026"
   rozpadają się na kawałki.

2. **Wersja „pismo urzędowe":**

   ```
   Dzień dobry, czy mógłby Pan uprzejmie podać mi sumę wydatków działu 750 za sierpień 2026? Z góry bardzo dziękuję!
   ```

   **Sprawdź:** kilkanaście tokenów więcej, treść polecenia identyczna.

3. **Wersja P.K.Z.O.** ([zadanie 1 z Bloku C](../claude-zadania/01-formula-pkzo.md)):

   ```
   Jesteś analitykiem budżetowym. Z arkusza "sierpien_2026" podaj sumę wydatków działu 750. Kwotę zapisz w PLN z separatorem tysięcy, bez komentarza.
   ```

   **Sprawdź:** najwięcej tokenów – i to jest w porządku. Każde zdanie
   zmienia wynik: kto odpowiada, skąd bierze dane, jak formatuje.

4. **Rozmowa (2 min):** które tokeny z wersji 2 wnosiły coś do
   odpowiedzi? Które z wersji 3? Wniosek do „Notatek".

## Na co zwrócić uwagę

- **Płacicie za wejście i wyjście.** „Bez komentarza", „jednym zdaniem"
  to mniej tokenów na wyjściu.
- **Oszczędzać ≠ pisać krótko.** Tniemy uprzejmości, powtórzenia
  i wklejanie całych plików – nie personę, kontekst, ograniczenia.
- **Wasze polecenie to najmniejsza część okna.** Claude Code ma w nim
  także `CLAUDE.md`, narzędzia, skille – tym bardziej niech polecenie
  będzie konkretne, nie ozdobne.

## Notatki własne

- Ile tokenów miały wersje 1, 2, 3?
- Jakie zwroty „z pisma" wpisujecie do Claude z przyzwyczajenia?
