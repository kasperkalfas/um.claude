# Baza wiedzy Wydziału – Obsidian + Claude Code (Dzień 2)

Materiały do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
prowadzący: Kasper Kalfas).

**Miejsce w agendzie:** Dzień 2, **Blok D (60 min): Ćwiczenia własne**
– jako alternatywa dla „odtworzenia fragmentu własnego procesu", albo
praca własna po szkoleniu. Wymaga Claude Code z Bloku A. Cztery zadania
tworzą jedną ciągłą ścieżkę (ok. 70 min) na jednym vaultcie; da się
zrobić 1–2 na szkoleniu, 3–4 samodzielnie.

**Dlaczego Obsidian:** vault to zwykły folder z plikami `.md` – dokładnie
to, na czym Claude Code pracuje od Dnia 1. Żadnej integracji, żadnej
wtyczki: Claude pisze pliki w terminalu, Obsidian pokazuje je jako
notatki z linkami i grafem. Wiedza Wydziału („jak zamykamy miesiąc",
„skąd dane działu 851", „co ustaliliśmy 10.09") przestaje być w głowie
jednej osoby.

## Zadania

- [ ] **[01 – Obsidian i Claude Code w jednym folderze – vault, struktura, pierwsza notatka](01-obsidian-i-claude-code-w-jednym-folderze.md)** *(15 min)*
      — vault = folder; `CLAUDE.md` z 7 zasadami bazy; struktura
      `00-Start … 90-Szablony`; notatka o dziale 851 ze źródłem i
      linkiem do nieistniejącej notatki; test dwóch okien.
- [ ] **[02 – Ze starej instrukcji, maila i CSV do procedur – notatki, które się linkują](02-ze-starych-instrukcji-do-procedur.md)** *(20 min)*
      — najpierw tabela różnic 2019 → 2026 (7 zmian), potem procedura
      zamknięcia miesiąca ze śladem zmian; 8 notatek działów z CSV;
      graf i lista szarych linków jako kolejka; kontrola faktów spoza
      źródeł.
- [ ] **[03 – Pytania do bazy – odpowiedzi ze źródłem, „nie ma w bazie" i dziennik decyzji](03-pytania-do-bazy-i-dziennik-decyzji.md)** *(15 min)*
      — sześć pytań nowej osoby z kluczem (w tym sprzeczne źródła i
      Proces 3 = „nie ma w bazie"); notatka ze spotkania → 3 decyzje +
      sprawy otwarte; decyzja poniżej progu a procedura.
- [ ] **[04 – Utrzymanie bazy – własne komendy, przegląd, wersje w Git i co do bazy nie wchodzi](04-utrzymanie-bazy-komendy-wersje-i-granice.md)** *(20 min)*
      — zasada „tylko z bazy" w `CLAUDE.md`; `/nowa-decyzja`,
      `/przeglad-bazy` (przeterminowane, zerwane linki, sieroty);
      Git: zapis, różnica, cofnięcie; eksport `.docx` ze stopką; notatka
      „Czego nie wpisujemy".

## Dane w `materialy/`

Wszystko fikcyjne – materiał szkoleniowy. Kopiowane do vaulta w zad. 1.

| Plik | Co to | Rola w zadaniach |
|---|---|---|
| `zrodla/instrukcja_zamkniecia_miesiaca_2019.txt` | stara instrukcja (9 kroków, w połowie nieaktualna) | zad. 2 – źródło historyczne |
| `zrodla/email_skarbnik_terminy_2026.txt` | mail z 6 zasadami obowiązującymi od 2026 | zad. 2–3 – źródło obowiązujące; **sprzeczne** z 2019 w 7 punktach |
| `zrodla/notatka_spotkanie_2026-09-10.txt` | notatka: 3 decyzje + 2 sprawy otwarte | zad. 3 – dziennik decyzji |
| `zrodla/slownik_dzialow.csv` | 8 działów (te same, co w zestawieniach Dnia 1 i prezentacji budżetowej) | zad. 1–2 – notatki słownikowe |
| `szablony/procedura.md`, `pojecie.md`, `decyzja.md` | szablony z frontmatterem | wszystkie |
| `CLAUDE_vault.md` | zasady dla Claude Code w vaultcie (7 punktów) | kopiowany jako `CLAUDE.md` |

**Klucz różnic 2019 → 2026** jest w zadaniu 2 (tabela), klucz odpowiedzi
na sześć pytań – w zadaniu 3.

## Wymagania techniczne

| Co | Uwaga |
|---|---|
| Claude Code + Git for Windows + konto Team | jak w ścieżce `../../day-1/claude-code-cli/` |
| Obsidian ([obsidian.md](https://obsidian.md); od 2025 r. bezpłatny także do użytku służbowego, bez licencji komercyjnej) | instalator nie wymaga uprawnień administratora; jeśli IT blokuje – wersja portable |
| Folder lokalny `C:\Szkolenie\dzien-2\baza-wydzial-finansowy` | **nie** OneDrive/dysk wspólny Urzędu na szkoleniu |
| (zad. 4) generowanie `.docx` | Claude Code robi to skryptem (python-docx) – `pip install python-docx`, jeśli brak |

> Zasada bezpieczeństwa danych z Dnia 1 (Blok B) obowiązuje w całości:
> Claude Code czyta cały vault i wysyła treść do dostawcy modelu. Do
> bazy nie trafiają nazwiska, kwoty z roboczych zestawień, treść umów
> ani cokolwiek z realnych plików Urzędu bez pisemnej zgody – zadanie 4
> kończy się notatką „Czego nie wpisujemy".
