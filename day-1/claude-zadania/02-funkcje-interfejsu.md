# Zadanie 2: Poznanie interfejsu Claude – funkcje, które warto znać

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**Blok C, 60 min: Claude Czat w przeglądarce**).

**Cel:** poznać funkcje interfejsu Claude, które będą przydatne w codziennej
pracy z zestawieniami i raportami – pliki, Artifacts, historię rozmów,
styl odpowiedzi i pamięć – zanim przejdziemy do pracy na realnych
przykładach w kolejnych dniach.
**Poziom:** podstawowy
**Czas:** ok. 20 minut

> **Przypomnienie z Bloku B:** wszystkie pliki i liczby w tym zadaniu są
> przykładowe/fikcyjne. Nie wgrywaj prawdziwych danych budżetowych urzędu –
> do tego wrócimy dopiero po ustaleniu pisemnej zgody, zgodnie z zasadami
> omówionymi w Bloku B.

## Materiały

- Konto na [claude.ai](https://claude.ai) – instrukcja logowania w
  [README](README.md#jak-zacząć-pracę-z-claude).
- Prompty P.K.Z.O. z [zadania 1](01-formula-pkzo.md).
- Plik `../materialy/zestawienie_przykladowe.xlsx` (fikcyjne dane).

## Mapa interfejsu – zanim zaczniesz

Zanim przejdziesz do kroków, zlokalizuj na ekranie:

- **Pole wiadomości** na środku/dole ekranu – tu wpisujesz prompty.
- **"New chat"** – rozpoczyna nową, pustą rozmowę.
- **Listę rozmów** po lewej stronie – historia wszystkiego, o co kiedyś
  pytałeś/aś.
- **Ikonę spinacza/"+"** przy polu wiadomości – wgrywanie plików.
- **"Search and tools"** – włączanie wyszukiwania w internecie i
  konektorów (poznamy je w materiale dodatkowym po szkoleniu).
- **Avatar/ikonę konta** w lewym dolnym rogu – tam są Ustawienia.

## Kroki

### Część 1: Wgrywanie i analiza pliku

1. Weź gotowy, fikcyjny plik `zestawienie_przykladowe.xlsx`
   (`day-1/materialy/`) – zestawienie kilku wydziałów urzędu z kolumnami:
   dział, kwota planowana, kwota wykonana, miesiąc.
2. Kliknij ikonę wgrywania pliku przy polu wiadomości i dodaj ten plik do
   rozmowy.
3. Poproś Claude o opis struktury, np.:
   *"Opisz strukturę tego pliku: ile jest kolumn, co zawierają, czy widzisz
   jakieś braki lub niespójności."*
4. Zwróć uwagę, że Claude "widzi" tylko to, co jest w pliku – nazwy kolumn i
   arkuszy pomagają mu zrozumieć dane szybciej (to samo metadane, o których
   mówiliśmy w Bloku B).

### Część 2: Artifacts – gdy odpowiedź to więcej niż tekst

5. W tej samej rozmowie poproś:
   *"Podsumuj te dane w przejrzystej tabeli i dodaj do niej krótki komentarz
   pod spodem."*
6. Zauważ, że dłuższa tabela lub dokument pojawia się w osobnym panelu
   (Artifact) obok rozmowy, a nie jako zwykły tekst na czacie – łatwiej go
   przewijać, kopiować i edytować.
7. Poproś o zmianę w Artifact, np.: *"Dodaj kolumnę z procentowym odchyleniem
   od planu"* – sprawdź, czy Claude modyfikuje istniejący dokument, zamiast
   tworzyć wszystko od nowa.

### Część 3: Styl odpowiedzi i pamięć

8. Wejdź w **Ustawienia** (avatar w lewym dolnym rogu) i znajdź opcję stylu
   odpowiedzi (np. Concise/Zwięzły, Explanatory/Wyjaśniający). Przełącz styl
   i zadaj to samo pytanie co w kroku 3 – porównaj długość i ton odpowiedzi.
9. Sprawdź w Ustawieniach funkcję pamięci (jeśli dostępna na Waszym
   koncie/planie) – Claude może zapamiętywać ustalenia między rozmowami
   (np. że pracujesz w urzędzie i wolisz zwięzłe odpowiedzi po polsku).
10. Otwórz **"New chat"**, wróć do listy rozmów po lewej i odnajdź rozmowę z
    tego zadania – w praktyce tak wygląda wracanie do wcześniejszej pracy.

## Na co zwrócić uwagę

- **Nowa rozmowa = czysta karta.** Jeśli chcesz zacząć zupełnie inny temat,
  lepiej otworzyć "New chat", niż kontynuować w tej samej, długiej rozmowie
  – odpowiedzi bywają trafniejsze.
- **Artifact to żywy dokument w ramach rozmowy**, nie plik na dysku – jeśli
  chcesz go zachować na stałe, pobierz go lub skopiuj treść.
- Styl odpowiedzi i pamięć to ustawienia, które warto skonfigurować raz na
  początku, a nie za każdym razem tłumaczyć Claude, jak ma odpowiadać.
- To, co widzieliście dziś na pojedynczym, fikcyjnym pliku, to dokładnie ten
  sam mechanizm, którego użyjemy w Dniu 2 do pracy z zanonimizowanym
  przykładem zestawienia miesięcznego.

## Notatki własne

- Która funkcja (pliki, Artifacts, styl, pamięć) wydaje Ci się najbardziej
  przydatna do Twojej codziennej pracy?
- Czy zmiana stylu odpowiedzi realnie zmieniła użyteczność odpowiedzi dla
  Ciebie?
