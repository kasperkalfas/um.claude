# Zadanie 5: MCP – jak Claude sięga po dane i narzędzia poza rozmową

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
wstęp do **Bloku D: Claude Code – pierwszy kontakt**).

**Cel:** zrozumieć, czym jest MCP (Model Context Protocol), jak ma się do
„konektorów" z Claude Czat i Cowork, co z niego trafia do okna kontekstu
– i co to oznacza dla bezpieczeństwa danych Urzędu.
**Poziom:** podstawowy (teoria, bez klikania)
**Czas:** ok. 8 minut (lektura + rozmowa z prowadzącym)

## Problem, który to rozwiązuje

Model sam z siebie **nic nie widzi poza oknem kontekstu**: nie zna
Waszego kalendarza, nie otworzy Excela z dysku sieciowego, nie sprawdzi
lotu. Wszystko, co „wie", musi ktoś do okna wprowadzić – Wy (wklejając)
albo jakiś mechanizm (automatycznie). MCP to ten mechanizm. Bez niego
Claude jest bardzo oczytanym rozmówcą zamkniętym w pokoju bez okien.

## Co to jest MCP

**MCP (Model Context Protocol) to otwarty standard, przez który Claude
podłącza się do zewnętrznych źródeł danych i narzędzi.** Najprościej:
**wtyczka jak USB** – jeden wspólny standard gniazda, a po drugiej
stronie może być cokolwiek: kalendarz, poczta, dysk, baza danych,
system rezerwacji, arkusz.

Trzy strony układu:

| Kto | Co robi | Przykład |
|---|---|---|
| **Serwer MCP** | udostępnia dane i czynności („narzędzia") w standardowej formie | serwer Google Calendar: *pokaż wydarzenia*, *dodaj wydarzenie* |
| **Klient MCP** | aplikacja, w której rozmawiacie – pośredniczy między Wami, modelem a serwerem | Claude Czat, Cowork, Claude Code |
| **Model** | decyduje, *kiedy* i *którego* narzędzia użyć, i interpretuje wynik | Claude Opus 5 / Sonnet 5 |

„Konektory", które podpinaliście w zadaniach 4–5 z Bloku C (Google
Calendar, Booking.com, Kiwi.com), to właśnie serwery MCP w gotowej,
sklepowej wersji – producent usługi wystawia serwer, Wy klikacie
„Połącz". W Claude Code ten sam mechanizm konfiguruje się plikiem
(`.mcp.json`) – i to jest droga, którą IT Urzędu mogłoby kiedyś podpiąć
np. bazę ERP w trybie „tylko odczyt".

## Co się dzieje, gdy Claude używa MCP

Weźmy pytanie: *„Co mam jutro w kalendarzu?"*

1. **Do okna kontekstu trafia lista narzędzi** podpiętych serwerów – ich
   nazwy, opisy i parametry. Dzieje się to **na starcie każdej rozmowy**,
   zanim o cokolwiek zapytacie.
2. Model czyta pytanie i **wybiera narzędzie** (*pokaż wydarzenia*,
   parametr: jutrzejsza data). Nie wykonuje go sam – prosi klienta.
3. Klient (Czat/Cowork/Code) **wywołuje serwer**; w Claude Code
   zobaczycie pytanie o zgodę, jak przy zmianie pliku.
4. **Wynik wraca do okna kontekstu** jako zwykły tekst – i dopiero teraz
   model „wie", co macie jutro. Odpowiada Wam po polsku.

Z perspektywy tokenów (zadania 1–4) ważne są punkty 1 i 4: **opisy
narzędzi zajmują okno w każdej rozmowie, nawet nieużywane**, a **każdy
wynik z serwera to kolejne tokeny** – lista 300 wydarzeń „waży" więcej
niż lista 3.

## Materiały

- Ten plik i rozmowa z prowadzącym. Bez podpinania czegokolwiek.
- Dla chętnych po szkoleniu: lista konektorów w ustawieniach Claude
  (Czat/Cowork) – gdzie widać, co jest podpięte do Waszego konta.

## Kroki

1. Przeczytajcie tabelę „trzy strony układu". Sprawdźcie, czy umiecie
   powiedzieć własnymi słowami, czym różni się **serwer** od **klienta**
   (podpowiedź: serwer „ma dane", klient „ma Was i model").
2. Prześledźcie 4 kroki na przykładzie pytania o kalendarz. Potem
   zróbcie to samo dla zadania z Bloku C: *„Znajdź lot z Wrocławia do
   Warszawy w przyszły wtorek"* – które narzędzie, jaki parametr, co
   wraca do okna?
3. Rozmowa z prowadzącym (3 min) – trzy pytania:
   - Gdyby Urząd chciał podpiąć przez MCP **eksport z ERP** (Proces 1),
     jaki serwer i jakie narzędzia musiałyby powstać? Kto by za to
     odpowiadał – Wy czy IT?
   - Co z **danymi**: wynik z serwera wraca do okna, czyli trafia do
     dostawcy modelu. Czy to zgodne z zasadą z Bloku B?
   - Ile konektorów naprawdę potrzebujecie w codziennej pracy: 2? 10?
     Co robi 8 nieużywanych z Waszym oknem kontekstu?

## Na co zwrócić uwagę

- **MCP nie „daje modelowi dostępu do wszystkiego".** Serwer wystawia
  tylko konkretne narzędzia (np. *odczytaj*, ale nie *usuń*), a klient
  pyta o zgodę. Zakres ustala ten, kto konfiguruje serwer – dla
  systemów Urzędu byłoby to IT, nie użytkownik.
- **Każdy podpięty serwer to koszt stały w oknie kontekstu.** Opisy
  narzędzi są wczytywane na starcie rozmowy, niezależnie od użycia.
  Podpinajcie to, z czego korzystacie; resztę odłączcie (zasada z
  zadania 3: `/context` pokaże, ile zajmują).
- **Wynik z serwera = dane wysłane do dostawcy modelu.** Podpięcie
  konektora do systemu z danymi osobowymi lub poufnymi (poczta służbowa,
  ERP, rejestry) podlega tej samej zasadzie co wklejanie: **bez
  pisemnej zgody Urzędu/PNT – nie**. W Bloku C ćwiczyliśmy dlatego na
  kalendarzu prywatnym i konektorach podróży, nie na systemach Urzędu.
- **MCP a skille to dwie różne rzeczy.** Skill (zadania 7–8 z Bloku C)
  to *instrukcja, jak coś robić* (np. jak pisać notatkę budżetową);
  serwer MCP to *dostęp do danych i czynności* (np. odczyt kalendarza).
  Skill może korzystać z MCP; MCP nie potrzebuje skilla. Oba zajmują
  miejsce w oknie.
- **Przyszłość Procesu 1 i 2** wygląda tak: dziś Claude Code czyta
  eksport z ERP z pliku, który Wy zapisujecie na dysk; jutro mógłby go
  pobrać przez serwer MCP w trybie tylko-odczyt. Mechanika po stronie
  modelu jest identyczna – zmienia się tylko, kto dostarcza dane do okna.

## Notatki własne

- Które z Waszych systemów (ERP, poczta, kalendarz, dysk sieciowy)
  miałyby sens jako serwer MCP – i w jakim trybie (odczyt / zapis)?
- Jakie pytanie zadalibyście IT Urzędu, zanim pozwolicie podpiąć
  cokolwiek do Claude?
