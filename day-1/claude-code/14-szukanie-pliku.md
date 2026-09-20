# Zadanie 14: Szukanie pliku w gąszczu folderów

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok D, 60 min: Claude Code – pierwszy kontakt**).

**Cel:** zamiast ręcznie przeszukiwać Eksplorator plik po pliku – opisać
Claude Code, czego szukacie, i pozwolić mu znaleźć to za Was.
**Poziom:** podstawowy
**Czas:** ok. 6 minut

## Materiały

- Folder `test-claude-code` po zadaniu 13 (już posegregowany na
  `Wrzesien/` i `Pazdziernik/`). W `archiwum/` czeka plik o nieoczywistej
  nazwie `zal_3_korekta.xlsx` – to on ma być „znaleziskiem" w kroku 1
  (klucz odpowiedzi: `../materialy/test-claude-code/README.md`).

## Kroki

1. Poproście o wyszukanie po **treści**, nie tylko po nazwie, np.: *„Znajdź
   w tym folderze (i podfolderach) plik, w którym jest wydział 'Zieleni
   Miejskiej'."*
2. Zwróćcie uwagę, że Claude Code **zagląda do środka plików**, a nie
   tylko patrzy na nazwy – tego nie da się łatwo zrobić samym
   Eksploratorem Windows bez dodatkowych narzędzi.
3. Spróbujcie mniej precyzyjnego zapytania, np.: *„Który plik ma
   najwyższą kwotę wykonaną w kolumnie Kwota wykonana?"* – i sprawdźcie,
   czy Claude Code sam przeszuka wszystkie pliki, żeby odpowiedzieć.
4. Poproście o wskazanie **dokładnej ścieżki** do znalezionego pliku, żeby
   móc go samodzielnie otworzyć.

## Na co zwrócić uwagę

- To pokazuje różnicę między szukaniem „po nazwie" (to potrafi też
  Windows) a szukaniem „po treści i sensie" (to jest mocna strona AI).
- Przy jednym pliku różnica jest kosmetyczna – przy dziesiątkach plików w
  różnych podfolderach to ogromna oszczędność czasu.
- Zawsze warto poprosić o **ścieżkę do pliku**, żeby zweryfikować wynik
  samodzielnie, a nie polegać wyłącznie na podsumowaniu.
