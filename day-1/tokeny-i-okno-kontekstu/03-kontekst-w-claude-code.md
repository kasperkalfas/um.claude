# Zadanie 3: Kontekst w praktyce – Claude Code i Cowork

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
wstęp do **Bloku D: Claude Code – pierwszy kontakt**).

**Cel:** zobaczyć okno kontekstu „na liczniku" i użyć trzech poleceń,
które nim sterują: `/context`, `/compact`, `/clear`.
**Poziom:** podstawowy
**Czas:** ok. 7 minut
**Wymaga:** Claude Code ([instalacja](../claude-code/06-instalacja-claude-code-cli.md))
uruchomiony w folderze `test-claude-code` na Pulpicie (kopia
`../materialy/test-claude-code/`).

## Trzy polecenia

| Polecenie | Co robi | Co tracicie |
|---|---|---|
| `/context` | pokazuje, ile okna zajęte i przez co | nic |
| `/compact` | streszcza rozmowę i zastępuje ją streszczeniem | szczegóły |
| `/clear` | czysta karta | całą rozmowę (zostaje `CLAUDE.md` i pliki na dysku) |

## Kroki

1. **Koszt stały.** Zaraz po uruchomieniu, zanim cokolwiek napiszecie:

   ```
   /context
   ```

   **Sprawdź:** okno **nie jest puste** – instrukcje systemowe, opisy
   narzędzi, `CLAUDE.md` już zajmują miejsce. Zapiszcie procent.

2. **Wczytajcie pliki:**

   ```
   Przeczytaj wszystkie pliki w tym folderze i streść, co w nich jest.
   ```

   Potem znów:

   ```
   /context
   ```

   **Sprawdź:** o ile urosło? Pliki i odpowiedź Claude liczą się razem.

3. **Kompaktowanie:**

   ```
   /compact
   ```

   Claude streszcza rozmowę. `/context` pokaże spadek. Zapytajcie:

   ```
   Co było w plikach, które czytałeś przed chwilą?
   ```

   **Sprawdź:** odpowiada ze streszczenia – sens jest, drobne szczegóły
   mogą zniknąć. To samo Claude Code robi **automatycznie**, gdy okno się
   zapełnia (komunikat „compacting").

4. **Czysta karta:**

   ```
   /clear
   ```

   `/context` pokazuje znów tylko koszt stały z kroku 1.

5. **(Jeśli jest Cowork)** Otwórzcie Cowork i pokażcie pasek kontekstu po
   prawej – ten sam mechanizm graficznie.

## Nawyki na Dzień 2

1. Jeden temat = jedna rozmowa (`/clear` między zadaniami).
2. Proście o **podsumowanie** pliku, nie o wklejenie całości.
3. Duże Excele niech Claude Code czyta skryptem – do okna trafia wynik,
   nie tysiące komórek.
4. `CLAUDE.md` krótki – wczytuje się do **każdej** rozmowy.
5. Ważne ustalenia (format kwot, zasady) zapisujcie w `CLAUDE.md`
   ([zadanie 19](../claude-code/19-claude-md-pamiec-projektu.md)) – plik
   przeżyje każde kompaktowanie i `/clear`.
6. Gdy Claude „gubi wątek" – nie walczcie: `/compact` albo `/clear`
   i krótkie przypomnienie.

## Na co zwrócić uwagę

- **Kompaktowanie to streszczenie, nie pamięć.**
- Skille, konektory i serwery MCP też zajmują okno – ich opisy wczytują
  się do każdej rozmowy, nawet nieużywane (zadania 5–6).

## Notatki własne

- Ile procent okna było zajęte po kroku 1? Po kroku 2?
- Które z Waszych zadań warto rozbić na osobne rozmowy?
