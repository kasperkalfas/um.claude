# Zadanie 10: Claude Code zawsze pyta o zgodę przed zmianą

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok D, 60 min: Claude Code – pierwszy kontakt**).

**Cel:** oswoić się z mechanizmem kontroli – Claude Code nie robi nic
nieodwracalnego bez pytania, a Ty masz zawsze ostatnie słowo.
**Poziom:** podstawowy
**Czas:** ok. 6 minut

## Kroki

1. Poproście Claude Code o coś, co wymaga zmiany pliku, np.: *„Zmień
   nazwę pliku zestawienie_przykladowe.xlsx na
   zestawienie_wrzesien_2026.xlsx."*
2. Zanim cokolwiek się zmieni, Claude Code **pokazuje dokładnie, co
   zamierza zrobić** i prosi o potwierdzenie (podobnie jak tryb Manual we
   wtyczce Chrome z [zadania 3](03-wtyczka-chrome.md)).
3. Za pierwszym razem **odrzućcie** propozycję (opcja „Odrzuć"/„No") i
   sprawdźcie w Eksploratorze plików, że nic się nie zmieniło.
4. Poproście o to samo jeszcze raz i tym razem **zaakceptujcie** –
   sprawdźcie, że plik faktycznie zmienił nazwę.

## Na co zwrócić uwagę

- To jest dokładnie ta sama zasada bezpieczeństwa, co przy connectorach i
  Cowork ([zadanie 1](01-czym-jest-cowork.md)) – Claude pyta, zanim
  zmieni cokolwiek trwałego.
- Odrzucenie propozycji **nic nie psuje** – to bezpieczny, odwracalny
  krok, nie błąd.
- Właśnie dlatego kolejne zadania w tym bloku (i cały Dzień 2) można
  bezpiecznie testować na plikach – zawsze zobaczycie propozycję zmiany,
  zanim się wydarzy.
