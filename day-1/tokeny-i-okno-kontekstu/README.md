# Tokeny i okno kontekstu — jak Claude „widzi" tekst

Materiał do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
prowadzący: Kasper Kalfas).

**Miejsce w agendzie:** krótki wstęp teoretyczny **na początku Bloku D
(Claude Code – pierwszy kontakt)** albo materiał do samodzielnej pracy
między Blokiem C a D. Zadania 1–4 to praktyka na tokenizerze i w Claude Code,
5–6 to teoria (MCP, wtyczki), 7–8 to dłuższe demo wtyczki Data w Cowork, 9–11 to praca
własna (skill z internetu, własna wtyczka Wydziału, wtyczka dla zespołu). Zadania 1–6
łącznie ok. 42 minuty, zadania 7–8 osobno ok. 45 minut, zadania 9–11 ok. 95 minut. Zadanie 3 wymaga
zainstalowanego Claude Code (`../claude-code/06-instalacja-claude-code-cli.md`),
zadania 6–11 – aplikacji Claude Cowork (`../claude-code/01-czym-jest-cowork.md`).

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
- [ ] **[06 – Wtyczki (plugins) – skille, konektory, komendy i subagenci w jednym](06-wtyczki-czyli-skille-konektory-i-komendy-w-jednym.md)** *(8 min, teoria + podgląd katalogu)*
      — cztery elementy wtyczki, subagenci i ich własne okna kontekstu,
      katalog w Cowork (Customize → Browse plugins) bez instalowania.
- [ ] **[07 – Od surowego Excela do dashboardu – wtyczka Data w Cowork](07-dashboard-z-wtyczka-data.md)** *(25 min, demo prowadzącego / praca własna)*
      — `/explore-data` → `/validate` → czyszczenie do `_v1` →
      `/build-dashboard` na fikcyjnych zestawieniach; klucz odpowiedzi w środku.
- [ ] **[08 – Od analizy do prezentacji dla przełożonego – skill statystyczny i PowerPoint](08-statystyka-i-prezentacja-z-wtyczka-data.md)** *(20 min, demo prowadzącego / praca własna)*
      — skill `statistical-analysis`, prezentacja `.pptx` z wyników zadania 7,
      kontrola liczb na slajdach, Settings → Usage (ile to kosztowało).
- [ ] **[09 – Prognoza wykonania na rok – skill z internetu w Cowork](09-prognoza-z-zewnetrznym-skillem.md)** *(30 min, praca własna)*
      — skills.sh → checklist bezpieczeństwa → upload `SKILL.md` → ARIMA/SARIMA
      na fikcyjnych 36 miesiącach (`materialy/`), sprawdzian „średnia × 12" (Proces 2).
- [ ] **[10 – Własna wtyczka Wydziału – analiza odchyleń i zestawienie dla banku jedną komendą](10-wlasna-wtyczka-wydzialu.md)** *(40 min, praca własna)*
      — szablon opisu wtyczki do wklejenia (profil, struktura działów, dwie
      komendy, skill z zasadami), złożenie przez Cowork, test na plikach z repo,
      prezentacja. Most do `/zamknij-miesiac` w Dniu 2.
- [ ] **[11 – Wtyczka dla zespołu – pobierz, przekaż, wgraj, popraw](11-wtyczka-dla-zespolu.md)** *(25 min, praca własna w parach)*
      — plik `.plugin` jako dokument zespołu: Download → przegląd → Upload na
      drugim koncie, ten sam test u obu, edycja progu, właściciel wersji,
      wyłączanie; reguła „wtyczka czy skill".

## Dane w `materialy/`

Fikcyjne dane do zadania 9: `wykonanie_miesieczne_2023-2025.xlsx` (36 miesięcy
× 8 działów, z celową sezonowością i trendem) i `kalendarz_2026.xlsx` (do
wypełnienia prognozą). `python generuj_prognoza.py` odtwarza oba pliki i
wypisuje klucz odpowiedzi (mnożniki sezonowe i trend per dział).

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
