# Zadanie 1: Czym są tokeny – demo na tokenizerze

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
wstęp do **Bloku D: Claude Code – pierwszy kontakt**).

**Cel:** zobaczyć na własne oczy, że model nie czyta słów ani liter, tylko
„tokeny" – i wyczuć, ile tokenów zajmuje typowy tekst urzędowy.
**Poziom:** podstawowy
**Czas:** ok. 7 minut

## Problem, który to rozwiązuje

W rozmowie z Claude wszystko liczy się w tokenach: limit rozmowy, rozmiar
pliku, który da się wkleić, i cena (przy planach Team liczą się limity
użycia, przy API – rachunek). Nikt nie liczy słów ani stron – liczy tokeny.
Jeśli nie wiecie, co to jest, komunikaty typu „conversation is too long"
albo pasek kontekstu w Cowork nic Wam nie powiedzą.

## Co to jest token

Model AI nie widzi tekstu tak jak my. Zanim zdanie trafi do modelu, jest
**cięte na kawałki – tokeny** – a każdy kawałek dostaje numer (ID).
Model pracuje wyłącznie na tych numerach i na tym, jak często występują
obok siebie. „Rozumienie" to statystyka relacji między numerami.

Przykład – zdanie **`Welcome to the boot camp!`** to 6 tokenów:

```
Welcome | to | the | boot | camp | !
```

Uwaga: `boot camp` to dwa tokeny (a gdyby napisać to łącznie, `bootcamp`
też rozpadłoby się na kawałki), wykrzyknik to osobny token. Token to nie słowo – to „kawałek, który
model widział wystarczająco często, żeby dostać własny numer".

## Materiały

- Przeglądarka, strona https://platform.openai.com/tokenizer
  (tokenizer OpenAI – Claude ma własny, ale mechanizm jest identyczny;
  używamy go, bo jest publiczny i wizualny).
- Zdania do wklejenia z sekcji „Kroki" (tekst fikcyjny/jawny).

## Kroki

1. Otwórzcie https://platform.openai.com/tokenizer. U góry wybierzcie
   dowolny nowszy model (np. GPT-5 / GPT-4o) – wynik będzie się nieco
   różnił między modelami, o to właśnie chodzi (każdy producent ma swój
   tokenizer).
2. Wpiszcie w pole tekstowe: `Welcome to the boot camp!` Sprawdźcie
   licznik **Tokens** (powinno być ok. 6) i kolorowe pola pod tekstem –
   każdy kolor to jeden token. Kliknijcie **Token IDs** – to są liczby,
   które „widzi" model.
3. Teraz to samo po polsku: `Witamy na szkoleniu!` Porównajcie liczbę
   tokenów. Zwróćcie uwagę, że polskie słowa dzielą się na więcej
   kawałków (słowo „szkoleniu" to zwykle 2–3 tokeny) – tokenizery były
   trenowane głównie na angielskim.
4. Wklejcie zdanie „urzędowe" (fikcyjne):
   `Wydział Finansowy przekazuje zestawienie wykonania budżetu za sierpień 2026 r. w załączeniu.`
   Zapiszcie: ile znaków, ile tokenów. Policzcie **znaki ÷ tokeny** – to
   Wasza własna reguła kciuka dla polskiego tekstu urzędowego (zwykle
   wychodzi ok. 2–3 znaki na token, po angielsku ≈ 4).
5. Na koniec wklejcie liczbę i datę: `1 234 567,89 zł` oraz `31.08.2026`.
   Zobaczcie, na ile tokenów rozpada się jedna kwota – to tłumaczy, czemu
   arkusz z tysiącami liczb „waży" w tokenach więcej niż akapit prozy.

## Na co zwrócić uwagę

- **Trzy liczby do zapamiętania** (tekst angielski): 1 token ≈ 4 znaki;
  1 000 tokenów ≈ 750 słów; 1 000 000 tokenów ≈ całe dzieła Szekspira
  (≈ 8 pełnych powieści). Po polsku wychodzi ok. 1,5–2× więcej tokenów
  na ten sam tekst.
- **Płaci się za tokeny, nie za słowa.** W planie Team limity użycia też
  są liczone w tokenach – długa rozmowa z wklejonym dużym plikiem
  „zużywa" więcej niż dziesięć krótkich pytań.
- **Liczby są drogie.** Kwota `1 234 567,89` to kilka tokenów, a nie
  jeden. Arkusz Excel przekazany do Claude (Czat lub Code) to setki
  tysięcy tokenów – dlatego w Dniu 2 Claude Code będzie czytał Excela
  skryptem, a nie „wklejał go do rozmowy".
- To narzędzie OpenAI, nie Anthropic – liczba tokenów dla Claude będzie
  nieco inna, ale rząd wielkości ten sam. Chodzi o intuicję, nie o
  dokładny wynik.

## Notatki własne

- Ile tokenów miało Wasze zdanie urzędowe z kroku 4? Jaki wyszedł
  stosunek znaki ÷ tokeny?
- Ile stron A4 ma typowe miesięczne zestawienie, które przekazujecie
  dalej? Ile to w przybliżeniu tokenów (strona ≈ 500 słów ≈ 1 000–1 300
  tokenów po polsku)?
