# Zadanie 10: Claude Code zawsze pyta o zgodę przed zmianą

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok D, 60 min: Claude Code – pierwszy kontakt**).

**Cel:** przećwiczyć mechanizm kontroli – Claude Code nic nie zmienia bez
pytania, a odrzucenie propozycji niczego nie psuje.
**Poziom:** podstawowy
**Czas:** ok. 6 minut

## Materiały

- Folder `test-claude-code` (po zadaniu 9) – w folderze głównym
  `zestawienie_przykladowe.xlsx`.

## Kroki

1. Poproście o zmianę, która dotyka pliku:

   ```
   Zmień nazwę pliku zestawienie_przykladowe.xlsx
   na zestawienie_wrzesien_2026.xlsx.
   ```

2. Claude Code pokazuje dokładnie, co zamierza zrobić, i czeka na
   potwierdzenie.
3. **Odrzućcie** („No" / „Odrzuć").
4. **Sprawdź** w Eksploratorze: plik nadal nazywa się
   `zestawienie_przykladowe.xlsx`. Nic się nie stało.
5. Poproście jeszcze raz (możecie po prostu napisać `Zrób to jednak`)
   i tym razem **zaakceptujcie**.
6. **Sprawdź** w Eksploratorze: plik nazywa się teraz
   `zestawienie_wrzesien_2026.xlsx`.

## Na co zwrócić uwagę

- Ta sama zasada co w Cowork i wtyczce Chrome (tryb Manual): Claude pyta,
  zanim zmieni cokolwiek trwałego.
- Odrzucenie to bezpieczny, normalny krok – nie błąd.
- Dzięki temu cały Blok D i Dzień 2 można testować bez obaw: zawsze
  widzicie propozycję, zanim się wykona.
