# Zadanie 4: Utrzymanie bazy – własne komendy, przegląd, wersje w Git i co do bazy nie wchodzi

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
**Dzień 2, Blok D** lub praca własna; kontynuacja
[zadania 3](03-pytania-do-bazy-i-dziennik-decyzji.md)).

**Cel:** sprawić, żeby baza **nie umarła po szkoleniu**: dwie własne
komendy Claude Code (`/nowa-decyzja` – dopisywanie w 30 sekund,
`/przeglad-bazy` – co jest przeterminowane, zerwane, osierocone),
zasada „tylko z bazy" na stałe w `CLAUDE.md`, wersjonowanie vaulta w Git
(cofnięcie zmiany, historia „kto co kiedy"), eksport dla osób bez
Obsidiana – i lista tego, czego do bazy **nie wolno** wpisać.
**Poziom:** średni
**Czas:** ok. 20 minut
**Wymaga:** vault po zadaniu 3; Git for Windows (jest – Claude Code go
wymaga, zadanie 1 ścieżki Claude Code).

## Problem, który to rozwiązuje

Każdy Wydział ma za sobą co najmniej jedną bazę wiedzy, która umarła:
wiki, folder „Procedury", zeszyt. Umierają z trzech powodów: dopisanie
czegoś jest za drogie, nikt nie wie, co jest nieaktualne, i nie da się
sprawdzić, kto co zmienił. Trzy komendy poniżej odpowiadają dokładnie na
te trzy powody – a Git dodaje to, czego dysk wspólny nie ma: **różnicę**
między wersjami, nie tylko datę.

## Materiały

- Vault po zadaniu 3 (procedura, 8 działów, pojęcia, 3 decyzje, sprawy
  otwarte).
- Mechanizm własnych komend: `.claude/commands/nazwa.md` → `/nazwa`
  (zadanie 10 ścieżki Claude Code; `$ARGUMENTS` = tekst po nazwie).

## Kroki

1. **Zasada „tylko z bazy" na stałe.** *„Dopisz do CLAUDE.md sekcję
   »Odpowiadanie na pytania«: odpowiadaj tylko na podstawie notatek,
   do każdego faktu podawaj ścieżkę, gdy czegoś nie ma – napisz »nie ma
   w bazie«; źródła w 80-Zrodla traktuj jako materiał do przepisania,
   nie jako notatki."* Wpiszcie `/clear` (nowa sesja, Dzień 1) i
   zadajcie pytanie 5 z zadania 3 (prezentacja dla Rady). Klucz: „nie
   ma w bazie" **bez** powtarzania zasady w rozmowie.
2. **Komenda `/nowa-decyzja`.** *„Utwórz komendę `/nowa-decyzja`: z
   tekstu w `$ARGUMENTS` (jedno-dwa zdania: co, kto, od kiedy) tworzy
   notatkę w 30-Decyzje według szablonu decyzji, z dzisiejszą datą w
   nazwie i frontmatterze, linkuje działy/procedury, których dotyczy, i
   pyta o źródło (mail? spotkanie?), jeśli nie podano. Pokaż plik
   komendy przed zapisaniem."* Test: `/nowa-decyzja od października
   dane działu 851 przychodzą przez formularz, nie mailem – ustalone ze
   Skarbnikiem 2026-09-20`. Klucz: nowa notatka z `data: 2026-09-20`,
   linkiem do `[[Dział 851 – Ochrona zdrowia]]`, pytaniem o źródło (lub
   `zrodla: [ustne – do potwierdzenia]`) **i** pytaniem, czy zmienić
   procedurę (krok „mail z Wydziału Zdrowia" przestaje być aktualny).
   Nie zmieniajcie procedury – to fikcyjna decyzja testowa; **usuńcie**
   tę notatkę po teście albo zostawcie ze `status: test`.
3. **Komenda `/przeglad-bazy`.** *„Utwórz komendę `/przeglad-bazy`, która
   raportuje (bez zmian w plikach): (a) procedury z `ostatni_przeglad`
   starszym niż 6 miesięcy lub pustym, (b) decyzje ze `status:
   obowiazuje` i terminem w treści, który już minął, (c) linki do
   nieistniejących notatek z liczbą wystąpień, (d) notatki, do których
   nic nie linkuje (sieroty), (e) notatki bez `zrodla`. Wynik jako
   tabela, posortowany od najpilniejszego."* Uruchomcie. Klucz (stan po
   zadaniu 3): (a) procedura ma pusty `ostatni_przeglad` – do
   uzupełnienia; (b) nic jeszcze nie minęło (terminy 2026-10-15 i
   2026-11-30; jeśli robicie to ćwiczenie później – pojawią się);
   (c) kilka szarych linków (`Skarbnik`, `Wydział Zdrowia`, `Uchwała
   budżetowa`…); (d) `Start.md` i sprawy otwarte zwykle są sierotami;
   (e) `Start.md`. Uzupełnijcie jedno: *„Wpisz w procedurze
   `ostatni_przeglad: 2026-09-23` i `wlasciciel: gł. specjalista ds.
   budżetu`."*
4. **Wersje w Git.** *„Zainicjuj repozytorium Git w tym folderze, dodaj
   `.gitignore` z `.obsidian/workspace*` (ustawienia okna, nie treść),
   i zrób pierwszy zapis wersji z opisem »Baza wiedzy – stan po
   szkoleniu 23.09.2026«."* Potem zmieńcie coś ręcznie w Obsidianie
   (np. w procedurze zamieńcie „7. dnia roboczego" na „8.") i
   zapytajcie: *„Co się zmieniło w vaultcie od ostatniego zapisu? Pokaż
   różnicę."* Klucz: Claude pokazuje **dokładną linię** przed/po
   (`git diff`). *„Cofnij tę zmianę."* – procedura wraca do 7. dnia.
   To jest różnica między Git a historią wersji dysku wspólnego:
   widzicie **co** się zmieniło, nie tylko **że**.
5. **Dla osób bez Obsidiana.** *„Wygeneruj `Procedura – Zamknięcie
   miesiąca.docx` z notatki procedury: linki `[[ ]]` zamień na zwykły
   tekst, listę kontrolną na pola do odhaczenia, w stopce datę
   przeglądu i ścieżkę notatki źródłowej."* Klucz: plik `.docx`
   otwiera się w Wordzie, ma stopkę ze ścieżką – żeby ktoś, kto go
   dostanie, wiedział, gdzie jest wersja obowiązująca. Zasada: **Word to
   eksport, Obsidian to źródło** – poprawki wprowadza się w notatce,
   nie w Wordzie.
6. **Czego do bazy nie wpisujemy.** Zapytajcie Claude: *„Na podstawie
   CLAUDE.md i notatki ze spotkania 10.09 (punkt o danych poufnych)
   zaproponuj notatkę `00-Start/Czego nie wpisujemy.md`."* Dobra
   propozycja zawiera co najmniej: nazwiska i dane osobowe (role zamiast
   osób), kwoty z roboczych zestawień przed publikacją, treść umów z
   bankiem, hasła i loginy do ERP, dane z realnych plików Urzędu bez
   pisemnej zgody. Dopiszcie własnym słowem: **kto** decyduje w
   wątpliwych przypadkach (Skarbnik) i **gdzie** zgłosić, jeśli coś
   takiego już trafiło do bazy.

## Na co zwrócić uwagę

- **Baza żyje, jeśli dopisanie kosztuje mniej niż minutę.**
  `/nowa-decyzja` po spotkaniu, z telefonu w notatniku, przepisane
  wieczorem – to realistyczny rytm. Bez komendy każda decyzja wymaga
  otwarcia szablonu i wymyślenia nazwy, i już nikt tego nie robi.
- **`/przeglad-bazy` raz w miesiącu, razem z zamknięciem miesiąca.**
  Procedura ma `ostatni_przeglad` po to, żeby przegląd był
  **pytaniem do maszyny**, nie do sumienia. Wynik to lista do
  15-minutowego spotkania, nie zadanie na tydzień.
- **Git to nie narzędzie programistów – to historia zmian z różnicą.**
  Na szkoleniu obsługuje go Claude Code („zapisz wersję", „co się
  zmieniło", „cofnij"); nikt nie musi znać komend. Docelowo: repozytorium
  na serwerze Urzędu (ustalenie z IT), a nie na koncie prywatnym.
  Obsidian ma też wtyczkę Git – opcja, nie wymóg.
- **Jedno źródło prawdy.** Eksport do Worda (krok 5) jest dla odbiorców,
  nie do edycji. Jeśli ktoś poprawi Worda, poprawka ginie przy
  następnym eksporcie – stopka ze ścieżką notatki jest po to, żeby
  wiedział, gdzie poprawiać.
- **Dane poufne w bazie to ryzyko podwójne.** Raz – bo baza jest
  czytana przez Claude Code (wysyłana do dostawcy). Dwa – bo baza jest
  po to, by ją udostępniać (nowa osoba, zastępstwo). Notatka „Czego nie
  wpisujemy" jest ważniejsza niż większość procedur; zasada z Dnia 1
  (Blok B) i umowa szkoleniowa obowiązują tu w całości.
- **Skrypty i komendy zostają, rozmowa znika.** `CLAUDE.md`,
  `.claude/commands/`, szablony i Git są w folderze – to ta sama lekcja,
  co w zadaniu 10 ścieżki Claude Code. Wszystko, co ma działać za
  miesiąc, jest w plikach.

## Notatki własne

- Czy po `/clear` zasada „tylko z bazy" z `CLAUDE.md` zadziałała bez
  przypominania?
- Co `/przeglad-bazy` pokazał jako najpilniejsze?
- Kto w Wydziale będzie właścicielem bazy – i kiedy jest pierwszy
  przegląd?
