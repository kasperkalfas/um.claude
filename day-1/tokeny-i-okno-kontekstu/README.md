# Tokeny i okno kontekstu — jak Claude „widzi" tekst

Materiał do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
prowadzący: Kasper Kalfas).

**Miejsce w agendzie:** krótki wstęp teoretyczny **na początku Bloku D
(Claude Code – pierwszy kontakt)** albo materiał do samodzielnej pracy
między Blokiem C a D. Pięć zadań, łącznie ok. 34 minuty. Zadanie 3 wymaga
zainstalowanego Claude Code (`../claude-code/06-instalacja-claude-code-cli.md`).

## Po co to w ogóle?

Zwykle nie trzeba wiedzieć, jak działa silnik, żeby prowadzić samochód.
Ale z Claude są dwie sytuacje, w których „silnik" zaczyna mieć znaczenie:

1. **Długa rozmowa albo duży plik** — Claude w pewnym momencie „zapomina"
   początek rozmowy, streszcza ją (Claude Code: `/compact`, Cowork:
   pasek kontekstu po prawej) albo odmawia wczytania zbyt dużego dokumentu.
2. **Praca na wielu plikach w Claude Code** — kiedy prosicie o
   przejrzenie folderu z setkami zestawień, Claude Code **nie wczytuje
   wszystkiego naraz**, tylko zarządza tym, co ma „przed oczami".

Obie sytuacje sprowadzają się do dwóch pojęć: **token** (jednostka, w
której model liczy tekst) i **okno kontekstu** (ile takich jednostek
model może mieć „przed oczami" jednocześnie). Zrozumienie ich pozwala
przewidzieć, kiedy Claude sobie poradzi, kiedy trzeba mu pomóc – i ile to
kosztuje.

## Zadania

- [ ] **[01 – Czym są tokeny – demo na tokenizerze](01-czym-sa-tokeny.md)** *(7 min)*
      — wklejamy zdanie do https://platform.openai.com/tokenizer i patrzymy,
      jak model dzieli je na kawałki. Bonus: polski „kosztuje" więcej niż angielski.
- [ ] **[02 – Okno kontekstu – ile Claude widzi naraz](02-okno-kontekstu.md)** *(6 min)*
      — co się mieści w oknie (pytanie + odpowiedź + pliki + zasady), jak to
      przeliczyć na strony, i dlaczego „500 dokumentów w folderze" to nie to
      samo co „500 dokumentów w rozmowie".
- [ ] **[03 – Kontekst w praktyce: Claude Code i Cowork](03-kontekst-w-claude-code.md)** *(7 min)*
      — `/context`, `/compact`, `/clear` w Claude Code, pasek kontekstu w
      Cowork, i kilka nawyków, które oszczędzają okno.
- [ ] **[04 – „Proszę" i „dziękuję" też kosztują – jak pisać oszczędnie](04-grzecznosc-kosztuje-tokeny.md)** *(6 min)*
      — to samo polecenie w trzech wersjach na tokenizerze: rzeczowe,
      „pismo urzędowe" i P.K.Z.O. Co tniemy, a czego nie.
- [ ] **[05 – MCP – jak Claude sięga po dane i narzędzia poza rozmową](05-mcp-czyli-jak-claude-siega-po-dane.md)** *(8 min, teoria)*
      — serwer / klient / model, co z konektorów trafia do okna kontekstu,
      dlaczego podpięcie ERP to decyzja IT i Zamawiającego, nie użytkownika.

## Trzy liczby do zapamiętania

| Reguła kciuka | Wartość (tekst angielski) | Po polsku |
|---|---|---|
| 1 token | ≈ 4 znaki | ≈ 2–3 znaki |
| 1 000 tokenów | ≈ 750 słów (ok. 1,5 strony A4) | ≈ 400–500 słów |
| 1 000 000 tokenów | ≈ 3 000 stron, całe dzieła Szekspira (≈ 8 powieści) | ≈ 1 500–2 000 stron |

Aktualne modele Claude (Opus 5, Sonnet 5 – stan na wrzesień 2026) mają
okno kontekstu **1 000 000 tokenów**. Brzmi jak „nieskończoność", ale
patrz zadanie 2: okno zapełnia się szybciej, niż się wydaje.

> Zasada bezpieczeństwa danych z Bloku B obowiązuje też tutaj: do
> tokenizera OpenAI i do Claude wklejamy **tylko tekst fikcyjny lub
> jawny** (np. zdania z tych zadań), nigdy fragmenty realnych dokumentów
> Urzędu (`CLAUDE.md`, sekcja o bezpieczeństwie danych).

## Narzędzia

- Tokenizer pokazowy OpenAI: https://platform.openai.com/tokenizer (narzędzie
  pokazowe – Claude ma własny tokenizer, ale zasada działania jest ta sama).
