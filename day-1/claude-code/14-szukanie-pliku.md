# Zadanie 14: Szukanie pliku w gąszczu folderów

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok D, 60 min: Claude Code – pierwszy kontakt**).

**Cel:** szukać po **treści**, nie po nazwie – opisać, czego szukacie,
i dostać ścieżkę do pliku.
**Poziom:** podstawowy
**Czas:** ok. 6 minut

## Materiały

- Folder `test-claude-code` (po zadaniu 13): `Wrzesien/`, `Pazdziernik/`,
  `archiwum/`. W archiwum leży `zal_3_korekta.xlsx` – nazwa nic nie mówi,
  ale w środku jest wydział Zieleni Miejskiej.

## Kroki

1. Szukanie po treści:

   ```
   Znajdź w tym folderze i podfolderach wszystkie pliki, w których
   występuje wydział „Zieleni Miejskiej". Podaj pełne ścieżki.
   ```

   **Sprawdź:** Claude wymienia **6 plików**, w tym
   `archiwum\zal_3_korekta.xlsx` – plik, którego po nazwie nikt by nie
   znalazł.

2. Pytanie mniej precyzyjne:

   ```
   W którym pliku jest najwyższa pojedyncza kwota w kolumnie
   Kwota wykonana? Podaj kwotę, dział i ścieżkę do pliku.
   ```

   **Sprawdź:** **860 000 zł, Wydział Inwestycji**,
   `Pazdziernik\UM_zestawienie_pazdziernik_PODSUMOWANIE.xlsx`.

3. Otwórzcie wskazany plik z podanej ścieżki i potwierdźcie kwotę
   w Excelu.

## Na co zwrócić uwagę

- Windows szuka po nazwie. Claude Code szuka **po treści i sensie** –
  zagląda do środka każdego pliku.
- **Zawsze proście o ścieżkę** – żeby sprawdzić samodzielnie, nie na
  słowo.
