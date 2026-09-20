# Workshop Opole UM — Claude, Excel, PowerPoint i automatyzacja zadań

Materiały do 3-dniowego szkolenia **„Wykorzystanie systemu AI Claude we
współpracy z Excel, PowerPoint oraz automatyzacja zadań"** dla zespołu
Urzędu Miejskiego w Opolu, organizowanego przez Park Naukowo-Technologiczny
w Opolu.

- **Prowadzący:** Kasper Kalfas (CloudKasper)
- **Terminy:** 22, 23 i 25 września 2026, start 8:30, 4h dydaktyczne dziennie
- **Miejsce:** PNT Opole, ul. Technologiczna 2B, sala 0.05
- **Grupa:** 5 osób, zespół finansowo-księgowy (profil nietechniczny)
- **Agenda:** [agenda/Agenda_szkolenia.md](agenda/Agenda_szkolenia.md)

## Struktura repozytorium

```
agenda/        agenda szkolenia (md + pdf)
day-1/         Dzień 1 – prezentacje i ćwiczenia (Claude Czat, Claude Code)
  claude-zadania/      8 zadań z Claude Czat (3 na żywo w Bloku C + 5 dodatkowych)
  claude-code/         19 krótkich zadań: Cowork, wtyczka Chrome, Claude Code – pierwszy kontakt (Blok D)
  tokeny-i-okno-kontekstu/  5 zadań: tokeny (tokenizer), okno kontekstu, /context /compact /clear, oszczędne polecenia, MCP (wstęp do Bloku D)
  claude-code-cli/     10 zadań Claude Code + Excel: Proces 1 i 2, przepis, skrypt, własna komenda (Dzień 1)
    materialy/         fikcyjne eksporty ERP, zestawienia, generator (generuj_dane.py)
  materialy/           fikcyjne pliki Excel do ćwiczeń z czatu i Bloku D
materialy/     materiały pomocnicze (data storytelling, DataPOV) – Dzień 3
umowa/         dokumenty umowne i wzory (lokalnie, poza repozytorium)
CLAUDE.md      kontekst projektu dla Claude Code (lokalnie, poza repozytorium)
```

Część plików jest celowo wyłączona z repozytorium przez `.gitignore`
(umowa, notatki robocze, kontekst dla Claude Code) — patrz sekcja
„Bezpieczeństwo danych".

## Program

| Dzień | Data | Temat | Materiały |
|---|---|---|---|
| 1 | 22.09.2026 | Podstawy AI, dane jako fundament, Claude Czat, pierwszy kontakt z Claude Code, Power BI / Excel | `day-1/` — gotowe |
| 2 | 23.09.2026 | Praca na komórkach Excela i automatyzacja z Claude Code (CLI) | `day-1/claude-code-cli/` — ćwiczenia i dane gotowe, prezentacja do przygotowania |
| 3 | 25.09.2026 | DataPOV, prezentacje danych z Claude, wizualizacja w PowerPoint, mapowanie procesów | `materialy/` — kontekst gotowy, prezentacje do przygotowania |

### Dzień 1 — zawartość

| Blok | Czas | Temat | Plik |
|---|---|---|---|
| A | 30 min | AI Intro → ML & Gen AI | `day-1/day-1-ai-intro.pptx` |
| B | 30 min | Dane jako fundament — „Data First, AI Second" | `day-1/day-1-data-first-ai-second.pptx` |
| C | 60 min | Claude Czat w przeglądarce — interfejs i promptowanie | `day-1/day1-claude.pptx` + [`day-1/claude-zadania/`](day-1/claude-zadania/README.md) |
| D | 60 min | Claude Code — pierwszy kontakt | [`day-1/claude-code/`](day-1/claude-code/README.md), zad. 6–16 (1–5: Cowork i wtyczka Chrome, praca własna); wstęp: [`day-1/tokeny-i-okno-kontekstu/`](day-1/tokeny-i-okno-kontekstu/README.md) |
| E | 60 min | Power BI / Excel z asystą AI | — |

### Dzień 1 — ćwiczenia Claude Code + Excel (`day-1/claude-code-cli/`)

Szczegóły, mapowanie na bloki i klucz odpowiedzi: [day-1/claude-code-cli/README.md](day-1/claude-code-cli/README.md).

| # | Zadanie | Część |
|---|---|---|
| 1 | Instalacja i pierwsze uruchomienie | Dzień 1, cz. 1 |
| 2 | Nawigacja po folderach w języku naturalnym | Dzień 1, cz. 1 |
| 3 | „Otwórz ten Excel i powiedz, co w nim jest" | Dzień 1, cz. 1 |
| 4 | Błędy na poziomie komórek — znajdź i napraw | Dzień 1, cz. 2 |
| 5 | Operacje na komórkach w języku naturalnym | Dzień 1, cz. 2 |
| 6 | Proces 1: z eksportu ERP do zestawienia miesięcznego | Dzień 1, cz. 3 |
| 7 | Proces 2: powtarzalny przepis z miesięcznego do rocznego | Dzień 1, cz. 3 |
| 8 | Kolejny miesiąc od początku do końca + raport kontrolny | Dzień 1, cz. 3/4 |
| 9 | Gdy Claude Code się myli — obsługa błędów | Dzień 1, cz. 4 |
| 10 | CLAUDE.md z zasadami Wydziału i własna komenda „zamknij miesiąc" | Dzień 1, cz. 4 |

Dane wsadowe (`day-1/claude-code-cli/materialy/`) są fikcyjne i odtwarzalne:
`python generuj_dane.py` nadpisuje wszystkie pliki czystą wersją i
wypisuje klucz odpowiedzi.

## Ćwiczenia z Claude (`day-1/claude-zadania/`)

Szczegóły, kolejność i minutaż: [day-1/claude-zadania/README.md](day-1/claude-zadania/README.md).

**Na żywo, Blok C (60 min):**

1. Formuła P.K.Z.O. — skuteczne prompty (Persona, Kontekst, Zadanie, Ograniczenia)
2. Funkcje interfejsu Claude — pliki, Artifacts, styl, pamięć
3. Bezpieczna analiza arkusza budżetowego — wykrywanie błędów i podsumowanie

**Materiał dodatkowy (praca własna po szkoleniu):**

4. Google Calendar (+ odpowiednik Microsoft 365 w realiach Urzędu)
5. Podróże: Booking.com i Kiwi.com (z rozróżnieniem od delegacji służbowej)
6. Plany i limity — darmowy Claude, plan Team Urzędu, Claude Code
7. Własny skill — notatka o odchyleniach budżetowych
8. Gotowe skille z internetu — które przydadzą się w Urzędzie

### Pliki wsadowe (`day-1/materialy/`)

Wszystkie dane są **fikcyjne**, wzorowane na realnym procesie miesięcznego
zestawienia budżetowego (eksport z ERP → Excel):

| Plik | Zawartość | Użycie |
|---|---|---|
| `zestawienie_przykladowe.xlsx` | 7 wydziałów, bez błędów | zad. 2, 8 |
| `zestawienie_miesieczne_PRZYKLAD.xlsx` | 3 celowe błędy: pusty wiersz, niespójne daty, scalona komórka | zad. 3 (klucz odpowiedzi w README zadań) |
| `zestawienie_miesieczne_PODSUMOWANIE.xlsx` | 10 wydziałów, 7 przekracza plan | zad. 3, 7, 8 |

## Bezpieczeństwo danych

Wszystkie ćwiczenia działają **wyłącznie na danych fikcyjnych lub
zanonimizowanych**, wzorowanych na procesach Urzędu. Do Claude ani innych
systemów AI nie trafiają prawdziwe dane budżetowe, dane osobowe ani dane
poufne Urzędu. Zasada ta jest omawiana z uczestnikami w Dniu 1 (Blok B) i
powtarzana w każdym zadaniu; dotyczy także integracji z usługami
zewnętrznymi (konektory, skille).

Z tego samego powodu dokumenty umowne i notatki robocze zawierające
szczegóły współpracy pozostają lokalnie, poza repozytorium.

## Status i do zrobienia

- [x] Dzień 1: prezentacje Bloków A–C, ćwiczenia z Claude Czat i Claude Code (Blok D), pliki wsadowe
- [ ] Dzień 1: materiały do Bloku E (Power BI / Excel)
- [x] Dzień 1: 10 ćwiczeń z Claude Code + fikcyjne dane wsadowe z generatorem
- [ ] Dzień 1: prezentacja wprowadzająca do Claude Code CLI (Blok A) i sprawdzenie wymagań technicznych na laptopach uczestników (Python, Git, Claude Code)
- [ ] Dzień 3: prezentacje (DataPOV, storytelling, PowerPoint)
- [ ] Po szkoleniu: listy obecności, certyfikaty, protokół realizacji

## Konwencje

- Każdemu istotnemu dokumentowi źródłowemu (pdf/docx/pptx) towarzyszy
  plik `kontekst_*.md` lub `opis_*.md` ze streszczeniem po polsku.
- Zadania w `claude-zadania/` mają jednolitą strukturę: cel, poziom, czas,
  materiały, kroki, „Na co zwrócić uwagę", „Notatki własne". Numer w nazwie
  pliku odpowiada numerowi w nagłówku „Zadanie N".
