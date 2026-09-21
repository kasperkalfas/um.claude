# Zadanie 1: Czym są tokeny – demo na tokenizerze

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
wstęp do **Bloku D: Claude Code – pierwszy kontakt**).

**Cel:** zobaczyć na liczniku, że model nie czyta słów, tylko „tokeny" –
i wyczuć, ile tokenów zajmuje typowy tekst urzędowy.
**Poziom:** podstawowy
**Czas:** ok. 7 minut

## W dwóch zdaniach

Zanim tekst trafi do modelu, jest **cięty na kawałki – tokeny** – a każdy
kawałek dostaje numer. Wszystko w Claude liczy się w tokenach: limit
rozmowy, rozmiar pliku, który da się wkleić, i zużycie limitu w planie
Team. Nikt nie liczy słów ani stron.

## Materiały

- https://platform.openai.com/tokenizer – tokenizer OpenAI (Claude ma
  własny, ale mechanizm jest ten sam; ten jest publiczny i kolorowy).
- Zdania z kroków poniżej. **Tylko tekst fikcyjny** – nigdy fragmenty
  realnych dokumentów Urzędu.

## Kroki

1. Otwórzcie tokenizer. U góry wybierzcie dowolny nowszy model.
2. Wpiszcie:

   ```
   Welcome to the boot camp!
   ```

   **Sprawdź:** licznik **Tokens** ≈ 6. Każdy kolor pod tekstem = jeden
   token. Kliknijcie **Token IDs** – te liczby „widzi" model.

3. To samo po polsku:

   ```
   Witamy na szkoleniu!
   ```

   **Sprawdź:** więcej tokenów niż po angielsku – „szkoleniu" to 2–3
   kawałki. Tokenizery uczyły się głównie na angielskim.

4. Zdanie urzędowe (fikcyjne):

   ```
   Wydział Finansowy przekazuje zestawienie wykonania budżetu za sierpień 2026 r. w załączeniu.
   ```

   Zapiszcie liczbę znaków i tokenów, policzcie **znaki ÷ tokeny**.
   **Sprawdź:** wychodzi ok. 2–3 znaki na token (po angielsku ≈ 4). To
   Wasza reguła kciuka dla polskiego tekstu.

5. Kwota i data:

   ```
   1 234 567,89 zł oraz 31.08.2026
   ```

   **Sprawdź:** jedna kwota to kilka tokenów, nie jeden. Dlatego arkusz
   z tysiącami liczb „waży" więcej niż akapit prozy.

## Na co zwrócić uwagę

- **Trzy liczby do zapamiętania** (tekst angielski): 1 token ≈ 4 znaki;
  1 000 tokenów ≈ 750 słów; 1 000 000 tokenów ≈ całe dzieła Szekspira.
  Po polsku 1,5–2× więcej tokenów na ten sam tekst.
- **Liczby są drogie.** Dlatego w Dniu 2 Claude Code będzie czytał Excela
  skryptem, a nie „wklejał go do rozmowy".
- Narzędzie jest OpenAI, nie Anthropic – rząd wielkości ten sam, chodzi
  o intuicję.

## Notatki własne

- Ile tokenów miało zdanie z kroku 4? Jaki stosunek znaki ÷ tokeny?
- Ile stron A4 ma Wasze miesięczne zestawienie? Ile to tokenów
  (strona ≈ 1 000–1 300 tokenów po polsku)?
