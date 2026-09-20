# Zadanie 4: „Proszę" i „dziękuję" też kosztują – jak pisać oszczędnie

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
wstęp do **Bloku D: Claude Code – pierwszy kontakt**).

**Cel:** zobaczyć na liczniku, że każde dodatkowe słowo w poleceniu to
tokeny – i nauczyć się odróżniać słowa, które coś wnoszą, od słów, które
tylko zajmują okno.
**Poziom:** podstawowy
**Czas:** ok. 6 minut

## Problem, który to rozwiązuje

Piszemy do Claude tak, jak piszemy pisma: „Dzień dobry, uprzejmie proszę
o…", „Z góry dziękuję". To naturalne i w pojedynczej rozmowie nie ma
znaczenia. Ale zasada jest ogólna: **model rozlicza tokeny na wejściu i
na wyjściu**, a w Claude Code i Cowork to samo polecenie potrafi być
wykonywane wielokrotnie, do tego z doklejonym `CLAUDE.md`, opisami skilli
i konektorów. Wtedy każde zbędne słowo mnoży się przez liczbę uruchomień.
Publicznie przyznał to nawet szef OpenAI: same „proszę" i „dziękuję" w
ChatGPT kosztują firmę miliony dolarów w mocy obliczeniowej.

## Materiały

- Tokenizer pokazowy OpenAI: https://platform.openai.com/tokenizer (ten
  sam co w zadaniach 1–2).
- Polecenia z sekcji „Kroki" (tekst fikcyjny).

## Kroki

1. Wklejcie do tokenizera krótkie, rzeczowe polecenie:
   `Podaj sumę wydatków działu 750 za sierpień 2026.`
   Zapiszcie liczbę tokenów. Zauważcie, że **kropka na końcu to osobny
   token**, a kod działu i rok rozpadają się na kilka kawałków.
2. Teraz wersja „pismo urzędowe":
   `Dzień dobry, czy mógłby Pan uprzejmie podać mi sumę wydatków działu 750 za sierpień 2026? Z góry bardzo dziękuję!`
   Porównajcie licznik. Grzeczność dołożyła kilkanaście tokenów, a treść
   polecenia jest identyczna. Kliknijcie **Token IDs** – dla modelu to po
   prostu więcej liczb do przetworzenia.
3. Trzecia wersja – dłuższa, ale **z treścią**, zgodnie z formułą P.K.Z.O.
   z [zadania 1 z Bloku C](../claude-zadania/01-formula-pkzo.md):
   `Jesteś analitykiem budżetowym. Z arkusza "sierpien_2026" podaj sumę wydatków działu 750. Kwotę zapisz w PLN z separatorem tysięcy, bez komentarza.`
   Ta wersja ma najwięcej tokenów – i to jest w porządku. Każde zdanie
   zmienia wynik (kto odpowiada, skąd bierze dane, jak formatuje).
4. Rozmowa z prowadzącym (2 min): które tokeny z kroku 2 wnosiły coś do
   odpowiedzi, a które z kroku 3? Wniosek zapiszcie w „Notatkach".

## Na co zwrócić uwagę

- **Płacicie za wejście i wyjście.** Długie pytanie to tokeny, długa
  odpowiedź też. „Odpowiedz jednym zdaniem" albo „bez komentarza" to nie
  tylko wygoda – to mniej tokenów na wyjściu.
- **Grzeczność nie szkodzi w czacie, szkodzi w automatyzacji.** W
  pojedynczej rozmowie „proszę" to tyle co nic. Ale w `CLAUDE.md`, w
  komendzie `/zamknij-miesiac` czy w skillu każde zbędne słowo jest
  wczytywane przy **każdym** uruchomieniu – tam piszemy telegraficznie.
- **Oszczędzać tokeny ≠ pisać krótko.** Krok 3 jest najdłuższy i
  najlepszy. Tniemy uprzejmości, powtórzenia i wklejanie całych plików,
  a nie personę, kontekst, ograniczenia i przykłady (P.K.Z.O.).
- **Agent dźwiga więcej niż Wasze pytanie.** Claude Code przy każdym
  poleceniu ma w oknie także opis projektu, narzędzia, skille i
  konektory (zadanie 2). Wasze polecenie to zwykle najmniejsza część –
  tym bardziej warto, żeby była konkretna, a nie ozdobna.

## Notatki własne

- Ile tokenów miały wersje z kroków 1, 2 i 3? Które słowa z wersji 2
  wyrzucilibyście, a które z wersji 3 zostawilibyście na pewno?
- Jakie zwroty „z pisma" najczęściej wpisujecie do Claude z przyzwyczajenia?
