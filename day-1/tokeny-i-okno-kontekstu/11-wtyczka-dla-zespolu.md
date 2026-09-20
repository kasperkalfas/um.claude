# Zadanie 11: Wtyczka dla zespołu – pobierz, przekaż, wgraj, popraw

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**praca własna po szkoleniu**, w parach; kontynuacja
[zadania 10](10-wlasna-wtyczka-wydzialu.md)).

**Cel:** zamienić wtyczkę z zadania 10 z „mojej" w „naszą": pobrać plik
`.plugin`, przekazać koledze/koleżance, wgrać na drugim koncie, zmienić
jedną regułę (próg odchylenia) i sprawdzić, że obie osoby dostają ten sam
wynik z tych samych danych. Przy okazji: kiedy budować wtyczkę, a kiedy
wystarczy skill.
**Poziom:** średniozaawansowany (praktyka w Cowork, 2 osoby)
**Czas:** ok. 25 minut
**Wymaga:** dwa konta Cowork w planie Team Urzędu; wtyczka
`wydzial-finansowy` z zadania 10 na jednym z nich; folder
`Pulpit\wtyczka-wydzialu` z plikami fikcyjnymi na obu komputerach.

## Problem, który to rozwiązuje

Wtyczka na jednym laptopie to prywatne usprawnienie. Proces 1 i 2 robi
zespół – i jeśli każdy opisze „analizę odchyleń" po swojemu, dostaniecie
pięć różnych analiz z tych samych liczb. Wtyczka jako **plik** rozwiązuje
to tak samo jak wspólny szablon Excela: jedna definicja, wiele osób,
jedna wersja do poprawiania.

## Co jest w pliku `.plugin`

Plik `wydzial-finansowy.plugin` to spakowany folder. W środku (układ
w przybliżeniu – dokładne nazwy podfolderów zależą od wersji Cowork):

| Element | Co zawiera | Kto to zmienia |
|---|---|---|
| **metadane** | nazwa, opis, **autor** (Wasze imię i nazwisko z konta), wersja | autor przy każdej zmianie |
| `skills/zasady-wydzialu/SKILL.md` | zasady wspólne (format kwot, kopia przed zmianą, ton) | zespół, rzadko |
| `commands/analiza-odchylen.md` | kroki komendy 1 (w tym próg %) | właściciel procesu |
| `commands/zestawienie-dla-banku.md` | kroki komendy 2 | właściciel procesu |
| `agents/`, `hooks/`, `connectors` | u Was puste – celowo | IT, jeśli kiedykolwiek |

To zwykłe pliki tekstowe – można je czytać i poprawiać w Notatniku, bez
Cowork. Dlatego wtyczkę da się **przejrzeć przed wgraniem** (tak jak
skill z internetu w zadaniu 9) i trzymać na wspólnym dysku Wydziału jako
„wersję obowiązującą".

## Materiały

- Osoba A: konto z wtyczką z zadania 10.
- Osoba B: konto **bez** tej wtyczki.
- Oboje: `Pulpit\wtyczka-wydzialu\zestawienie_miesieczne_PODSUMOWANIE.xlsx`.

## Kroki

1. **A – pobierz.** Cowork → **Customize → Plugins → wydzial-finansowy →
   Download**. Plik `wydzial-finansowy.plugin` ląduje w folderze
   pobranych / w folderze roboczym. Zawartość obejrzyjcie w Cowork
   (**Customize → Plugins → wydzial-finansowy → Commands / Skills**) i
   pokażcie B komendę `analiza-odchylen`.
2. **B – przejrzyj i wgraj.** Zanim B cokolwiek wgra: czyta
   `SKILL.md` i obie komendy (checklist z zadania 9 – nawet gdy autorem
   jest kolega z pokoju; nawyk ma być bezwarunkowy). Potem **Customize →
   Plugins → „+" → Upload plugin** → wskazuje `.plugin`. Po chwili
   wtyczka jest na liście B, z autorem = A.
3. **Ten sam test u obu.** A i B, każdy na swoim koncie, w swoim folderze:
   `/analiza-odchylen` → `zestawienie_miesieczne_PODSUMOWANIE.xlsx`.
   Porównajcie: liczba wydziałów oznaczonych powyżej 10% (klucz: 7),
   kolejność top 5, komentarze. Liczby powinny być identyczne; komentarze
   mogą się różnić słowami – jeśli różnią się **treścią**, komenda jest
   za mało precyzyjna (zapiszcie, które zdanie w niej dodać).
4. **B – popraw regułę.** Skarbnik chce widzieć odchylenia już od 5%.
   B: **Customize → Plugins → wydzial-finansowy → Commands →
   analiza-odchylen → Edit**, zmienia `10%` na `5%` i dopisuje krok:
   *„Osobno wypisz działy między 5% a 10% jako 'do obserwacji'."*
   Zapisuje. Uruchamia komendę ponownie – w wyniku pojawia się nowa
   grupa. **A nic nie widzi** – A ma nadal starą wersję.
5. **B → A – przekaż z powrotem.** B pobiera poprawioną wtyczkę
   (Download), A **najpierw usuwa** u siebie starą wersję (Customize →
   Plugins → wydzial-finansowy → usuń), potem wgrywa nową (**Upload
   plugin**) – dwie wtyczki o tej samej nazwie to prosta droga do
   pomyłki, która komenda się uruchomiła. Od teraz oboje mają próg 5%. Ustalcie w „Notatkach", **kto
   jest właścicielem wersji** – ta osoba jako jedyna edytuje i
   rozsyła; reszta tylko wgrywa.
6. **Sprzątanie.** Wtyczki, których nie używacie na co dzień, wyłączcie
   (**Customize → Plugins → przełącznik**) – zajmują okno kontekstu w
   każdej rozmowie (zadanie 6). Plik `.plugin` zostaje na dysku; włączenie
   to jedno kliknięcie.

## Wtyczka czy skill? Krótka reguła

Cowork ma dwa wbudowane narzędzia: **tworzenie wtyczek** (użyliście w
zadaniu 10) i **tworzenie skilli** (Blok C, zadanie 7). Łatwo je pomylić:

| Chcecie… | Wystarczy skill | Potrzebna wtyczka |
|---|---|---|
| żeby Claude pisał notatki w stylu Wydziału | ✔ | |
| jedną powtarzalną komendę `/` na cały proces | | ✔ |
| kilka komend, które dzielą wspólne zasady | | ✔ |
| przekazać zespołowi „jak my to robimy" w jednym pliku | | ✔ |
| podpiąć konektor (za zgodą) do konkretnego procesu | | ✔ |

Wtyczka = skille + komendy (+ konektory + subagenci). Jeśli nie macie
komendy – nie macie wtyczki, macie skill.

## Na co zwrócić uwagę

- **Wtyczka to plik, więc podlega zasadom jak dokument.** Wersja, autor,
  miejsce przechowywania, kto zatwierdza zmiany. Bez tego po miesiącu
  każdy ma inny próg i inną kolejność kroków.
- **Autor ≠ właściciel procesu.** W metadanych zostaje ten, kto kliknął
  *Save*. Właściciela ustalacie Wy – i najlepiej wpisujecie go w opisie
  wtyczki („Wersja 1.1, właściciel: …, zmiana: próg 5%").
- **Ta sama komenda, te same liczby, różne słowa.** Model nie jest
  deterministyczny w komentarzach – jest w arytmetyce, jeśli liczy
  formułami. Wszystko, co ma być identyczne u wszystkich, zapisujcie
  jako regułę w skillu, nie zostawiajcie „domyślności".
- **Czytanie przed wgraniem obowiązuje zawsze** – nawet dla wtyczki od
  kolegi. Nie dlatego, że kolega jest podejrzany, tylko dlatego, że
  nawyk działa wtedy, gdy nie ma wyjątków. Wtyczka z konektorami albo
  skryptami idzie do IT.
- **Dane bez zmian.** Ćwiczenie w parach = dwa razy dane fikcyjne.
  Prawdziwe zestawienie na czyimkolwiek koncie – tylko za pisemną zgodą
  Zamawiającego (Blok B).
- **W Dniu 2 to samo w Claude Code.** `CLAUDE.md` + folder
  `.claude/commands/` w repozytorium Wydziału robią dokładnie to, co plik
  `.plugin` – i mają Git do wersjonowania. Zobaczycie oba podejścia i
  wybierzecie, które pasuje do Waszego zespołu.

## Notatki własne

- Czy wyniki `/analiza-odchylen` u A i B były identyczne w liczbach?
  W komentarzach?
- Kto jest właścicielem wersji wtyczki `wydzial-finansowy` i gdzie leży
  plik „obowiązujący"?
- Co z Waszej pracy jest skillem (styl, zasady), a co wtyczką (proces z
  komendą)?
