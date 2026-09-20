# Zadanie 10: Własna wtyczka Wydziału – analiza odchyleń i zestawienie dla banku jedną komendą

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**praca własna po szkoleniu** albo demo prowadzącego; domknięcie zadań
6–9 i most do `/zamknij-miesiac` z Claude Code w Dniu 2).

**Cel:** zamiast korzystać z cudzej wtyczki, opisać Cowork **własny
proces** – kim jesteście, na jakich danych pracujecie, jakie macie zasady
– i poprosić, żeby złożył z tego wtyczkę z dwiema komendami:
`/analiza-odchylen` (plan vs wykonanie) i `/zestawienie-dla-banku`
(Proces 2). Potem uruchomić obie i zamienić wynik w prezentację.
**Poziom:** średniozaawansowany (praktyka w Cowork)
**Czas:** ok. 40 minut (tworzenie wtyczki ~10, uruchomienie komend ~20,
prezentacja ~10)
**Wymaga:** Cowork, konto w planie Team Urzędu, pliki fikcyjne z repo
(niżej).

## Problem, który to rozwiązuje

Gotowa wtyczka finansowa z katalogu (zadanie 6) zna „finanse w ogóle":
rachunek zysków i strat, bilans, cash flow. Wy nie robicie bilansu –
robicie **wykonanie budżetu wg działów klasyfikacji budżetowej, plan vs
wykonanie, prognozę dla banku**. Zamiast tłumaczyć to agentowi w każdej
rozmowie, opisujecie raz – jako wtyczkę. Od tej pory `/analiza-odchylen`
znaczy dokładnie to, co u Was znaczy „analiza odchyleń".

## Materiały

Folder roboczy `Pulpit\wtyczka-wydzialu\` z **kopiami** plików
fikcyjnych:

| Plik | Skąd | Do czego |
|---|---|---|
| `zestawienie_miesieczne_PODSUMOWANIE.xlsx` | `../materialy/` | 10 wydziałów, plan/wykonanie za październik; 7 wydziałów przekracza plan → `/analiza-odchylen` |
| `zestawienie_roczne_2026.xlsx` | `../claude-code-cli/materialy/` | arkusz `Wykonanie` (plan roczny, I–VIII) i pusty arkusz `Prognoza` → `/zestawienie-dla-banku` |

Plus **opis wtyczki** (niżej) – skopiujcie go do Notatnika i uzupełnijcie
pola w nawiasach kwadratowych `[...]`. Co zostawicie w nawiasach, o to
agent dopyta w trakcie; co wpiszecie na sztywno, przyjmie bez pytania.

## Opis wtyczki – szablon do wklejenia

```
Chcę, żebyś zbudował dla mnie własną wtyczkę Cowork dopasowaną do moich
obowiązków. Nazwa wtyczki: wydzial-finansowy.

MÓJ PROFIL
- Rola: [Skarbnik / główny księgowy / inspektor ds. budżetu]
- Organizacja: urząd miejski (jednostka samorządu terytorialnego), Polska
- Rok budżetowy: kalendarzowy (styczeń–grudzień)
- Waluta raportowania: PLN, kwoty z separatorem tysięcy, bez groszy
- Narzędzie pracy: Excel; wynik zawsze jako plik .xlsx
- Odbiorcy raportów: [Skarbnik / Rada Miasta / bank kredytujący / mieszkańcy]

STRUKTURA DANYCH
- Wydatki grupujemy wg działów klasyfikacji budżetowej, np.: 600 Transport
  i łączność, 750 Administracja publiczna, 801 Oświata i wychowanie,
  851 Ochrona zdrowia, 852 Pomoc społeczna, 900 Gospodarka komunalna
  i ochrona środowiska, 921 Kultura i ochrona dziedzictwa narodowego,
  926 Kultura fizyczna.
- Zestawienie miesięczne: kolumny Dział | Kwota planowana | Kwota wykonana
  | Miesiąc.
- Zestawienie roczne: arkusz "Wykonanie" (Dział, Nazwa działu, Plan
  roczny, miesiące I–XII, Razem, % planu) i arkusz "Prognoza" (Plan
  roczny, Wykonanie narastająco, Średnia miesięczna, Prognoza roczna,
  Odchylenie od planu).

KOMENDA 1: /analiza-odchylen
Cel: porównać wykonanie z planem w zestawieniu miesięcznym.
Kroki:
1. Wczytaj wskazany plik miesięczny; sprawdź puste wiersze, niespójne
   formaty miesiąca, scalone komórki – zgłoś je, nie poprawiaj po cichu.
2. Policz odchylenie w PLN i w % dla każdego działu.
3. Oznacz działy z odchyleniem powyżej [10]% (na plus i na minus).
4. Wypisz 5 największych odchyleń z krótkim, rzeczowym komentarzem
   (bez zgadywania przyczyn – jeśli nie wynikają z danych, napisz
   "do wyjaśnienia z wydziałem").
5. Zapisz nowy plik <nazwa>_odchylenia.xlsx z arkuszami: Odchylenia,
   Top5, Dane_do_wykresu (wykres wodospadowy plan → wykonanie).
   Nigdy nie nadpisuj pliku źródłowego.

KOMENDA 2: /zestawienie-dla-banku
Cel: uzupełnić zestawienie roczne i prognozę (nasz "Proces 2").
Kroki:
1. Wczytaj zestawienie roczne i wskazany plik miesięczny; dopasuj wiersze
   po kodzie działu (kolumna A), nigdy po nazwie.
2. Wpisz kwoty wykonane do właściwej kolumny miesiąca.
3. W arkuszu "Prognoza" wpisz FORMUŁY (nie wartości): wykonanie
   narastająco, średnia miesięczna, prognoza roczna = średnia × 12,
   odchylenie od planu.
4. Zaznacz działy, w których prognoza przekracza plan roczny.
5. Zapisz jako <nazwa>_<rok>_<miesiąc>.xlsx; przelicz formuły i sprawdź,
   że nie ma błędów (#ARG!, #ADR!).
6. Napisz 5-punktowe podsumowanie po polsku dla odbiorcy: [bank].

SKILL: zasady-wydzialu (wiedza wspólna dla obu komend)
- Wszystkie dane w ćwiczeniach są fikcyjne; nie proś o dane realne.
- Kopia przed każdą zmianą pliku (podfolder kopie/).
- Kwoty: PLN, separator tysięcy, bez groszy; procenty z 1 miejscem.
- Odchylenie = wykonanie − plan; dodatnie = przekroczenie planu.
- Formuły zamiast wpisanych wartości wszędzie, gdzie to możliwe.
- Ton komentarzy: rzeczowy, urzędowy, bez ocen personalnych.

KONEKTORY MCP: żadnych. Pracujemy wyłącznie na plikach w bieżącym
folderze.

Złóż tę wtyczkę i przed zapisaniem pokaż mi jej pełną strukturę
(skille, komendy, agenci, konektory) do przejrzenia.
```

## Kroki

1. **Porządek przed startem.** Cowork → **Customize**: sprawdźcie, że nie
   macie włączonej innej wtyczki finansowej ani skilli, które mogłyby się
   „wtrącić" (np. skill prognozowania z zadania 9 – wyłączcie na czas
   ćwiczenia).
2. **Folder i polecenie.** Nowe zadanie → *Choose a different folder* →
   `Pulpit\wtyczka-wydzialu` → **Allow**. Wklejcie uzupełniony opis
   wtyczki i uruchomcie. Agent najpierw **dopyta o pola w nawiasach**
   (rola, próg %, odbiorca) – odpowiadajcie krótko. Potem po prawej
   zobaczycie, że sięga po wbudowany skill tworzenia wtyczek, czyta
   Wasz Excel, składa pakiet i przedstawia strukturę do przeglądu.
3. **Przegląd struktury.** Zanim klikniecie *Save*: czy są dokładnie dwie
   komendy o Waszych nazwach? jeden skill `zasady-wydzialu`? zero
   konektorów? Otwórzcie podgląd komendy `/analiza-odchylen` – kroki
   powinny być Waszymi krokami, przepisanymi po angielsku lub po polsku.
   Jeśli agent coś „dodał od siebie" (np. bilans) – każcie usunąć.
   Kliknijcie **Save** i (opcjonalnie) **Download** – plik
   `wydzial-finansowy.plugin` ląduje w folderze; w **Customize →
   Plugins** wtyczka powinna być już widoczna z dwiema komendami.
4. **Test komendy 1.** Nowe zadanie w tym samym folderze → `/` →
   `wydzial-finansowy` → `/analiza-odchylen` → na pytanie o plik:
   `zestawienie_miesieczne_PODSUMOWANIE.xlsx`. Obserwujcie podzadania
   (wczytaj → policz → oznacz > 10% → top 5 → zapisz). **Sprawdzian:**
   plik ma 10 wydziałów, **7 przekracza plan** – tyle powinno być
   oznaczonych na plus. Otwórzcie `_odchylenia.xlsx` i porównajcie
   jedno odchylenie z własnym wyliczeniem.
5. **Test komendy 2.** `/zestawienie-dla-banku` → plik roczny
   `zestawienie_roczne_2026.xlsx` + miesięczny z kroku 4 jako nowy miesiąc.
   **Sprawdzian:** w arkuszu `Prognoza` kliknijcie komórkę „Prognoza
   roczna" – ma być **formuła**, nie liczba; kody działów 600–926
   dopasowane po kolumnie A (zestawienie miesięczne używa nazw
   wydziałów – agent powinien **zapytać o mapowanie**, a nie zgadywać;
   jeśli zgadł – to błąd do zapisania w notatkach).
6. **Prezentacja.** W tej samej rozmowie: *„Podsumuj analizę odchyleń
   i zestawienie dla banku w prezentacji PowerPoint dla [odbiorca]:
   7 slajdów – tytuł, streszczenie, plan vs wykonanie, top 5 odchyleń
   z wykresem wodospadowym, prognoza roczna, działy zagrożone
   przekroczeniem planu, następne kroki."* Skill PowerPoint zrobi
   projekt → plik → kontrolę wizualną → poprawki. Odbiór jak w zadaniu
   8: min. 2 liczby sprawdzone z arkuszem.

## Na co zwrócić uwagę

- **Wtyczka to Wasz proces spisany po ludzku.** Nie pisaliście kodu –
  opisaliście, co robicie krok po kroku, i jakie macie zasady. To samo,
  co `CLAUDE.md` + własna komenda w Claude Code (Dzień 2), tylko w
  Cowork i w jednym pakiecie do udostępnienia.
- **Nawiasy `[...]` = pytania, sztywne wpisy = decyzje.** Jeśli wtyczka
  ma być tylko dla Was, wpiszcie wszystko na sztywno – agent nie będzie
  pytał. Jeśli dla całego zespołu – zostawcie nawiasy tam, gdzie ludzie
  się różnią (rola, odbiorca).
- **„Nie poprawiaj po cichu" i „zapytaj o mapowanie" to celowe zasady.**
  Sprawdzają, czy agent trzyma się Waszych reguł, a nie „ulepsza".
  Wtyczka, która sama zgaduje, że „Wydział Edukacji" = dział 801, jest
  wygodna – i niebezpieczna w zestawieniu dla banku.
- **Formuły, nie wartości.** Wbudowany skill Excel i tak to wymusza, ale
  wpisanie tej zasady we własny skill sprawia, że obowiązuje też, gdy
  ktoś w zespole poprosi „szybko, bez formuł".
- **Zero konektorów – świadomie.** Wtyczka pracuje tylko na plikach w
  folderze. Podpięcie ERP, poczty czy dysku Urzędu to osobna decyzja IT
  i Zamawiającego (zadanie 5), nie linijka w opisie.
- **Koszt.** Tworzenie wtyczki jest tanie; jej uruchomienie na dwóch
  plikach + prezentacja – nie (zadanie 8, Settings → Usage). Testujcie na
  jednym pliku, a nie na dziesięciu miesiącach naraz.
- **70–80% to nie 100%.** Wynik komend wygląda profesjonalnie, ale to
  wersja robocza: mapowanie działów, odchylenia i prognoza są **do
  sprawdzenia przez Was** za każdym razem. Na realnych danych Urzędu –
  wyłącznie za pisemną zgodą (Blok B) i po ocenie IT.

## Notatki własne

- Ile wydziałów oznaczyła komenda 1 jako przekraczające plan? (klucz: 7)
- Czy komenda 2 zapytała o mapowanie nazw wydziałów na kody działów, czy
  zgadła?
- Jaka trzecia komenda w tej wtyczce oszczędziłaby Wam najwięcej czasu w
  miesiącu?
