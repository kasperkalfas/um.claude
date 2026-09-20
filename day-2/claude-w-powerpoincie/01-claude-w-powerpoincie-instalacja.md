# Zadanie 1: Claude w PowerPoincie – instalacja dodatku i pierwsze uruchomienie

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
**Dzień 2** – domknięcie ścieżki „Claude w aplikacjach Office", po
[`../claude-w-excelu/`](../claude-w-excelu/README.md); przygotowanie
narzędzia pod Dzień 3, Bloki B–C: tworzenie prezentacji z Claude).

**Cel:** dodać Claude do PowerPointa jako dodatek (tak samo jak do
Excela), zalogować się kontem Urzędu, wybrać model – i sprawdzić, że
panel widzi otwartą prezentację, zanim w kolejnych zadaniach zacznie ją
budować i poprawiać.
**Poziom:** podstawowy
**Czas:** ok. 8 minut
**Wymaga:** PowerPoint z Microsoft 365 (desktop Windows albo
przeglądarka), konto Claude w planie Team Urzędu, dostęp do sklepu
dodatków Office (jeśli dodatek Excela zadziałał – ten też zadziała).

## Problem, który to rozwiązuje

Prezentację dla Skarbnika, Rady czy banku (Proces 3) buduje się dziś
tak: liczby z Excela → ręcznie na slajdy → wykresy wklejone jako
obrazki → tytuły „wymyślone na kolanie" → poprawki po uwagach. W Dniu 1
Claude generował gotowe `.pptx` z Cowork (folder „tokeny i okno
kontekstu", zadania 8 i 10) – ale to plik, który dostajecie z zewnątrz.
Dodatek **Claude w PowerPoincie** pracuje **w otwartej prezentacji**:
tworzy slajdy, przepisuje tytuły, dodaje obrazy, streszcza istniejący
pokaz, robi prezentację z Worda lub PDF-a – i każda zmiana jest widoczna
od razu, w Waszym pliku, w Waszym szablonie.

## Materiały

- Pusta prezentacja (Plik → Nowy) **albo** dowolna prezentacja
  szkoleniowa z tego repozytorium (np. `../../day-1/day1-claude.pptx`)
  – do sprawdzenia, że dodatek ją widzi. Nic jeszcze nie zmieniamy.
- Login do konta Claude Urzędu.

> Ta sama zasada co przy Excelu: dodatek wysyła treść otwartej
> prezentacji do Anthropic. **Prezentacje z realnymi danymi Urzędu
> (kwoty, nazwiska, dokumenty wewnętrzne) otwieramy z dodatkiem tylko
> za pisemną zgodą Zamawiającego** (Dzień 1, Blok B). Na szkoleniu –
> pliki fikcyjne i materiały szkoleniowe.

## Kroki

1. **Otwórzcie PowerPoint** i prezentację (pustą albo `day1-claude.pptx`).
2. **Dodatki.** Prawy górny róg wstążki (albo *Wstawianie → Pobierz
   dodatki*) → **Dodatki** → wyszukajcie `Claude`. Pozycja **Claude by
   Anthropic** z opisem w rodzaju *build, edit and refine presentations –
   purpose-built for PowerPoint* → **Dodaj**. Po kilkunastu sekundach na
   wstążce pojawia się przycisk **Open Claude**, a po prawej panel.
3. **Zalogujcie się** – adres e-mail konta Claude w organizacji Urzędu,
   potem standardowe logowanie. Jeśli logowaliście się dziś do dodatku
   w Excelu, panel może połączyć się od razu.
4. **Model** – prawy dolny róg panelu. Do budowania i przebudowywania
   prezentacji: **Opus** (najlepiej trzyma strukturę i styl). Do pytań
   i drobnych poprawek: **Sonnet**. Tak jak w Excelu – model zmienia
   się jednym kliknięciem, więc zaczynajcie od tańszego, przełączajcie
   gdy trzeba.
5. **Pierwszy kontakt.** W panelu: *„Co jest w tej prezentacji? Ile
   slajdów, jaki układ, jaki szablon?"* Jeśli otworzyliście pustą –
   Claude ma to powiedzieć wprost („jeden pusty slajd tytułowy, motyw
   domyślny"). Jeśli `day1-claude.pptx` – ma podać liczbę slajdów i
   streścić 2–3 z nich, **odwołując się do numerów slajdów**. To
   dowód, że panel czyta otwarty plik, a nie zgaduje.
6. **Przegląd, bez klikania.** Przejrzyjcie podpowiedzi startowe w
   panelu (tworzenie prezentacji z opisu, z dokumentu, poprawa slajdów,
   streszczenie). Zmiany w prezentacji zaczynają się w zadaniu 2.
7. **Notatka o Copilocie** (jeśli macie). W tym samym rogu wstążki może
   być przycisk **Copilot** – to asystent Microsoftu na innych modelach
   i na innej umowie o dane. Na szkoleniu porównamy oba na tym samym
   poleceniu (zadanie 2), ale pracujemy w Claude. Nie musicie go
   włączać.

## Na co zwrócić uwagę

- **Trzy miejsca, trzy zasięgi.** Czat: prezentacja jako plik do
  pobrania. Cowork: `.pptx` w folderze, budowane z wielu plików.
  Dodatek: praca **w otwartej prezentacji** – najbliżej Waszego
  szablonu i najłatwiej poprawiać po jednym slajdzie. Wybór narzędzia
  zależy od tego, czy zaczynacie od danych (Cowork), czy od slajdów
  (dodatek).
- **Szablon Urzędu to atut, nie dane.** Pusty `.pptx` z logo, kolorami
  i układami można otworzyć z dodatkiem – to wygląd. Dopiero treść
  (kwoty, nazwiska) podlega zasadzie z Bloku B.
- **Panel = ta sama rozmowa co w czacie**: limity planu Team, okno
  kontekstu (długa prezentacja z dużą ilością tekstu i notatek to
  tysiące tokenów przy każdym pytaniu), zasada „co w oknie, to u
  dostawcy".
- **Jeśli sklepu dodatków nie ma** – to blokada administratora
  Microsoft 365, ta sama co przy Excelu. Jedno zgłoszenie do IT
  załatwia oba dodatki; zgłaszać **przed** szkoleniem.
- **Wersja beta** – dodatek jest rozwijany; przyciski i podpowiedzi
  mogą wyglądać inaczej niż w opisie. Logika się nie zmienia: panel po
  prawej, model na dole, polecenia po polsku.

## Notatki własne

- Czy panel poprawnie podał liczbę slajdów i streścił wskazane?
- Które prezentacje robicie cyklicznie (miesięczne, dla Rady, dla
  banku) – i która z nich ma **najwięcej ręcznego przepisywania liczb**?
  To kandydat na zadanie 2.
