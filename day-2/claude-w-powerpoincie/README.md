# Claude w PowerPoincie — dodatek Claude by Anthropic (Dzień 2)

Materiały do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
prowadzący: Kasper Kalfas).

**Miejsce w agendzie:** Dzień 2 – druga część ścieżki „Claude w
aplikacjach Office", bezpośrednio po
[`../claude-w-excelu/`](../claude-w-excelu/README.md) (ten sam mechanizm
instalacji, to samo konto, ten sam panel boczny). Dodatek jest
narzędziem, którego uczestnicy będą używać w **Dniu 3** (Bloki B–C:
tworzenie prezentacji z Claude, prezentacja danych w PowerPoint,
DataPOV) – dlatego instalację i pierwszy kontakt robimy dzień wcześniej,
żeby Dzień 3 zacząć od treści, nie od klikania w sklep dodatków.

## Zadania

- [ ] **[01 – Claude w PowerPoincie – instalacja dodatku i pierwsze uruchomienie](01-claude-w-powerpoincie-instalacja.md)** *(8 min)*
      — Dodatki → Claude by Anthropic → logowanie → model → „co jest w
      tej prezentacji?" z odwołaniami do numerów slajdów.
- [ ] **[02 – Prezentacja z jednego zdania – plan, zgoda, slajdy „rodzą się" na Waszych oczach](02-prezentacja-z-jednego-zdania.md)** *(15 min)*
      — tryb zgód (pytaj / akceptuj), pytania o odbiorcę–długość–styl,
      plan do zatwierdzenia, samokontrola slajdów; część 2: prezentacja
      z pięciu punktów z Excela (Wasza treść, forma Claude).
- [ ] **[03 – Notatki prelegenta do każdego slajdu – i co w nich sprawdzić](03-notatki-prelegenta.md)** *(10 min)*
      — jedno polecenie → pole notatek pod każdym slajdem; kontrola
      faktów spoza slajdów; dopasowanie czasu (45 s/slajd), głosu,
      przejść; istniejąca prezentacja; notatki w innym języku.
- [ ] **[04 – Nowy slajd z podanego źródła i zmiana tonu dla innego odbiorcy](04-slajd-ze-zrodla-i-zmiana-tonu.md)** *(12 min)*
      — slajd z jawnej strony (ISAP/BIP) w stylu reszty + notatka + przypis;
      kontrola liczb ze źródłem; „tylko slajd 1" dla młodzieży, potem dla
      Rady; granica tonu w materiale Urzędu.
- [ ] **[05 – Prezentacja w szablonie Urzędu – Claude ma się dopasować, nie narzucać](05-prezentacja-w-szablonie-urzedu.md)** *(12 min)*
      — 3 slajdy w istniejącym szablonie; trzy testy: Resetuj (układy vs
      pola na wierzchu), zmiana motywu, stałe elementy (herb, stopka,
      numer); poprawka słowem; „odchudzony" szablon do pracy z AI.
- [ ] **[06 – Poprawianie gotowej prezentacji słowami – tytuł z tezą, ikona, slajd bez ściany tekstu](06-poprawianie-gotowej-prezentacji.md)** *(25 min)*
      — istniejąca prezentacja o wykonaniu budżetu (5 slajdów, dane
      fikcyjne); tytuł = teza z liczbą (most do DataPOV); ikona + pętla
      „zrzut → poprawka"; slajd 2: 46 liczb w akapicie → 8 kart;
      **kontrola 16 liczb względem klucza** (zaokrąglenia, znaki,
      zamiana kart, liczby dopisane); wnioski sprzeczne z danymi; 80/20.

## Plan kolejnych zadań (w przygotowaniu)

Kolejność odpowiada temu, jak Wydział buduje prezentację w Procesie 3:

| # | Temat | Materiał wejściowy (fikcyjny) |
|---|---|---|
| 07 | Porównanie Claude / Copilot / NotebookLM na tym samym poleceniu | temat z zad. 02 |
| 08 | Prezentacja z dokumentu Word / PDF – w szablonie Urzędu (przedostatni krok Procesu 3) | `../../agenda/Agenda_szkolenia.pdf` lub notatka fikcyjna |
| 09 | Obrazy i wykresy na slajdach; burza mózgów „czego brakuje" | wykresy z `../claude-w-excelu/` zad. 4 |
| 10 | Streszczenie istniejącej prezentacji i artefakty z niej (notatka, e-mail, plan wystąpienia) | `../../day-1/day1-claude.pptx` |
| 11 | Przygotowanie do wystąpienia: pytania od odbiorców, próba, plan B bez rzutnika | prezentacja z zad. 02–09 |

(Planowane wcześniej „Tytuły slajdów: z opisowych na wnioskowe" weszło do
zad. 06 jako krok 2.)

## Dane w `materialy/`

`wykonanie_budzetu_2026_8m.pptx` (zad. 06) – celowo przeciętna
prezentacja (domyślny szablon, ściana tekstu, tabela, wypunktowanie,
wnioski „zgodnie z planem") o fikcyjnym wykonaniu wydatków 8 działów po
8 miesiącach 2026 r. Liczby liczone z
`../../day-1/claude-code-cli/materialy/zestawienie_roczne_2026.xlsx`
(te same działy i kwoty, co w ścieżce Claude Code), prognoza roczna =
średnia miesięczna × 12. `generuj_prezentacja.py` odtwarza plik i
wypisuje klucz (46 liczb slajdu 2, działy nad planem 750 i 851,
prognoza −2,9 %, przykładowy tytuł-teza).

## Wymagania techniczne (sprawdzić przed Dniem 2)

| Co | Uwaga |
|---|---|
| PowerPoint z Microsoft 365 (desktop Windows lub przeglądarka) | starsze wersje bez sklepu dodatków nie zadziałają |
| Dostęp do sklepu dodatków Office | jedno zgłoszenie do IT dla obu dodatków (Excel + PowerPoint) |
| Konto Claude w organizacji Urzędu (plan Team) | to samo co do czatu, Cowork i Excela |
| (Opcjonalnie) pusty szablon `.pptx` Urzędu | wygląd, nie dane – można używać |

> Zasada bezpieczeństwa danych z Dnia 1 (Blok B) obowiązuje bez
> wyjątków: dodatek wysyła treść otwartej prezentacji do dostawcy
> modelu. Prezentacje z realnymi danymi Urzędu – tylko za pisemną zgodą
> Zamawiającego. Na szkoleniu: pliki fikcyjne i materiały szkoleniowe.
