# Zadanie 4: Wtyczka Claude in Chrome razem z Cowork – praktyka

> **Materiał wprowadzający**, zakłada [zadanie 1](01-czym-jest-cowork.md)
> i [zadanie 3](03-wtyczka-chrome.md) jako zrobione.

**Cel:** wykonać to samo zadanie w Cowork trzy razy – przez wbudowaną
przeglądarkę, przez wtyczkę Chrome i z przeglądarką wskazaną wprost
w poleceniu – i zobaczyć różnicę.
**Poziom:** podstawowy
**Czas:** ok. 15 minut

## Dwie przeglądarki, jeden Cowork

Cowork nie ma własnych „oczu" w internecie – używa **jednej z dwóch**
przeglądarek:

- **Built-in browser** – izolowana, bez Twoich loginów (zadanie 1);
  zalecana na start,
- **Chrome (Claude in Chrome)** – Twoja prawdziwa przeglądarka, z Twoimi
  kontami (zadanie 3).

Wybierasz w **Ustawienia → Cowork → Preferred browser**. Wybór
przeglądarki **nie zmienia** trybu zatwierdzania (Manual/Auto/Skip) – to
dwa osobne ustawienia. Zasada bezpieczeństwa jak w zadaniach 1 i 3: tylko
publiczne strony, nigdy systemy służbowe.

## Kroki

### Test 1: wbudowana przeglądarka

1. Ustawienia → Cowork → **Preferred browser → Built-in browser**.
2. Uruchom Cowork z celem:

   ```
   Wejdź na polską Wikipedię, znajdź hasło „budżet obywatelski"
   i przygotuj krótkie, 3-zdaniowe podsumowanie.
   ```

3. **Sprawdź:** Cowork otwiera stronę w osobnym oknie, **nie** w Twoim
   Chrome. Możesz w tym czasie normalnie korzystać ze swojej przeglądarki.

### Test 2: Twoja przeglądarka przez wtyczkę

4. **Preferred browser → Chrome (Claude in Chrome)**. Wtyczka z zadania 3
   musi być włączona.
5. Uruchom Cowork z **tym samym** celem co w kroku 2.
6. **Sprawdź:** tym razem karta otwiera się **w Twoim oknie Chrome**.
   W ustawieniach wtyczki (**Site permissions**) odwiedzona strona
   pojawiła się na liście.

### Test 3: przeglądarka wskazana w poleceniu

7. Nie zmieniaj ustawień. Do celu dopisz jedno zdanie:

   ```
   Wejdź na polską Wikipedię, znajdź hasło „budżet obywatelski"
   i przygotuj krótkie, 3-zdaniowe podsumowanie. Użyj wbudowanej
   przeglądarki, nie mojego Chrome.
   ```

8. **Sprawdź:** Cowork użył wbudowanej przeglądarki, a ustawienie
   **Preferred browser** w Ustawieniach **nie zmieniło się** – polecenie
   działa tylko dla tego jednego zadania.

## Na co zwrócić uwagę

- Gdy preferowana przeglądarka jest niedostępna, Cowork sam przełączy się
  na drugą i powie o tym. Gdy wskażesz przeglądarkę w poleceniu –
  najpierw zapyta o zgodę na zmianę.
- Admin IT na planie Team może ustawić obie opcje centralnie dla całej
  organizacji (Organization settings → Cowork / Claude in Chrome), w tym
  listę dozwolonych i zablokowanych stron.

## Notatki własne

- Którą przeglądarkę wybrałbyś/wybrałabyś jako domyślną i dlaczego?
- Czy któryś wariant „przeszkadzał" Ci w normalnej pracy na komputerze?
