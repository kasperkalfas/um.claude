# Workshop Opole UM — Claude, Excel, PowerPoint i automatyzacja zadań

Materiały do 3-dniowego szkolenia **„Wykorzystanie systemu AI Claude we współpracy
z Excel, PowerPoint oraz automatyzacja zadań"** dla zespołu finansowo-księgowego
Urzędu Miejskiego w Opolu. Organizator: Park Naukowo-Technologiczny w Opolu.

| | |
|---|---|
| **Prowadzący** | Kasper Kalfas (CloudKasper) |
| **Terminy** | 22, 23 i 25 września 2026, start 8:30, 4 h dydaktyczne dziennie |
| **Miejsce** | PNT Opole, ul. Technologiczna 2B, sala 0.05 |
| **Grupa** | 5 osób, profil księgowo-finansowy, nietechniczny |
| **Agenda** | [agenda/Agenda_szkolenia.md](agenda/Agenda_szkolenia.md) |

> **Wszystkie dane w ćwiczeniach są fikcyjne.** Do Claude ani innych systemów AI nie
> trafiają prawdziwe dane budżetowe, osobowe ani poufne Urzędu — patrz
> [Bezpieczeństwo danych](#bezpieczeństwo-danych).

## Plan szkolenia

| Dzień | Data | Temat | Materiały |
|---|---|---|---|
| 1 | 22.09 | Podstawy AI, dane jako fundament, Claude Czat, pierwszy kontakt z Claude Code | `day-1/` |
| 2 | 23.09 | Excel i automatyzacja z Claude Code; dodatki Claude w Excelu i PowerPoincie | `day-1/claude-code-cli/`, `day-2/` |
| 3 | 25.09 | DataPOV, prezentacje z Claude, wizualizacja danych, mapowanie procesów | `day-2/DataPOV-punkt-widzenia-na-dane.pptx`, `day-2/claude-w-powerpoincie/` |

### Dzień 1 — bloki

| Blok | Czas | Temat | Materiały |
|---|---|---|---|
| A | 30 min | AI Intro → ML & Gen AI | `day-1/day-1-ai-intro.pptx` |
| B | 30 min | Dane jako fundament — „Data First, AI Second" | `day-1/day-1-Data-First-AI-Second.pptx` |
| C | 60 min | Claude Czat — interfejs i promptowanie | `day-1/day1-claude.pptx` + [`claude-zadania/`](day-1/claude-zadania/README.md) |
| D | 60 min | Claude Code — pierwszy kontakt | [`claude-code/`](day-1/claude-code/README.md) zad. 6–16; wstęp: [`tokeny-i-okno-kontekstu/`](day-1/tokeny-i-okno-kontekstu/README.md) |
| E | 60 min | Power BI / Excel z asystą AI | — (do przygotowania) |

## Zestawy ćwiczeń

Każdy folder ma własny `README.md` z kolejnością, minutażem i kluczem odpowiedzi.

| Folder | Zadań | Kiedy | O czym |
|---|---|---|---|
| [`day-1/claude-zadania/`](day-1/claude-zadania/README.md) | 8 | Dzień 1, Blok C (1–3 na żywo) + praca własna (4–8) | Claude Czat: P.K.Z.O., interfejs, analiza arkusza, konektory, plany i limity, skille |
| [`day-1/claude-code/`](day-1/claude-code/README.md) | 19 | Dzień 1, Blok D (6–16) + praca własna | Cowork, wtyczka Chrome, Claude Code w terminalu, nawigacja, tryby pracy, `CLAUDE.md` |
| [`day-1/tokeny-i-okno-kontekstu/`](day-1/tokeny-i-okno-kontekstu/README.md) | 11 | Dzień 1, wstęp do Bloku D + demo + praca własna | Tokeny, okno kontekstu, `/context` `/compact` `/clear`, MCP, wtyczki; dashboard i prezentacja z wtyczką Data; prognoza; własna wtyczka Wydziału |
| [`day-1/claude-code-cli/`](day-1/claude-code-cli/README.md) | 10 | Dzień 1–2 | Claude Code + Excel na Procesie 1 i 2: błędy w komórkach, przepis miesięczny → roczny, raport kontrolny, `CLAUDE.md`, komenda `/zamknij-miesiac` |
| [`day-2/claude-w-excelu/`](day-2/claude-w-excelu/README.md) | 9 | Dzień 2 | Dodatek Claude w Excelu: EDA, formuły, wykresy, sortowanie, filtrowanie, formatowanie warunkowe, braki danych, model finansowy inwestycji |
| [`day-2/claude-w-powerpoincie/`](day-2/claude-w-powerpoincie/README.md) | 6 | Dzień 2 (instalacja) → Dzień 3 | Dodatek Claude w PowerPoincie: prezentacja z jednego zdania, notatki prelegenta, slajd ze źródła, szablon Urzędu, poprawianie gotowej prezentacji |
| [`day-2/obsidian-baza-wiedzy/`](day-2/obsidian-baza-wiedzy/README.md) | 4 | Dzień 2, Blok D / praca własna | Baza wiedzy Wydziału w Obsidianie budowana Claude Code: `CLAUDE.md`, procedury ze starych instrukcji, dziennik decyzji, komendy i Git |

## Struktura repozytorium

```
agenda/     agenda szkolenia (md + pdf)
day-1/      prezentacje Bloków A–C (.pptx) + 4 zestawy ćwiczeń (patrz wyżej)
day-2/      dodatki Claude w Excelu i PowerPoincie, baza wiedzy w Obsidianie,
            prezentacja DataPOV (DataPOV-punkt-widzenia-na-dane.pptx — Blok A Dnia 3)
day-3/      (pusty — Bloki B–E Dnia 3 do przygotowania)
materialy/  materiały pomocnicze do Dnia 3 (data storytelling, DataPOV)
umowa/      dokumenty umowne i wzory — lokalnie, poza repozytorium
CLAUDE.md   kontekst projektu dla Claude Code — lokalnie, poza repozytorium
```

Pliki z `.gitignore` (umowa, notatki robocze, `CLAUDE.md`) nie trafiają do
repozytorium ze względu na poufność.

## Dane wsadowe

Każdy zestaw ma podfolder `materialy/` z fikcyjnymi plikami. Tam, gdzie jest
generator, `python <skrypt>.py` odtwarza czyste pliki i wypisuje klucz odpowiedzi.

| Folder | Pliki | Generator |
|---|---|---|
| `day-1/materialy/` | 3 zestawienia miesięczne (jedno z 3 celowymi błędami, jedno z 10 wydziałami) + `test-claude-code/` | — |
| `day-1/claude-code-cli/materialy/` | eksporty ERP (CSV), szablon miesięczny, plik roczny 2026, plik z błędami | `generuj_dane.py` |
| `day-1/tokeny-i-okno-kontekstu/materialy/` | wykonanie miesięczne 2023–2025, kalendarz 2026 | `generuj_prognoza.py` |
| `day-2/claude-w-excelu/materialy/` | `Human_Resources.xlsx` (1 470 × 35, kadrowy), założenia termomodernizacji | `generuj_termomodernizacja.py` |
| `day-2/claude-w-powerpoincie/materialy/` | `wykonanie_budzetu_2026_8m.pptx` (prezentacja do poprawy) | `generuj_prezentacja.py` |
| `day-2/obsidian-baza-wiedzy/materialy/` | fikcyjne źródła (instrukcje, maile, CSV) i szablony notatek | — |

Układ plików Excel (kody działów w kolumnie A, wiersze 6–13) jest wspólny dla
szablonu miesięcznego i pliku rocznego, żeby „dopasowanie po kodzie działu" było
ćwiczone jawnie.
