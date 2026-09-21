# Zadanie 11: Wtyczka dla zespołu – pobierz, przekaż, wgraj, popraw

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**praca własna po szkoleniu, w parach**; kontynuacja
[zadania 10](10-wlasna-wtyczka-wydzialu.md)).

**Cel:** zamienić wtyczkę z zadania 10 z „mojej" w „naszą": przekazać ją
drugiej osobie jako plik, sprawdzić, że oboje dostajecie te same liczby,
zmienić jedną regułę i ustalić, kto jest właścicielem wersji.
**Poziom:** średniozaawansowany (praktyka w Cowork, 2 osoby)
**Czas:** ok. 25 minut
**Wymaga:** dwa konta Cowork w planie Team Urzędu; wtyczka
`wydzial-finansowy` z zadania 10 na jednym z nich; folder
`Pulpit\wtyczka-wydzialu\` z plikiem
`zestawienie_miesieczne_PODSUMOWANIE.xlsx` na obu komputerach.

## Role

- **Osoba A** – ma wtyczkę z zadania 10.
- **Osoba B** – nie ma jej. Wgra, przetestuje i poprawi.

## Co powstanie

1. wtyczka `wydzial-finansowy` na **obu** kontach,
2. dwa wyniki `/analiza-odchylen` z tego samego pliku – do porównania,
3. wersja 1.1 wtyczki z progiem 5% zamiast 10%, z zapisanym właścicielem.

## Po co to robić

Wtyczka na jednym laptopie to prywatne usprawnienie. Proces 1 i 2 robi
zespół – jeśli każdy opisze „analizę odchyleń" po swojemu, dostaniecie pięć
różnych analiz z tych samych liczb. Wtyczka jako **plik** działa jak
wspólny szablon Excela: jedna definicja, wiele osób, jedna wersja do
poprawiania.

## Co jest w pliku `.plugin`

`wydzial-finansowy.plugin` to spakowany folder ze zwykłymi plikami
tekstowymi (dokładne nazwy podfolderów zależą od wersji Cowork):

| Element | Co zawiera | Kto to zmienia |
|---|---|---|
| metadane | nazwa, opis, **autor** (z konta), wersja | autor przy każdej zmianie |
| `skills/zasady-wydzialu/SKILL.md` | zasady wspólne: format kwot, kopia przed zmianą, ton | zespół, rzadko |
| `commands/analiza-odchylen.md` | kroki komendy 1, w tym próg % | właściciel procesu |
| `commands/zestawienie-dla-banku.md` | kroki komendy 2 | właściciel procesu |
| `agents/`, `hooks/`, konektory | u Was puste – celowo | IT, jeśli kiedykolwiek |

Skoro to tekst, można go przeczytać w Notatniku **przed wgraniem** – tak
jak skill z internetu w zadaniu 9 – i trzymać na wspólnym dysku Wydziału
jako „wersję obowiązującą".

## Kroki

### Krok 1 (A): pobierz wtyczkę – 3 min

**Zrób:** Cowork → **Customize → Plugins → wydzial-finansowy → Download**.
Plik `wydzial-finansowy.plugin` przekażcie B (dysk wspólny, pendrive).

**Sprawdź:** w **Customize → Plugins → wydzial-finansowy → Commands** widać
obie komendy. Pokażcie B treść `analiza-odchylen`.

### Krok 2 (B): przeczytaj i wgraj – 4 min

**Zrób:** najpierw przeczytajcie `SKILL.md` i obie komendy (checklist
z zadania 9 – obowiązuje nawet dla wtyczki od kolegi z pokoju). Dopiero
potem **Customize → Plugins → „+" → Upload plugin** → wskażcie `.plugin`.

**Sprawdź:**

- [ ] wtyczka jest na liście B
- [ ] autor = A
- [ ] dwie komendy, jeden skill, zero konektorów

### Krok 3 (A i B): ten sam test – 6 min

**Zrób:** każdy na swoim koncie, w swoim folderze: `/analiza-odchylen` →
`zestawienie_miesieczne_PODSUMOWANIE.xlsx`. Połóżcie wyniki obok siebie.

**Sprawdź:**

- [ ] liczba wydziałów powyżej 10%: u obu **7** (klucz)
- [ ] kolejność top 5: **taka sama**
- [ ] komentarze: mogą różnić się słowami. Jeśli różnią się **treścią**
      (inny wniosek), komenda jest za mało precyzyjna – zapiszcie, jakie
      zdanie trzeba do niej dodać

### Krok 4 (B): zmień regułę – 5 min

Scenariusz: Skarbnik chce widzieć odchylenia już od 5%.

**Zrób:** **Customize → Plugins → wydzial-finansowy → Commands →
analiza-odchylen → Edit**. Zmieńcie `10%` na `5%` i dopiszcie krok:
*„Osobno wypisz działy między 5% a 10% jako 'do obserwacji'."* Zapiszcie
i uruchomcie komendę ponownie.

**Sprawdź:**

- [ ] u B w wyniku pojawiła się grupa „do obserwacji"
- [ ] u A **nic się nie zmieniło** – A nadal ma próg 10%. Wtyczka to plik,
      nie wspólny dokument online

### Krok 5 (B → A): przekaż poprawioną wersję – 5 min

**Zrób (B):** Download poprawionej wtyczki, przekażcie A.
**Zrób (A):** najpierw **usuńcie** starą wersję (Customize → Plugins →
wydzial-finansowy → usuń), dopiero potem **Upload plugin** z nowym plikiem.

**Sprawdź:**

- [ ] A ma **jedną** wtyczkę `wydzial-finansowy`, nie dwie (dwie o tej
      samej nazwie = nie wiadomo, która się uruchomiła)
- [ ] A uruchamia `/analiza-odchylen` – jest grupa „do obserwacji"
- [ ] w „Notatkach własnych" wpisaliście, **kto jest właścicielem wersji**:
      ta osoba jako jedyna edytuje i rozsyła, reszta tylko wgrywa

### Krok 6 (A i B): posprzątaj – 2 min

**Zrób:** wtyczki, których nie używacie na co dzień, wyłączcie
(**Customize → Plugins → przełącznik**). Każda włączona wtyczka zajmuje
miejsce w oknie kontekstu każdej rozmowy (zadanie 6). Plik `.plugin`
zostaje na dysku – włączenie to jedno kliknięcie.

## Wtyczka czy skill? Krótka reguła

Cowork ma dwa wbudowane narzędzia: **tworzenie wtyczek** (zadanie 10)
i **tworzenie skilli** (Blok C, zadanie 7). Łatwo je pomylić:

| Chcecie… | Wystarczy skill | Potrzebna wtyczka |
|---|---|---|
| żeby Claude pisał notatki w stylu Wydziału | ✔ | |
| jedną powtarzalną komendę `/` na cały proces | | ✔ |
| kilka komend ze wspólnymi zasadami | | ✔ |
| przekazać zespołowi „jak my to robimy" w jednym pliku | | ✔ |
| podpiąć konektor (za zgodą) do konkretnego procesu | | ✔ |

Wtyczka = skille + komendy (+ konektory + subagenci). **Nie macie komendy –
nie macie wtyczki, macie skill.**

## Co zapamiętać

- **Wtyczka to plik, więc podlega zasadom jak dokument.** Wersja, autor,
  miejsce przechowywania, kto zatwierdza zmiany. Bez tego po miesiącu
  każdy ma inny próg.
- **Autor ≠ właściciel procesu.** W metadanych zostaje ten, kto kliknął
  *Save*. Właściciela ustalacie Wy i wpisujecie w opis wtyczki
  („Wersja 1.1, właściciel: …, zmiana: próg 5%").
- **Te same liczby, różne słowa.** Model liczy powtarzalnie, jeśli liczy
  formułami; komentarze pisze za każdym razem trochę inaczej. Co ma być
  identyczne u wszystkich – zapiszcie jako regułę w skillu.
- **Czytanie przed wgraniem obowiązuje zawsze.** Nie dlatego, że kolega
  jest podejrzany, tylko dlatego, że nawyk działa, gdy nie ma wyjątków.
  Wtyczka z konektorami albo skryptami idzie do IT.
- **Dane bez zmian.** Ćwiczenie w parach = dwa razy dane fikcyjne.
  Prawdziwe zestawienie na czyimkolwiek koncie – tylko za pisemną zgodą
  Zamawiającego (Blok B).
- **W Dniu 2 to samo w Claude Code.** `CLAUDE.md` + folder
  `.claude/commands/` robią to, co plik `.plugin` – i mają Git do
  wersjonowania. Zobaczycie oba podejścia i wybierzecie swoje.

## Notatki własne

- Czy wyniki `/analiza-odchylen` u A i B były identyczne w liczbach?
  A w komentarzach?
- Kto jest właścicielem wersji wtyczki `wydzial-finansowy` i gdzie leży
  plik „obowiązujący"?
- Co z Waszej pracy jest skillem (styl, zasady), a co wtyczką (proces
  z komendą)?
