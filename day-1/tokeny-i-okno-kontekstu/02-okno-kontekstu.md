# Zadanie 2: Okno kontekstu – ile Claude widzi naraz

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
wstęp do **Bloku D: Claude Code – pierwszy kontakt**).

**Cel:** zmierzyć, ile okna kontekstu zajmuje jeden długi dokument,
i zobaczyć w czacie, że Claude pamięta początek rozmowy – dopóki okno
się nie zapełni.
**Poziom:** podstawowy
**Czas:** ok. 6 minut

## W trzech zdaniach

**Okno kontekstu to maksymalna liczba tokenów, jaką model ma „przed
oczami" w jednej rozmowie.** Liczy się do niego **wszystko**: Wasze
pytania, odpowiedzi Claude, wklejone pliki, `CLAUDE.md`, opisy skilli
i konektorów. Gdy Claude „nie pamięta", co ustaliliście godzinę temu,
albo Cowork pokazuje pełny pasek kontekstu – to nie awaria, to okno się
zapełniło.

| Okno | ≈ stron (ang.) | Modele (09.2026) |
|---|---|---|
| 200 000 | 500 | Claude Haiku 4.5 |
| 1 000 000 | 3 000 | **Claude Opus 5, Sonnet 5** (plan Team Urzędu) |

Po polsku ok. 1,5–2× mniej stron (zadanie 1).

## Materiały

- https://platform.openai.com/tokenizer
- Claude Czat (konto Urzędu).
- Długi **jawny** tekst, np. ustawa z ISAP (isap.sejm.gov.pl) skopiowana
  jako tekst. **Nie** dokumenty Urzędu.

## Kroki

1. **Zmierzcie dokument.** Wklejcie 20–30 stron ustawy do tokenizera.
   Odczytajcie **Tokens**.

   **Sprawdź:** jaki to procent okna 200 000? A 1 000 000? Ile takich
   dokumentów zmieściłoby się w jednej rozmowie – i ile zostałoby na
   pytania, odpowiedzi i `CLAUDE.md`?

2. **Test pamięci.** Nowa rozmowa w Claude Czat, wklejcie ten sam tekst
   i zadajcie 3–4 pytania o treść, np.:

   ```
   Czego dotyczy art. 1 tego tekstu?
   ```

   ```
   Wypisz wszystkie terminy (liczby dni) wymienione w tekście.
   ```

3. Potem zapytajcie:

   ```
   Jaki był pierwszy tekst, który Ci wkleiłem, i o co pytałem
   na początku?
   ```

   **Sprawdź:** Claude pamięta – całość mieści się w oknie. Kiedy
   **przestanie** pamiętać początek, to znak, że okno się zapełniło
   albo zostało skompaktowane (zadanie 3).

4. **Nowy temat = nowa rozmowa.** Zamknijcie tę rozmowę. To najprostszy
   nawyk oszczędzania okna.

## Na co zwrócić uwagę

- **Większe okno ≠ nieskończoność.** Zapełniają je też odpowiedzi
  Claude, opisy narzędzi i cała historia rozmowy.
- **Wklejanie ≠ czytanie.** Claude Code nie wczyta 500 plików naraz –
  otwiera po kolei i notuje wnioski. To zamierzone.
- **Długa rozmowa = gorsza jakość**, jeszcze zanim okno się zapełni.
  W Claude Code: `/clear` (zadanie 3).
- **„W oknie" = „wysłane do dostawcy".** Kolejny powód, dla którego
  realne dane Urzędu nie trafiają do Claude bez pisemnej zgody (Blok B).

## Notatki własne

- Ile tokenów pokazał tokenizer w kroku 1? Jaki procent okna 1 mln?
- Które z Waszych zadań to „jedna rozmowa – jeden temat", a które
  naprawdę wymagają długiej rozmowy?
