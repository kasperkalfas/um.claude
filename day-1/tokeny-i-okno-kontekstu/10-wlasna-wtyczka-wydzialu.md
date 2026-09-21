# Zadanie 10: Własna wtyczka Wydziału – analiza odchyleń i zestawienie dla banku jedną komendą

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**praca własna po szkoleniu** albo demo prowadzącego; domknięcie zadań 6–9
i most do `/zamknij-miesiac` z Claude Code w Dniu 2).

**Cel:** opisać Cowork własny proces po polsku i dostać z tego wtyczkę
z dwiema komendami: `/analiza-odchylen` (plan vs wykonanie) i
`/zestawienie-dla-banku` (Proces 2). Potem uruchomić obie i zrobić z wyniku
prezentację.
**Poziom:** średniozaawansowany (praktyka w Cowork)
**Czas:** ok. 40 minut (opis i budowa wtyczki ~10, dwie komendy ~20,
prezentacja ~10)
**Wymaga:** Cowork, konto w planie Team Urzędu, dwa pliki fikcyjne (niżej).

## Co powstanie

Po 40 minutach macie na dysku:

1. wtyczkę `wydzial-finansowy` widoczną w Cowork (Customize → Plugins),
2. plik `..._odchylenia.xlsx` – wynik `/analiza-odchylen`,
3. uzupełnione zestawienie roczne z formułami w arkuszu `Prognoza` –
   wynik `/zestawienie-dla-banku`,
4. prezentację `.pptx` z obu analiz.

## Po co to robić

Gotowa wtyczka finansowa z katalogu (zadanie 6) zna „finanse w ogóle":
bilans, rachunek wyników, cash flow. Wy tego nie robicie. Robicie
**wykonanie budżetu wg działów, plan vs wykonanie, prognozę dla banku**.
Zamiast tłumaczyć to agentowi w każdej rozmowie, opisujecie raz – jako
wtyczkę. Od tej pory `/analiza-odchylen` znaczy dokładnie to, co u Was
znaczy „analiza odchyleń".

## Przygotowanie (3 minuty)

- [ ] Folder `Pulpit\wtyczka-wydzialu\` z **kopiami** dwóch plików:

| Plik | Skopiuj z | Do czego |
|---|---|---|
| `zestawienie_miesieczne_PODSUMOWANIE.xlsx` | `../materialy/` | 10 wydziałów, plan i wykonanie za październik → komenda 1 |
| `zestawienie_roczne_2026.xlsx` | `../claude-code-cli/materialy/` | arkusz `Wykonanie` (plan roczny, I–VIII) i pusty arkusz `Prognoza` → komenda 2 |

- [ ] Cowork → **Customize**: wyłączcie inne wtyczki finansowe i skill
      prognozowania z zadania 9, żeby się nie „wtrącały".
- [ ] Otwórzcie Notatnik – za chwilę wkleicie tam szablon opisu.

## Krok 1: Opisz swój proces (5 min)

Skopiujcie szablon poniżej do Notatnika i **uzupełnijcie pola w nawiasach
kwadratowych** `[...]`. Zasada:

- co **wpiszecie** – agent przyjmie bez pytania,
- co **zostawicie w nawiasie** – agent o to dopyta.

Pola do uzupełnienia: Wasza rola, odbiorcy raportów, próg odchylenia w %
(proponujemy 10), odbiorca zestawienia (bank).

```
Zbuduj dla mnie własną wtyczkę Cowork dopasowaną do moich obowiązków.
Nazwa wtyczki: wydzial-finansowy.

MÓJ PROFIL
- Rola: [Skarbnik / główny księgowy / inspektor ds. budżetu]
- Organizacja: urząd miejski (samorząd), Polska
- Rok budżetowy: kalendarzowy (styczeń–grudzień)
- Kwoty: PLN, separator tysięcy, bez groszy; procenty z 1 miejscem
- Narzędzie pracy: Excel; wynik zawsze jako plik .xlsx
- Odbiorcy raportów: [Skarbnik / Rada Miasta / bank / mieszkańcy]

MOJE DANE
- Wydatki grupujemy wg działów klasyfikacji budżetowej: 600 Transport
  i łączność, 750 Administracja publiczna, 801 Oświata i wychowanie,
  851 Ochrona zdrowia, 852 Pomoc społeczna, 900 Gospodarka komunalna
  i ochrona środowiska, 921 Kultura i ochrona dziedzictwa narodowego,
  926 Kultura fizyczna.
- Zestawienie miesięczne: kolumny Dział | Kwota planowana |
  Kwota wykonana | Miesiąc.
- Zestawienie roczne: arkusz "Wykonanie" (Dział, Nazwa działu, Plan
  roczny, miesiące I–XII, Razem, % planu) i arkusz "Prognoza" (Plan
  roczny, Wykonanie narastająco, Średnia miesięczna, Prognoza roczna,
  Odchylenie od planu).

KOMENDA 1: /analiza-odchylen
Cel: porównać wykonanie z planem w zestawieniu miesięcznym.
1. Wczytaj wskazany plik miesięczny. Puste wiersze, niespójne formaty
   miesiąca, scalone komórki – zgłoś, nie poprawiaj po cichu.
2. Policz odchylenie w PLN i w % dla każdego działu.
3. Oznacz działy z odchyleniem powyżej [10]% (na plus i na minus).
4. Wypisz 5 największych odchyleń z krótkim komentarzem. Nie zgaduj
   przyczyn – jeśli nie wynikają z danych, napisz "do wyjaśnienia
   z wydziałem".
5. Zapisz nowy plik <nazwa>_odchylenia.xlsx z arkuszami: Odchylenia,
   Top5, Dane_do_wykresu (wykres wodospadowy plan → wykonanie).
   Nigdy nie nadpisuj pliku źródłowego.

KOMENDA 2: /zestawienie-dla-banku
Cel: uzupełnić zestawienie roczne i prognozę (nasz "Proces 2").
1. Wczytaj zestawienie roczne i wskazany plik miesięczny. Dopasuj
   wiersze po KODZIE działu (kolumna A), nigdy po nazwie. Jeśli plik
   miesięczny nie ma kodów – zapytaj mnie o mapowanie, nie zgaduj.
2. Wpisz kwoty wykonane do właściwej kolumny miesiąca.
3. W arkuszu "Prognoza" wpisz FORMUŁY, nie liczby: wykonanie
   narastająco, średnia miesięczna, prognoza roczna = średnia × 12,
   odchylenie od planu.
4. Zaznacz działy, w których prognoza przekracza plan roczny.
5. Zapisz jako <nazwa>_<rok>_<miesiąc>.xlsx. Przelicz formuły
   i sprawdź, że nie ma błędów (#ARG!, #ADR!).
6. Napisz 5-punktowe podsumowanie po polsku dla odbiorcy: [bank].

SKILL: zasady-wydzialu (wspólne dla obu komend)
- Dane w ćwiczeniach są fikcyjne; nie proś o dane realne.
- Kopia przed każdą zmianą pliku (podfolder kopie/).
- Odchylenie = wykonanie − plan; dodatnie = przekroczenie planu.
- Formuły zamiast wpisanych wartości wszędzie, gdzie się da.
- Ton komentarzy: rzeczowy, urzędowy, bez ocen personalnych.

KONEKTORY MCP: żadnych. Pracujemy tylko na plikach w bieżącym folderze.

Przed zapisaniem pokaż mi pełną strukturę wtyczki (skille, komendy,
agenci, konektory) do przejrzenia.
```

## Krok 2: Zbuduj wtyczkę (5 min)

**Zrób:** Cowork → nowe zadanie → *Choose a different folder* →
`Pulpit\wtyczka-wydzialu` → **Allow**. Wklejcie uzupełniony szablon
i wyślijcie. Agent dopyta o pola, które zostały w nawiasach – odpowiadajcie
krótko. Potem sam sięgnie po wbudowany skill tworzenia wtyczek, zajrzy do
Waszych plików Excel i pokaże strukturę do przeglądu.

**Sprawdź, zanim klikniecie Save:**

- [ ] dokładnie **dwie komendy**: `/analiza-odchylen`, `/zestawienie-dla-banku`
- [ ] **jeden skill** `zasady-wydzialu`
- [ ] **zero konektorów**
- [ ] w podglądzie komendy 1 są **Wasze kroki** – jeśli agent dodał coś od
      siebie (np. bilans), każcie usunąć

**Zrób:** kliknijcie **Save**. Wtyczka pojawia się w **Customize → Plugins**
z dwiema komendami. Opcjonalnie **Download** – plik
`wydzial-finansowy.plugin` przyda się w zadaniu 11.

## Krok 3: Uruchom `/analiza-odchylen` (10 min)

**Zrób:** nowe zadanie w tym samym folderze → wpiszcie `/` → wybierzcie
`wydzial-finansowy` → `/analiza-odchylen`. Na pytanie o plik:
`zestawienie_miesieczne_PODSUMOWANIE.xlsx`. Patrzcie na podzadania po
prawej: wczytaj → policz → oznacz → top 5 → zapisz.

**Sprawdź:**

- [ ] oznaczonych na plus jest **7 wydziałów z 10** (klucz)
- [ ] otwórzcie `..._odchylenia.xlsx` i przeliczcie **jedno** odchylenie
      ręcznie (wykonanie − plan) – zgadza się?
- [ ] plik źródłowy **nie został zmieniony**

## Krok 4: Uruchom `/zestawienie-dla-banku` (10 min)

**Zrób:** `/zestawienie-dla-banku` → plik roczny
`zestawienie_roczne_2026.xlsx`, plik miesięczny z kroku 3 jako nowy miesiąc.

**Sprawdź:**

- [ ] plik miesięczny ma **nazwy** wydziałów, roczny ma **kody** działów –
      agent powinien **zapytać Was o mapowanie**. Jeśli zgadł sam, to
      błąd – zapiszcie w notatkach
- [ ] arkusz `Prognoza`, komórka „Prognoza roczna" – po kliknięciu widać
      **formułę**, nie liczbę
- [ ] brak `#ARG!` / `#ADR!` w całym arkuszu
- [ ] podsumowanie ma 5 punktów i jest napisane do banku, nie do Was

## Krok 5: Prezentacja (10 min)

**Zrób:** w tej samej rozmowie wklejcie:

> Podsumuj analizę odchyleń i zestawienie dla banku w prezentacji
> PowerPoint dla [odbiorca]. 7 slajdów: tytuł, streszczenie, plan vs
> wykonanie, top 5 odchyleń z wykresem wodospadowym, prognoza roczna,
> działy zagrożone przekroczeniem planu, następne kroki.

Skill PowerPoint zrobi projekt → plik → kontrolę wizualną → poprawki.

**Sprawdź** (jak w zadaniu 8):

- [ ] **min. 2 liczby** ze slajdów porównane z arkuszem
- [ ] liczba działów „zagrożonych" na slajdzie = liczba zaznaczonych
      w arkuszu `Prognoza`

## Co zapamiętać

- **Wtyczka to Wasz proces spisany po ludzku.** Nie pisaliście kodu.
  W Dniu 2 zrobicie to samo w Claude Code (`CLAUDE.md` + własna komenda)
  – tylko w innym opakowaniu.
- **Nawias = pytanie, wpis na sztywno = decyzja.** Wtyczka tylko dla Was?
  Wpiszcie wszystko. Dla zespołu? Zostawcie nawiasy tam, gdzie ludzie się
  różnią (rola, odbiorca).
- **„Nie poprawiaj po cichu" i „zapytaj o mapowanie" to celowe reguły.**
  Wtyczka, która sama zgaduje, że „Wydział Edukacji" = dział 801, jest
  wygodna – i niebezpieczna w zestawieniu dla banku.
- **Zero konektorów – świadomie.** Podpięcie ERP, poczty czy dysku Urzędu
  to decyzja IT i Zamawiającego (zadanie 5), nie linijka w opisie.
- **Koszt.** Budowa wtyczki jest tania, uruchomienie na plikach
  i prezentacja – nie (Settings → Usage). Testujcie na jednym pliku.
- **To wersja robocza.** Mapowanie, odchylenia i prognoza są do Waszej
  kontroli za każdym razem. Na realnych danych Urzędu – tylko za pisemną
  zgodą (Blok B) i po ocenie IT.

## Notatki własne

- Ile wydziałów oznaczyła komenda 1 jako przekraczające plan? (klucz: 7)
- Czy komenda 2 zapytała o mapowanie nazw na kody działów, czy zgadła?
- Jaka trzecia komenda w tej wtyczce oszczędziłaby Wam najwięcej czasu
  w miesiącu?
