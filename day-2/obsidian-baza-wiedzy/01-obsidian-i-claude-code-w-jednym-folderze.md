# Zadanie 1: Obsidian i Claude Code w jednym folderze – vault Wydziału, struktura, pierwsza notatka

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
**Dzień 2, Blok D: Ćwiczenia własne** lub praca własna; ścieżka
„Baza wiedzy Wydziału").

**Cel:** zrozumieć, że **vault Obsidiana to zwykły folder z plikami
`.md`** – czyli dokładnie to, na czym pracuje Claude Code. Założyć vault
`baza-wydzial-finansowy`, nadać mu strukturę, wgrać zasady dla Claude
(`CLAUDE.md`) i zobaczyć, jak notatka napisana przez Claude Code w
terminalu pojawia się w Obsidianie w tej samej sekundzie.
**Poziom:** podstawowy
**Czas:** ok. 15 minut
**Wymaga:** Claude Code (Dzień 1/2, ścieżka
[`../../day-1/claude-code-cli/`](../../day-1/claude-code-cli/README.md)),
Obsidian (bezpłatny, [obsidian.md](https://obsidian.md) – instalacja bez
uprawnień administratora), folder `materialy/` z tej ścieżki.

## Problem, który to rozwiązuje

Wiedza Wydziału o tym, **jak** się zamyka miesiąc, skąd biorą się dane
działu 851 i dlaczego plik roczny nazywa się tak, a nie inaczej, jest w
trzech miejscach: w głowie Skarbnika, w mailu sprzed ośmiu miesięcy i w
instrukcji z 2019 r., która jest w połowie nieaktualna. Nowa osoba pyta;
w czasie urlopu nikt nie wie. Baza wiedzy to folder notatek, które
**linkują do siebie** i które da się przeszukać – a Claude Code potrafi
te notatki pisać, porządkować i odpowiadać na pytania z nich.

## Materiały

- `materialy/zrodla/` – cztery fikcyjne „źródła" Wydziału: instrukcja
  z 2019 r., mail Skarbnika z terminami (2026), notatka ze spotkania
  (2026-09-10), słownik działów (CSV).
- `materialy/szablony/` – trzy szablony notatek: procedura, pojęcie,
  decyzja.
- `materialy/CLAUDE_vault.md` – zasady dla Claude Code w vaultcie.

## Kroki

1. **Zainstalujcie Obsidian** i przy pierwszym uruchomieniu wybierzcie
   *Create new vault* → nazwa `baza-wydzial-finansowy`, lokalizacja
   `C:\Szkolenie\dzien-2\` (**nie** OneDrive/dysk wspólny Urzędu –
   zasada z Dnia 1). Obsidian otworzy pusty vault. Otwórzcie ten sam
   folder w Eksploratorze: zobaczycie ukryty `.obsidian\` (ustawienia) i
   nic więcej. **Vault = folder.**
2. **Skopiujcie materiały** do vaulta: zawartość `materialy/zrodla/` do
   `80-Zrodla\`, `materialy/szablony/` do `90-Szablony\`,
   `materialy/CLAUDE_vault.md` jako `CLAUDE.md` w głównym folderze
   vaulta. Wróćcie do Obsidiana – pliki już są w panelu po lewej (Obsidian
   obserwuje folder). Otwórzcie `CLAUDE.md` i przeczytajcie 7 zasad – to
   umowa między Wami a Claude Code na resztę ścieżki.
3. **Claude Code w vaultcie.** PowerShell: `cd C:\Szkolenie\dzien-2\baza-wydzial-finansowy`,
   `claude`. Pierwsze polecenie: *„Co jest w tym folderze i jakie zasady
   obowiązują?"* Claude powinien streścić `CLAUDE.md` (w tym: dane
   fikcyjne, nie edytować `80-Zrodla`, linki `[[ ]]`) i wymienić cztery
   źródła. Jeśli nie wspomina o zasadach – nie przeczytał `CLAUDE.md`;
   sprawdźcie, czy plik jest w głównym folderze, nie w podfolderze.
4. **Struktura.** *„Utwórz foldery ze struktury opisanej w CLAUDE.md
   (00-Start, 10-Procedury, 20-Slownik, 30-Decyzje) i w 00-Start notatkę
   `Start.md`: co to za baza, dla kogo, jak dodawać notatki, z linkami do
   każdego folderu."* Zatwierdźcie plan. Przełączcie się do Obsidiana:
   foldery i `Start.md` są; kliknijcie link `[[10-Procedury]]` – Obsidian
   otworzy folder albo zaproponuje utworzenie notatki. Widać podstawową
   rzecz: **Claude pisze pliki, Obsidian je pokazuje** – żadnej
   integracji nie trzeba instalować.
5. **Pierwsza notatka ze źródła.** *„Na podstawie
   `80-Zrodla/slownik_dzialow.csv` utwórz w `20-Slownik/` jedną notatkę
   `Dział 851 – Ochrona zdrowia.md` według szablonu `90-Szablony/pojecie.md`.
   W `zrodla:` wpisz plik CSV."* Otwórzcie ją w Obsidianie: frontmatter
   (Obsidian pokazuje go jako *Properties* u góry), definicja, „W naszych
   plikach", uwagi o źródle danych (mail z Wydziału Zdrowia, nie ERP).
   Klucz: notatka ma **jedno źródło** w `zrodla:` i **co najmniej jeden
   link** `[[ ]]` (np. do `[[Eksport ERP]]` albo `[[Wydział Zdrowia]]`),
   który jeszcze nie istnieje – w Obsidianie taki link jest wyszarzony.
   To nie błąd, to lista rzeczy do opisania (zasada 5).
6. **Test dwóch okien.** Zostawcie Obsidian otwarty na tej notatce i w
   Claude Code: *„Dopisz do notatki o dziale 851 sekcję »Terminy« na
   podstawie maila Skarbnika."* Claude pokaże zmianę i poczeka na zgodę
   (zasada 7). Po zgodzie notatka w Obsidianie **odświeży się sama**.
   Zapiszcie sobie: Obsidian nie musi być zamknięty, Claude nie musi być
   „w Obsidianie".

## Na co zwrócić uwagę

- **Vault to folder, notatka to plik tekstowy.** Można go skopiować na
  pendrive, otworzyć Notatnikiem, wysłać jako ZIP, dać do przeczytania
  Claude Code. Nie ma bazy danych, nie ma formatu zamkniętego – za 10
  lat te pliki nadal się otworzą. To argument dla IT i dla Was.
- **`CLAUDE.md` w vaultcie robi to samo, co w folderze z Excelem**
  (zadanie 10 ścieżki Claude Code): zasady czytane na starcie każdej
  sesji. Najważniejsze dwie: „każdy fakt ze źródła" i „`80-Zrodla` tylko
  do czytania" – bez nich baza wiedzy zamienia się w zbiór ładnych
  zmyśleń.
- **Frontmatter to metadane, nie ozdoba.** `typ`, `zrodla`,
  `ostatni_przeglad` pozwalają w zadaniu 4 zapytać „które procedury nie
  były przeglądane od pół roku" – bez tego trzeba czytać wszystko.
- **Linki do nieistniejących notatek są celowe.** Obsidian pokazuje je na
  szaro; w widoku grafu (ikona po lewej) widać, które pojęcia się
  powtarzają, a nie mają jeszcze notatki – to naturalna kolejka pracy.
- **Nie synchronizujcie vaulta z dyskiem Urzędu na szkoleniu.** Na
  szkoleniu dane są fikcyjne; ale nawyk „Claude Code tylko w folderze
  lokalnym" ma zostać. Docelowe miejsce bazy (dysk wspólny, SharePoint,
  Git) to decyzja z IT – zadanie 4.
- **Obsidian ma setki wtyczek – nie potrzebujecie żadnej.** Wszystko w
  tej ścieżce działa na czystym Obsidianie; wtyczki (kalendarz, tabele
  z frontmattera, Git) można rozważyć później, po ustaleniu z IT.

## Notatki własne

- Czy Claude w kroku 3 sam wymienił zasady z `CLAUDE.md`?
- Które linki `[[ ]]` w notatce o dziale 851 są wyszarzone – i czy to
  właściwa kolejka do opisania?
- Gdzie dziś jest „instrukcja zamknięcia miesiąca" Waszego Wydziału – w
  jakim pliku, z jakiego roku?
