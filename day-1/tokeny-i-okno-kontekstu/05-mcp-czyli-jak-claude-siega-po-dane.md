# Zadanie 5: MCP – jak Claude sięga po dane i narzędzia poza rozmową

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
wstęp do **Bloku D: Claude Code – pierwszy kontakt**).

**Cel:** zobaczyć na własnym koncie, jakie konektory (serwery MCP) są
podpięte, ile miejsca zajmują w oknie kontekstu, i prześledzić jedno
wywołanie krok po kroku.
**Poziom:** podstawowy
**Czas:** ok. 8 minut

## W trzech zdaniach

Model **nic nie widzi poza oknem kontekstu** – nie zna kalendarza, nie
otworzy dysku sieciowego. **MCP (Model Context Protocol)** to standardowe
„gniazdo USB", przez które Claude podłącza zewnętrzne dane i narzędzia.
„Konektory" z Bloku C (Google Calendar, Booking, Kiwi) to gotowe serwery
MCP; w Claude Code ten sam mechanizm konfiguruje plik `.mcp.json` – i tą
drogą IT mogłoby kiedyś podpiąć ERP w trybie tylko-odczyt.

| Kto | Co robi |
|---|---|
| **Serwer MCP** | „ma dane" – wystawia narzędzia: *pokaż wydarzenia*, *dodaj wydarzenie* |
| **Klient** (Czat / Cowork / Claude Code) | „ma Was i model" – pośredniczy, pyta o zgodę |
| **Model** | wybiera narzędzie, interpretuje wynik |

**Co się dzieje, gdy pytacie „Co mam jutro w kalendarzu?"**
1. Na starcie rozmowy do okna trafiają **opisy wszystkich narzędzi**
   podpiętych serwerów – nawet nieużywanych.
2. Model wybiera narzędzie i prosi klienta o wykonanie.
3. Klient wywołuje serwer (w Claude Code – po Waszej zgodzie).
4. **Wynik wraca do okna jako tekst** – i dopiero teraz model „wie".

## Materiały

- Claude Code w folderze `test-claude-code` (z zadania 3).
- Claude Czat lub Cowork – ustawienia konektorów.

## Kroki

1. **Co jest podpięte?** W Claude Czat: **Search and tools → Add
   connectors** – policzcie, ile konektorów jest połączonych.
   W Claude Code:

   ```
   /mcp
   ```

   **Sprawdź:** lista serwerów MCP (może być pusta – to w porządku).

2. **Ile to kosztuje w oknie?** W Claude Code:

   ```
   /context
   ```

   **Sprawdź:** pozycja z narzędziami / MCP tools – to koszt stały
   z punktu 1 powyżej, płacony w każdej rozmowie.

3. **Prześledźcie jedno wywołanie.** Jeśli macie podpięty kalendarz
   (prywatny, z Bloku C), w Claude Czat:

   ```
   Co mam jutro w kalendarzu? Zanim odpowiesz, napisz jednym zdaniem,
   jakiego narzędzia użyjesz i z jakim parametrem.
   ```

   **Sprawdź:** Claude nazywa narzędzie (np. *list events*) i parametr
   (jutrzejsza data) – to punkt 2 z listy wyżej. Wynik, który wraca, to
   punkt 4.

   Bez kalendarza: zróbcie to na sucho dla pytania

   ```
   Znajdź lot z Wrocławia do Warszawy w przyszły wtorek.
   ```

   – które narzędzie, jaki parametr, co wraca do okna?

4. **Rozmowa (3 min):**
   - Eksport z ERP przez MCP (Proces 1): jaki serwer, jakie narzędzia,
     kto za to odpowiada – Wy czy IT?
   - Wynik z serwera trafia do okna, czyli do dostawcy modelu. Czy to
     zgodne z zasadą z Bloku B?
   - Ile konektorów naprawdę potrzebujecie? Co robi 8 nieużywanych
     z oknem kontekstu?

## Na co zwrócić uwagę

- **MCP nie daje dostępu „do wszystkiego".** Serwer wystawia konkretne
  narzędzia (np. *odczytaj*, ale nie *usuń*); zakres ustala ten, kto
  konfiguruje – dla systemów Urzędu IT.
- **Każdy serwer = koszt stały w oknie.** Odłączcie to, czego nie
  używacie.
- **Wynik z serwera = dane wysłane do dostawcy.** Konektor do poczty
  służbowej, ERP, rejestrów – tylko za pisemną zgodą Urzędu/PNT.
- **MCP ≠ skill.** Skill = *jak coś robić*; MCP = *dostęp do danych
  i czynności*. Oba zajmują okno.

## Notatki własne

- Ile konektorów macie podpiętych? Ile z nich używacie co tydzień?
- Które systemy Urzędu miałyby sens jako serwer MCP – i w jakim trybie
  (odczyt / zapis)?
