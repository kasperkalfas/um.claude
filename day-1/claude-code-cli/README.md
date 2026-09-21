# Zadania: Claude Code + Excel — Proces 1 i Proces 2

Zestaw 10 ćwiczeń z Claude Code dla zespołu Urzędu Miejskiego w Opolu, od
pierwszego uruchomienia do zamknięcia miesiąca jedną komendą. Wszystkie
zadania odwzorowują realne procesy Wydziału na **fikcyjnych danych**:

> **Jak to się ma do [`../claude-code/`](../claude-code/README.md)?** Tamten
> zestaw (19 krótkich zadań) to **pierwszy kontakt** – demo w Bloku D
> Dnia 1 (Cowork, wtyczka Chrome, terminal, nawigacja). Ten folder to
> **ścieżka Excel/procesy** (Dzień 1): praca na komórkach, Proces 1 i 2,
> przepis, skrypt, raport kontrolny, własna komenda. Zadania 1–3 tutaj
> celowo powtarzają podstawy z pierwszego kontaktu – jako samodzielna
> rozgrzewka na laptopach uczestników. Folder jest samodzielny (zadania +
> `materialy/` + generator) – kopiuje się w całości na pendrive.

- **Proces 1:** eksport z ERP → zestawienie miesięczne (Plik 1),
- **Proces 2:** zestawienie miesięczne → zestawienie roczne z prognozą dla
  banku (Plik 2).

Szkolenie: „Wykorzystanie systemu AI Claude we współpracy z Excel,
PowerPoint oraz automatyzacja zadań" (PNT Opole, prowadzący Kasper Kalfas).
Agenda: `../../agenda/Agenda_szkolenia.md`.

## Czym jest Claude Code i czym różni się od czatu

Czat Claude (Dzień 1) rozmawia w przeglądarce i nie dotyka komputera.
**Claude Code** działa w terminalu, **w konkretnym folderze**: czyta
pliki, tworzy nowe, zmienia istniejące, uruchamia skrypty – za każdym
razem pytając o zgodę. Nie pisze się w nim kodu; mówi się po polsku, co ma
zrobić. Kod (krótkie skrypty w Pythonie) pisze i uruchamia sam.

## ⚠️ Zasady bezpieczeństwa

1. **Tylko dane fikcyjne.** Wszystko w `claude-code-cli/materialy/` jest wymyślone.
   Do folderu roboczego nie kopiujemy prawdziwych zestawień, eksportów
   ani nazwisk. To wymóg umowy szkoleniowej (zasada z Dnia 1, Blok B).
2. **Tylko folder roboczy.** Claude Code uruchamiamy wyłącznie w
   `C:\Szkolenie\dzien-1\praca\` – nigdy w `C:\`, `Dokumentach` ani w
   folderach zsynchronizowanych z OneDrive/SharePoint Urzędu.
3. **Kopia przed zmianą.** Każda modyfikacja pliku – najpierw kopia do
   `kopie/` (od zadania 4 to nawyk, w zadaniu 10 – zapisana zasada).
4. **Plan przed zmianą.** „Pokaż, co zamierzasz, i poczekaj na zgodę."
   Zgody typu „Yes, don't ask again" na szkoleniu nie używamy.
5. **Liczby weryfikujemy w Excelu.** Claude Code liczy skryptem, więc
   jest dokładniejszy niż czat – ale to Wy odpowiadacie za zestawienie.

Przeniesienie czegokolwiek z Dnia 1 na prawdziwe pliki wymaga pisemnej
zgody Urzędu/PNT na pracę z danymi w Claude oraz ustaleń z IT.

## Wymagania techniczne (przed Dniem 1)

| Co | Po co | Skąd |
|---|---|---|
| Windows 10/11 + PowerShell | terminal | wbudowane |
| Claude Code | `irm https://claude.ai/install.ps1 \| iex` | zadanie 1 |
| Konto Claude w organizacji Urzędu (plan Team) | logowanie `/login` | IT Urzędu |
| Git for Windows | Claude Code korzysta z Git Bash | [git-scm.com](https://git-scm.com/download/win) |
| Python 3 + `pip install openpyxl pandas` | czytanie/zapis Excela i CSV | [python.org](https://www.python.org/downloads/) („Add Python to PATH") |
| Excel | weryfikacja wyników | Urząd |
| Kopia `claude-code-cli/materialy/` na pendrive | świeże pliki po każdym ćwiczeniu | prowadzący |

Bez Pythona z openpyxl zadania 3–10 nie zadziałają – to najczęstsza
przyczyna problemów, warto sprawdzić dzień wcześniej (`python --version`,
`python -c "import openpyxl"`).

## Spis zadań

| # | Zadanie | Poziom | Czas | Część |
|---|---|---|---|---|
| 1 | [Instalacja i pierwsze uruchomienie](01-instalacja-i-pierwsze-uruchomienie.md) | podstawowy | 20 min | Dzień 1, cz. 1 |
| 2 | [Nawigacja po folderach](02-nawigacja-po-folderach.md) | podstawowy | 20 min | Dzień 1, cz. 1 |
| 3 | [„Otwórz ten Excel i powiedz, co w nim jest"](03-co-jest-w-tym-excelu.md) | podstawowy | 20 min | Dzień 1, cz. 1 |
| 4 | [Błędy na poziomie komórek – znajdź i napraw](04-bledy-na-poziomie-komorek.md) | podst. → średni | 30 min | Dzień 1, cz. 2 |
| 5 | [Operacje na komórkach w języku naturalnym](05-operacje-na-komorkach.md) | średni | 30 min | Dzień 1, cz. 2 |
| 6 | [Proces 1: z eksportu ERP do zestawienia miesięcznego](06-proces-1-erp-do-miesiecznego.md) | średni | 30 min | Dzień 1, cz. 3 |
| 7 | [Proces 2: powtarzalny przepis z miesięcznego do rocznego](07-proces-2-przepis-miesieczny-do-rocznego.md) | średni → zaaw. | 40 min | Dzień 1, cz. 3 |
| 8 | [Kolejny miesiąc od początku do końca + raport kontrolny](08-kolejny-miesiac-i-kontrola.md) | zaawansowany | 30 min | Dzień 1, cz. 3/4 |
| 9 | [Gdy Claude Code się myli – obsługa błędów](09-gdy-claude-code-sie-myli.md) | średni (dla wszystkich) | 30 min | Dzień 1, cz. 4 |
| 10 | [CLAUDE.md z zasadami i własna komenda „zamknij miesiąc"](10-claude-md-i-wlasna-komenda.md) | zaawansowany | 40 min | Dzień 1, cz. 4 |

**Zależności:** 6 → 7 → 8 → 10 budują na sobie (przepis, skrypt, raport,
komenda). Zadanie 9 można zrobić w dowolnym momencie po 4.

### Mapowanie na agendę

Dzień 1, cztery części po ok. 60 min (po pierwszym kontakcie z zestawu
[`../claude-code/`](../claude-code/README.md)):

| Część | Czas | Zadania |
|---|---|---|
| Pierwszy kontakt | 60 min | zestaw `../claude-code/` (zad. 6–16 tamtego folderu); stąd ewentualnie 3 jako demo „Excel od środka" |
| 1 — Wprowadzenie (instalacja, nawigacja, czytanie Excela) | 60 min | 1–3 **samodzielnie** na laptopach uczestników |
| 2 — Praca na komórkach | 60 min | 4, 5 |
| 3 — Automatyzacja powtarzalnego procesu | 60 min | 6, 7 (8 jeśli czas pozwoli) |
| 4 — Obsługa błędów i utrwalenie | 60 min | 9, 10 (10 częściowo jako praca własna) |

Łączny czas zadań (~290 min) przekracza 4×60 min – to celowe: zadania 8
i 10 są na wypadek szybszej grupy albo do dokończenia samodzielnie, a
wcześniejszy pierwszy kontakt „kupuje" czas w części 1.

## Pliki wsadowe (`materialy/`)

Generowane skryptem `generuj_dane.py` – uruchomienie nadpisuje wszystkie
pliki czystą wersją (przydatne po każdej grupie / po nieudanym ćwiczeniu).

| Plik | Co udaje | Zawartość | Zadania |
|---|---|---|---|
| `01_sandbox/` | zabałaganiony folder „Zestawienia" | 17 plików: 2025/2026, duplikaty, 3 wersje notatki, TODO, eksport | 2 |
| `eksport_erp_2026-09.csv` | brudny eksport z ERP | 25 wierszy; 2 formaty dat, 4 formaty kwot, duplikat `FV/2026/09/0142`, brak paragrafu w `FV/2026/09/0210`, spacje w nazwach | 3, 6, 9 |
| `eksport_erp_2026-10.csv` | czysty eksport z ERP | 24 wiersze, bez pułapek | 8, 10 |
| `zestawienie_miesieczne_SZABLON.xlsx` | Plik 1 (miesięczne), z planem, bez wykonania | 8 działów (wiersze 6–13), kolumny: plan, wykonanie w miesiącu, narastająco, % planu; Razem w 14 | 3, 5, 6, 7 |
| `zestawienie_roczne_2026.xlsx` | Plik 2 (roczne) | arkusz `Wykonanie`: 8 działów × 12 miesięcy (I–VIII wypełnione), plan, Razem, % planu; arkusz `Prognoza` dla banku (`B2` = liczba miesięcy) | 3, 5, 7, 8, 9, 10 |
| `zestawienie_bledy.xlsx` | Plik 1 za sierpień z błędami | 8 celowych błędów (klucz niżej) | 4 |

Układ obu plików Excel jest identyczny w kolumnie A (kody działów w
wierszach 6–13) – dzięki temu „dopasowanie po kodzie działu" ma sens, a
błąd „przesunięcia o wiersz" jest wykrywalny.

> **Przed skopiowaniem na pendrive: otwórz każdy `.xlsx` w Excelu i zapisz
> (Ctrl+S).** Generator zapisuje formuły bez policzonych wartości – bez
> tego kroku Claude Code widzi w `D14`, `Razem` czy `F13` (`#DIV/0!`)
> puste komórki i musi liczyć sam (radzi sobie, ale uczestnicy zobaczą
> uwagę „plik nie ma zapisanych wyników formuł"). Excel przy zapisie
> uzupełnia wartości.

## Klucz odpowiedzi

**Sumy wg działów (Proces 1):**

| Dział | wrzesień (bez duplikatu) | październik |
|---|---|---|
| 600 Transport i łączność | 2 150 000 | 1 980 000 |
| 750 Administracja publiczna | 1 480 000 | 1 510 000 |
| 801 Oświata i wychowanie | 5 210 000 | 5 340 000 |
| 851 Ochrona zdrowia | 265 000 | 240 000 |
| 852 Pomoc społeczna | 1 720 000 | 1 690 000 |
| 900 Gospodarka komunalna | 1 340 000 | 1 415 000 |
| 921 Kultura | 610 000 | 585 000 |
| 926 Kultura fizyczna | 455 000 | 480 000 |
| **Razem** | **13 230 000** | **13 240 000** |

Suma września **z duplikatem** = 14 470 000 (różnica 1 240 000 = kwota
`FV/2026/09/0142`).

**Wykonanie narastająco I–VIII (plik roczny):** 600: 15 207 000 · 750:
12 435 000 · 801: 40 124 000 · 851: 2 166 000 · 852: 13 583 000 · 900:
10 170 000 · 921: 4 791 000 · 926: 3 508 000. Po wrześniu dział 600 =
17 357 000 (72,3% planu); po październiku dział 801 = 50 674 000 (81,7%).

**8 błędów w `zestawienie_bledy.xlsx` (zadanie 4):**

1. Brak nagłówka w `F5` („% wykonania planu").
2. Pusty wiersz 9 w środku danych.
3. `D7` – kwota jako tekst (`1 548 000,00 zł`), przez co `SUM` w `D15` ją
   pomija.
4. Scalone `B10:B11` – dział 852 bez nazwy.
5. `C13` – brak planu działu 921 → `F13` zwraca `#DIV/0!`.
6. Kolumna `E` ukryta.
7. Niespójne daty: `A17` „05.09.2026" vs `A18` „2026-09-08".
8. (wynikowy) `D15`/`C15` – sumy błędne: D15 pomija tekst z D7 (błąd 3),
   C15 nie zawiera planu działu 921 (błąd 5).

Pełny klucz wypisuje też `python generuj_dane.py`.

## Jak korzystać z tych plików

Każdy plik `.md` ma tę samą strukturę: cel, poziom, czas, blok, materiały,
kroki, „Na co zwrócić uwagę", „Notatki własne". Każde polecenie do Claude
Code jest w ramce – do skopiowania 1:1 – a po kluczowych krokach jest
**Sprawdź:** z wartością z klucza odpowiedzi. Zachęcamy, żeby polecenia
zmieniać: to najlepszy sposób, żeby zobaczyć, jak precyzja polecenia
wpływa na wynik.
