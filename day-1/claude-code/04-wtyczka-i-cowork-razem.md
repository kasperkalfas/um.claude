# Zadanie 4: Wtyczka Claude in Chrome razem z Cowork – praktyka

> **Materiał wprowadzający**, zakłada [zadanie 1](01-czym-jest-cowork.md)
> (czym jest Cowork) i [zadanie 3](03-wtyczka-chrome.md) (instalacja
> wtyczki Chrome) jako zrobione wcześniej.

**Cel:** zobaczyć w praktyce, że Cowork nie ma własnych „oczu i rąk" w
internecie – korzysta z **jednej z dwóch przeglądarek**, którą sam
wybierasz, i przetestować przełączanie między nimi.
**Poziom:** podstawowy

## Przypomnienie: dwie przeglądarki, jeden Cowork

- **Wbudowana przeglądarka** – izolowana, nic wspólnego z Twoimi
  loginami, nic nie instalujesz (zadanie 1).
- **Claude in Chrome** – wtyczka w Twojej prawdziwej przeglądarce, z
  Twoimi zalogowanymi kontami (zadanie 3).

Cowork w danym zadaniu **zawsze korzysta z jednej z nich** – domyślnie z
tej, którą ustawisz jako preferowaną, ale możesz to nadpisać wprost w
poleceniu do konkretnego zadania.

## Gdzie to ustawić

1. Otwórz aplikację Claude (desktop albo web) → **Ustawienia → Cowork**.
2. Znajdź sekcję **„Preferred browser"** (Preferowana przeglądarka).
3. Wybierz jedną z dwóch opcji:
   - **Built-in browser** – zalecane na start i do testów na fikcyjnych
     danych,
   - **Chrome (Claude in Chrome)** – tylko jeśli masz zainstalowaną
     wtyczkę z zadania 3 i świadomie chcesz, żeby Cowork korzystał z
     Twojej prawdziwej przeglądarki.

**Dla admina IT Urzędu (informacyjnie, nie robi tego każdy uczestnik):**
na planie Team te opcje da się też ustawić centralnie dla całej
organizacji w **Organization settings → Cowork** (wbudowana przeglądarka)
i **Organization settings → Claude in Chrome** (wtyczka, tu też ustawia
się dozwolone/zablokowane strony – wspólne dla obu przeglądarek). Na
planie Team obie opcje są domyślnie włączone.

## Kroki – test 1: wbudowana przeglądarka (bezpieczny wariant)

1. Ustaw „Preferred browser" na **Built-in browser**.
2. Uruchom Cowork z celem, np.: *„Wejdź na polską Wikipedię, znajdź hasło
   'budżet obywatelski' i przygotuj krótkie, 3-zdaniowe podsumowanie."*
3. Obserwuj panel boczny – zobaczysz, jak Cowork otwiera stronę, czyta
   ją, w osobnym, izolowanym oknie przeglądarki (nie w Twoim Chrome).
4. Sprawdź: czy w tym czasie mogłeś/aś normalnie korzystać ze swojej
   przeglądarki równolegle, bez przeszkadzania sobie nawzajem? (To
   właśnie zaleta izolacji.)

## Kroki – test 2: Twoja przeglądarka przez wtyczkę

5. Ustaw „Preferred browser" na **Chrome (Claude in Chrome)** – upewnij
   się, że wtyczka z zadania 3 jest zainstalowana i włączona.
6. Uruchom Cowork z tym samym (neutralnym, publicznym) celem co wyżej.
7. Zaobserwuj różnicę: tym razem Cowork otwiera zakładkę **w Twoim
   prawdziwym oknie Chrome** – zobaczysz, jak się otwiera i przełącza,
   dokładnie tak jak przy samodzielnym korzystaniu z wtyczki w zadaniu 3.
8. Sprawdź w Ustawieniach wtyczki (**Site permissions**), czy odwiedzona
   strona pojawiła się na liście z historią uprawnień.

## Kroki – test 3: nadpisanie preferencji w jednym poleceniu

9. Niezależnie od tego, co ustawiłeś/aś w Ustawieniach, spróbuj napisać
   to wprost w treści zadania dla Cowork, np.:
   *„Zrób to w mojej przeglądarce Chrome"* albo *„Użyj wbudowanej
   przeglądarki, nie mojego Chrome, do tego zadania."*
10. Zaobserwuj: Cowork powinien zastosować się do polecenia z tego
    konkretnego zadania, **nie zmieniając** Twojego ogólnego ustawienia
    w Cowork → Preferred browser.

## Na co zwrócić uwagę

- Jeśli preferowana przeglądarka jest akurat niedostępna: przy zadaniu
  ogólnym Cowork sam przełączy się na drugą i Cię o tym poinformuje;
  przy zadaniu, w którym wprost wskazujesz przeglądarkę, **najpierw
  zapyta o zgodę** na zmianę.
- To ustawienie („Preferred browser") działa też dla sesji Cowork na
  web i mobile – nie tylko w aplikacji desktopowej.
- **Zasada bezpieczeństwa jest ta sama co w zadaniach 1 i 3**: testy na
  fikcyjnych, publicznych stronach, nigdy na systemach/kontach
  służbowych Urzędu bez pisemnej zgody Zamawiającego
  (`CLAUDE.md`, sekcja o bezpieczeństwie danych).
- Wybór przeglądarki nie zmienia trybu zatwierdzania akcji (Manual/Auto/
  Skip z zadania 3) – to dwa niezależne ustawienia i warto ustawiać oba
  świadomie.

## Notatki własne

- Którą przeglądarkę wybrałbyś/wybrałabyś jako domyślną w swojej
  codziennej pracy i dlaczego?
- Czy zauważyłeś/aś różnicę w tym, jak bardzo Cowork „przeszkadzał" Ci w
  normalnym korzystaniu z komputera przy każdym z dwóch wariantów?
