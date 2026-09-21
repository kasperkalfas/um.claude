# Tokeny i okno kontekstu — jak Claude „widzi" tekst

Materiał do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
prowadzący: Kasper Kalfas).

**Miejsce w agendzie:** krótki wstęp na początku **Bloku D (Claude Code –
pierwszy kontakt)** albo praca własna między Blokiem C a D.

| Zadania | Forma | Czas | Wymaga |
|---|---|---|---|
| 1–4 | praktyka: tokenizer, Claude Czat, Claude Code | ok. 26 min | zad. 3: Claude Code ([instalacja](../claude-code/06-instalacja-claude-code-cli.md)) |
| 5–6 | krótka teoria + podgląd na własnym koncie (MCP, wtyczki) | ok. 16 min | zad. 6: Cowork ([wstęp](../claude-code/01-czym-jest-cowork.md)) |
| 7–8 | demo prowadzącego: wtyczka Data w Cowork | ok. 45 min | Cowork |
| 9–11 | praca własna: skill z internetu, własna wtyczka, wtyczka dla zespołu | ok. 95 min | Cowork |

Każde zadanie: krótki wstęp, kroki z gotowymi poleceniami w ramkach,
„Sprawdź" z kluczem.

## Po co to w ogóle?

Dwie sytuacje, w których „silnik" Claude zaczyna mieć znaczenie: **długa
rozmowa lub duży plik** (Claude „zapomina" początek, streszcza rozmowę,
odmawia wczytania dokumentu) i **praca na wielu plikach w Claude Code**
(nie wczytuje wszystkiego naraz, tylko zarządza tym, co ma „przed
oczami"). Obie sprowadzają się do dwóch pojęć: **token** (jednostka,
w której model liczy tekst) i **okno kontekstu** (ile takich jednostek
widzi jednocześnie).

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
- [ ] **[05 – MCP – jak Claude sięga po dane i narzędzia poza rozmową](05-mcp-czyli-jak-claude-siega-po-dane.md)** *(8 min)*
      — serwer / klient / model; `/mcp` i `/context` na własnym koncie, jedno
      wywołanie krok po kroku, dlaczego podpięcie ERP to decyzja IT i Zamawiającego.
- [ ] **[06 – Wtyczki (plugins) – skille, konektory, komendy i subagenci w jednym](06-wtyczki-czyli-skille-konektory-i-komendy-w-jednym.md)** *(8 min)*
      — cztery elementy wtyczki, subagenci; katalog w Cowork (Customize →
      Browse plugins) i rozbiórka jednej wtyczki finansowej, bez instalowania.
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
