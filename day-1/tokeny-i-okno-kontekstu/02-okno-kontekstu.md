# Zadanie 2: Okno kontekstu – ile Claude widzi naraz

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
wstęp do **Bloku D: Claude Code – pierwszy kontakt**).

**Cel:** zrozumieć, co to jest okno kontekstu, co się w nim mieści i
dlaczego nawet 1 milion tokenów da się zapełnić w jedno przedpołudnie.
**Poziom:** podstawowy
**Czas:** ok. 6 minut (rozmowa z prowadzącym + tokenizer + jeden szybki test w czacie)

## Problem, który to rozwiązuje

Prędzej czy później każdy trafia na jedną z tych sytuacji: Claude „nie
pamięta", co ustaliliście godzinę temu w tej samej rozmowie; Cowork
pokazuje, że kontekst jest prawie pełny; Claude Code sam z siebie
„kompaktuje" rozmowę. To nie awaria – to okno kontekstu się zapełniło.

## Co to jest okno kontekstu

**Okno kontekstu to maksymalna liczba tokenów, jaką model może
przetworzyć w jednej interakcji – wliczając to, co dostaje na wejściu,
i to, co sam generuje.** Mówi po prostu: „ile informacji model widzi
jednocześnie".

Kluczowe: **wszystko** liczy się do okna, nie tylko Wasze pytanie:

| Co zajmuje miejsce w oknie | Przykład |
|---|---|
| Instrukcje systemowe i zasady | plik `CLAUDE.md`, styl odpowiedzi, opis Waszego projektu |
| Wczytane pliki | wklejony PDF, arkusz odczytany przez Claude Code |
| Cała dotychczasowa rozmowa | każde Wasze pytanie i każda odpowiedź Claude od początku |
| Narzędzia i połączenia | opisy skilli, konektorów, serwerów MCP (z zadań w `../claude-zadania/`) |
| Odpowiedź, którą Claude właśnie pisze | tak, wyjście też się liczy |

Dlatego w Claude Code nie ma sensu prosić „przeczytaj wszystkie 500
plików w folderze" – Claude Code **zarządza kontekstem**: czyta to, co
potrzebne, streszcza, wraca po więcej. To właśnie zobaczycie w Bloku D.

## Ile to jest w praktyce

| Okno kontekstu | Mniej więcej | Przykład modelu (stan na 09.2026) |
|---|---|---|
| 128 000 tokenów | ≈ 300 stron | starsze modele (2023–2024) |
| 200 000 tokenów | ≈ 500 stron | Claude Haiku 4.5 |
| 400 000 tokenów | ≈ 1 200 stron | — |
| 1 000 000 tokenów | ≈ 3 000 stron, całe dzieła Szekspira | Claude Opus 5, Claude Sonnet 5, Gemini 3 |
| 10 000 000 tokenów | cała baza kodu / archiwum naraz | Llama 4 Maverick (Meta) |

(Strony liczone dla tekstu angielskiego; po polsku ok. 1,5–2× mniej –
patrz zadanie 1.) Opus 5 i Sonnet 5 to modele, z których korzystacie w
planie Team – oba mają okno 1 mln tokenów.

## Materiały

- Tokenizer pokazowy OpenAI: https://platform.openai.com/tokenizer (ten
  sam co w zadaniu 1).
- Claude Czat w przeglądarce (konto Urzędu, plan Team).
- Dowolny **jawny** długi tekst do testu – np. treść ustawy z ISAP
  (isap.sejm.gov.pl) skopiowana jako tekst, albo kilka stron z tych
  materiałów szkoleniowych. **Nie** wklejamy dokumentów Urzędu.

## Kroki

1. Rozmowa z prowadzącym (2 min): przejrzyjcie tabelę powyżej. Pytanie
   do grupy: *ile stron ma roczne zestawienie budżetowe razem z
   załącznikami? Ile miesięcznych zestawień zmieściłoby się w oknie
   1 mln tokenów, gdyby wklejać je jako tekst?*
2. Wklejcie długi jawny tekst (np. 20–30 stron ustawy) do tokenizera
   https://platform.openai.com/tokenizer. Odczytajcie licznik **Tokens**
   i odnieście go do tabeli powyżej: jaki to procent okna 200 000? A
   1 000 000? Ile takich dokumentów zmieściłoby się w oknie – i ile
   zostałoby na rozmowę, odpowiedzi i `CLAUDE.md`? Porównajcie też z
   regułą kciuka z zadania 1 (znaki ÷ 2–3).
3. Otwórzcie nową rozmowę w Claude Czat, wklejcie ten sam tekst i
   zadajcie 3–4 pytania o jego treść. Potem
   zapytajcie: *„Jaki był pierwszy tekst, który Ci wkleiłem, i o co
   pytałem na początku?"* – Claude powinien pamiętać, bo całość mieści
   się w oknie. Zapamiętajcie ten test: kiedy Claude **przestaje**
   pamiętać początek, to znak, że okno się zapełniło (lub zostało
   skompaktowane – zadanie 3).
4. Zamknijcie tę rozmowę i **zacznijcie nową** do kolejnego tematu. To
   najprostszy nawyk oszczędzania okna: jedna rozmowa = jeden temat.

## Na co zwrócić uwagę

- **Większe okno = więcej dokumentów, dłuższe rozmowy, bardziej złożone
  zadania.** Ale nie „nieskończoność": okno zapełniają też odpowiedzi
  Claude, opisy narzędzi i cała historia rozmowy – nie tylko pliki.
- **Wklejanie ≠ czytanie.** Jeśli poprosicie Claude Code o przeczytanie
  folderu z setkami zestawień, nie wczyta ich naraz do okna – będzie
  je otwierał po kolei i notował wnioski. To zamierzone. Wy też nie
  czytacie 500 pism jednocześnie.
- **Długa rozmowa = gorsza jakość.** Nawet zanim okno się zapełni,
  model gorzej „widzi" szczegóły zagubione w setkach tysięcy tokenów.
  Nowy temat → nowa rozmowa. W Claude Code: `/clear` (zadanie 3).
- **Bezpieczeństwo:** „w oknie" znaczy „wysłane do dostawcy". Wszystko,
  co zajmuje miejsce w kontekście, opuściło Wasz komputer – to kolejny
  powód, dla którego realne dane Urzędu nie trafiają do Claude bez
  pisemnej zgody (Blok B).

## Notatki własne

- Ile tokenów pokazał tokenizer w kroku 2? Jaki to procent okna
  1 mln – i ile takich dokumentów naraz „uniesie" jedna rozmowa?
- Które z Waszych zadań to „jedna rozmowa – jeden temat", a które
  faktycznie wymagają długiej, wielogodzinnej rozmowy?
