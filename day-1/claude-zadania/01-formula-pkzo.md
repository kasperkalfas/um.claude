# Zadanie 1: Formuła P.K.Z.O. – prompting dla każdego

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok C, 60 min: Claude Czat w przeglądarce** – pogłębione poznanie
interfejsu Claude i dobrych praktyk promptowania).

**Cel:** nauczyć się budować skuteczne zapytania (prompty) według prostej
formuły P.K.Z.O. i zobaczyć na własnym przykładzie, jak bardzo poprawia to
jakość odpowiedzi.
**Poziom:** podstawowy
**Czas:** ok. 20 minut

> **Przypomnienie z Bloku B:** ćwiczcie wyłącznie na przykładowych/fikcyjnych
> liczbach i nazwach, nigdy na prawdziwych danych budżetowych urzędu –
> zasady bezpiecznego użycia danych w Claude omówiliśmy w poprzednim bloku.

Dobry prompt to klucz do uzyskania precyzyjnych i użytecznych odpowiedzi od
AI. Formuła P.K.Z.O. to prosta metoda, która pomoże Ci konstruować skuteczne
zapytania.

## Schemat P.K.Z.O.

| Litera | Element | Co zawiera | Przykład |
|--------|---------|------------|----------|
| **P** | Persona (Rola) | Nadaj Claude konkretną rolę eksperta, który ma Ci pomóc. | *"Jesteś ekspertem finansowym…", "Jesteś doświadczonym nauczycielem…", "Jesteś specjalistą HR…"* |
| **K** | Kontekst (Sytuacja) | Opisz sytuację, w której się znajdujesz. Podaj tło i ważne szczegóły. | *"Pracujemy nad budżetem na 2027 rok…", "Organizuję szkolenie dla 20 osób…", "Przygotowuję się do rozmowy kwalifikacyjnej…"* |
| **Z** | Zadanie (Cel) | Określ konkretny cel – co dokładnie ma zrobić Claude? | *"Stwórz tabelę…", "Napisz e-mail…", "Przygotuj listę kroków…", "Wygeneruj pomysły…"* |
| **O** | Ograniczenia (Ramy i format) | Określ format odpowiedzi, długość, styl, język lub inne wymagania. | *"Użyj PLN, max 10 pozycji, format tabeli", "W punktach, maksymalnie 5 punktów", "Ton formalny, do 200 słów"* |

## Materiały

Konto na [claude.ai](https://claude.ai) – instrukcja logowania znajduje się
w [README](README.md#jak-zacząć-pracę-z-claude).

## Kroki

1. Zaloguj się na [claude.ai](https://claude.ai) i rozpocznij nową rozmowę.
2. **Zadaj najpierw "słabe" pytanie** – celowo ogólne, bez formuły, np.:

   ```
   Napisz notatkę o wzroście wydatków.
   ```

   Przeczytaj odpowiedź i oceń, na ile nadawałaby się do wysłania dalej bez
   poprawek.
3. **Teraz zbuduj prompt według P.K.Z.O.** – możesz wykorzystać poniższy
   przykład lub napisać własny na ten sam temat:

   ```
   P: Jesteś doradcą finansowym wspierającym urząd w komunikacji z radnymi.
   K: W zestawieniu miesięcznym wydatki na utrzymanie dróg wzrosły o 8%
      względem planu, głównie przez wyższe ceny materiałów.
   Z: Przygotuj krótką notatkę wyjaśniającą ten wzrost, którą można wysłać
      radnym przed sesją.
   O: Maksymalnie 6 zdań, ton rzeczowy i spokojny, bez żargonu finansowego,
      po polsku.
   ```

4. **Porównaj obie odpowiedzi.** Która jest bardziej konkretna? Która
   nadaje się do użycia bez poprawek?
5. **Zmień jedno ograniczenie** i wyślij prompt ponownie – np. zamiast
   6 zdań poproś o 3, albo zmień ton na bardziej swobodny:

   ```
   Skróć to do 3 zdań i napisz mniej formalnie.
   ```

   Zobacz, jak jeden element formuły zmienia efekt.
6. **Napisz własny prompt P.K.Z.O.** dotyczący Twojej pracy lub
   wolontariatu i sprawdź wynik.


## 💡 Przykład 1: Przygotowanie ogłoszenia o pracę

### ❌ Słaby prompt:
```
Napisz ogłoszenie o pracę dla sekretarki.
```

### ✅ Dobry prompt (P.K.Z.O.):
```
PERSONA: Jesteś specjalistą HR z 10-letnim doświadczeniem w rekrutacji.

KONTEKST: Nasza szkoła poszukuje osoby na stanowisko sekretarki/sekretarza 
do obsługi sekretariatu szkolnego. Praca na pełen etat, wymagana obsługa 
programu Vulcan, kontakt z rodzicami i nauczycielami.

ZADANIE: Stwórz profesjonalne ogłoszenie o pracę, które przyciągnie 
odpowiednich kandydatów.

OGRANICZENIA:
- Długość: do 300 słów
- Struktura: stanowisko, opis, wymagania, oferujemy, kontakt
- Ton: profesjonalny ale przyjazny
- Wynagrodzenie: 4500-5500 zł brutto (podaj widełki)
```

---

## 💡 Przykład 2: Planowanie budżetu wydziału

### ❌ Słaby prompt:
```
Pomóż mi z budżetem.
```

### ✅ Dobry prompt (P.K.Z.O.):
```
PERSONA: Jesteś doświadczonym doradcą finansowym wspierającym jednostki
samorządowe.

KONTEKST: Planuję (przykładowy, fikcyjny) budżet wydziału na 2027 rok.
Roczny budżet to około 600 000 zł. Chcę lepiej kontrolować wydatki i
przygotować się do rozmowy o priorytetach na przyszły rok.

ZADANIE: Stwórz szablon prostego budżetu rocznego z podstawowymi kategoriami 
kosztów, które powinienem monitorować.

OGRANICZENIA:
- Format: tabela w markdown
- Waluta: PLN
- Maksymalnie 12 kategorii kosztów
- Podziel na: koszty stałe i zmienne
- Dodaj kolumnę z procentowym udziałem w budżecie
- Dodaj krótki komentarz (2-3 zdania) do każdej kategorii
```



## Na co zwrócić uwagę

- Nie każdy prompt musi mieć wszystkie cztery elementy – ale im bardziej
  złożone zadanie, tym bardziej się opłacają. Najczęściej pomijanym, a
  najbardziej przydatnym elementem są **Ograniczenia** (O).
- Kontekst (K) to miejsce, w którym łatwo nieświadomie podać **dane
  osobowe** – nie wklejaj do promptu imion, adresów, numerów PESEL ani
  danych innych osób. Opisz sytuację ogólnie ("uczestnik szkolenia"
  zamiast konkretnego nazwiska).
- Rozmowa z Claude jest **kontekstowa** – nie musisz powtarzać całego
  promptu, żeby coś poprawić. Wystarczy dopisać *"Skróć to do 4 punktów"*
  albo *"Napisz to prostszym językiem"*.
- Jeśli odpowiedź nie trafia w Twoje potrzeby, zwykle szybciej jest
  **doprecyzować prompt**, niż wielokrotnie prosić o poprawki – to także
  oszczędza limit wiadomości na bezpłatnym planie.

## Notatki własne

- Czym różniła się odpowiedź na "słabe" pytanie od odpowiedzi na prompt
  P.K.Z.O.?
- Który element formuły (P, K, Z czy O) najbardziej zmienił wynik w Twoim
  przypadku?
- Zapisz tutaj swój najlepszy prompt P.K.Z.O., żeby móc go użyć ponownie:


