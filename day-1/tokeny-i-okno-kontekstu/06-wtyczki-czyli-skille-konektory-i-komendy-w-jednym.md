# Zadanie 6: Wtyczki (plugins) – skille, konektory, komendy i subagenci w jednym pakiecie

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
wstęp do **Bloku D: Claude Code – pierwszy kontakt**).

**Cel:** zrozumieć, czym jest wtyczka (plugin) w Claude, z jakich czterech
elementów się składa, jak ma się do skilli i MCP z poprzednich zadań –
i jak przejrzeć katalog wtyczek w Cowork, nie instalując niczego.
**Poziom:** podstawowy (teoria + krótki podgląd katalogu)
**Czas:** ok. 8 minut

## Problem, który to rozwiązuje

Do tej pory każdy element konfigurowaliśmy osobno: skill z Bloku C
(notatka budżetowa), konektor (kalendarz), własną komendę w Claude Code
(`/zamknij-miesiac`). I przy każdej nowej rozmowie od nowa tłumaczyliśmy,
kim jesteśmy i co chcemy zrobić. **Wtyczka** to gotowy pakiet, który
łączy te elementy w jedną całość „do konkretnej roboty" – tak, żeby
wystarczyło wpisać jedną komendę.

## Co to jest wtyczka

**Wtyczka (plugin) to pakiet, który łączy skille, konektory, komendy
(`/`) i subagentów w jedną całość wykonującą określone zadanie.** Nie
trzeba umieć programować, żeby jej używać ani żeby ją zbudować.

| Element | Co to jest | Gdzie już to widzieliście |
|---|---|---|
| **Skille** | wiedza specjalistyczna i sposób pracy („jak pisać notatkę o odchyleniach") | [zadania 7–8 z Bloku C](../claude-zadania/07-skill-notatka-budzetowa.md) |
| **Konektory (MCP)** | dostęp do danych i narzędzi: dysk, poczta, kalendarz, Teams | [zadanie 5](05-mcp-czyli-jak-claude-siega-po-dane.md), zadania 4–5 z Bloku C |
| **Komendy `/`** | „szybki start" – jedna komenda uruchamia cały opisany wcześniej przepływ pracy | `/zamknij-miesiac` w [zadaniu 10 z Claude Code + Excel](../claude-code-cli/10-claude-md-i-wlasna-komenda.md) |
| **Subagenci** | wyspecjalizowani wykonawcy – agent główny rozdziela zadanie na kilku „pracowników" | nowość – patrz niżej |

Przykład z Waszej branży. Pracownik wydziału finansowego w jednym
procesie: **szuka** danych, **liczy** w Excelu, **pisze** raport, **składa**
PDF, **wysyła** mailem. To pięć umiejętności plus dostęp do poczty i
plików. Wtyczka „zamknięcie miesiąca" pakuje to razem, a komenda
`/zamknij-miesiac` mówi: *zrób to wszystko, oto nowe dane*. Nie trzeba
za każdym razem opisywać, kim jesteście i jak wygląda Wasz proces.

## Subagenci – dlaczego nie jeden agent do wszystkiego

W Urzędzie nikt nie robi wszystkiego sam: ktoś księguje, ktoś planuje,
ktoś kontroluje. Tak samo działają wtyczki: **agent główny** dostaje
zadanie („zbuduj zestawienie roczne z prognozą"), rozbija je na części i
uruchamia **subagentów** – jeden czyta pliki, drugi liczy, trzeci
sprawdza wynik. Każdy subagent ma **własne okno kontekstu** (zadanie 2),
więc duże zadanie nie zapycha jednej rozmowy: agent główny dostaje tylko
wyniki, nie całą pracę pośrednią. To jeden z głównych powodów, dla których
wtyczki radzą sobie z zadaniami, które w pojedynczym czacie by „nie
weszły".

## Gotowe wtyczki od Anthropic

Anthropic przygotował wtyczki dla zawodów, w których dużą część pracy da
się opisać jako powtarzalny proces na plikach i danych.
W katalogu są m.in. kategorie: **produktywność**, **sprzedaż** (kontakt
z klientem, CRM), **prawo**, **dane i finanse** (FP&A, analiza odchyleń),
**HR**, **projektowanie**, **inżynieria**, **badania**. Dla Was najbardziej
interesująca jest kategoria finansowa – analiza odchyleń to w praktyce
Wasz Proces 2.

## Materiały

- Claude Cowork (aplikacja desktopowa) – tylko do **podglądu** katalogu.
  Niczego nie instalujemy w trakcie zajęć.
- Ten plik i rozmowa z prowadzącym.

## Kroki

1. Otwórzcie Cowork. Na pasku po lewej kliknijcie **Customize**, a potem
   **Browse plugins** (nazwy przycisków mogą się nieco zmieniać między
   wersjami aplikacji – szukajcie katalogu wtyczek w sekcji
   personalizacji). Przejrzyjcie kategorie (produktywność, sprzedaż,
   prawo, dane/finanse…). Nie klikajcie **Install**.
2. Wybierzcie jedną wtyczkę z kategorii finansowej i przeczytajcie jej
   opis. Spróbujcie rozpoznać cztery elementy z tabeli: jakie skille?
   jakie konektory (do czego chce się podłączyć)? jakie komendy `/`?
   czy używa subagentów?
3. Rozmowa z prowadzącym (3 min):
   - Gdyby zbudować wtyczkę „Proces 1 + 2" dla Waszego wydziału – co
     byłoby skillem, co konektorem, jak nazwalibyście komendę, i co
     robiliby subagenci?
   - Które konektory z tej wtyczki wymagałyby pisemnej zgody
     Urzędu/PNT, zanim ktokolwiek je podepnie?
4. Zapiszcie w „Notatkach" jedną wtyczkę, którą chcielibyście
   przetestować **po szkoleniu**, na danych fikcyjnych.

## Na co zwrócić uwagę

- **Wtyczka = skille + konektory + komendy + subagenci.** Nic nowego pod
  spodem – to pakiet rzeczy, które już znacie, poukładany pod konkretną
  pracę. Zamiast budować agenta od zera, wybieracie gotowy zestaw.
- **Komenda `/` to „streszczenie tego, co robicie jako człowiek".** Raz
  opisany przepływ pracy uruchamiacie potem jednym słowem – dokładnie
  tak, jak `/zamknij-miesiac` w zadaniach Claude Code + Excel.
- **Każda wtyczka zajmuje okno kontekstu.** Skille, opisy konektorów i
  komend są wczytywane na starcie rozmowy (zadania 3 i 5). Zainstalowana
  wtyczka „HR" w rozmowie o budżecie to czysty koszt. Instalujcie to,
  czego używacie.
- **Konektory we wtyczce = te same zasady co w zadaniu 5.** Wtyczka, która
  chce dostęp do poczty służbowej, Teams czy dysku Urzędu, przenosi dane
  do dostawcy modelu. Bez pisemnej zgody Zamawiającego – nie. Na
  szkoleniu oglądamy katalog, nie podpinamy systemów.
- **Subagenci nie znaczy „bez nadzoru".** Agent główny raportuje Wam
  wynik, a w Claude Code każda zmiana pliku nadal wymaga zgody. Wy
  odpowiadacie za zestawienie, nie „armia agentów".

## Notatki własne

- Jaką wtyczkę z katalogu chcecie sprawdzić po szkoleniu (na danych
  fikcyjnych)? Co ma robić?
- Gdyby Wasz wydział miał jedną własną wtyczkę – jak nazwałaby się jej
  główna komenda `/` i co by uruchamiała?
