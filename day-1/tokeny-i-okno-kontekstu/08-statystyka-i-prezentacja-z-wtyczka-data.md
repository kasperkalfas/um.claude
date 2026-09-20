# Zadanie 8: Od analizy do prezentacji dla przełożonego – skill statystyczny i PowerPoint

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**demo prowadzącego na koniec Bloku D** albo praca własna po szkoleniu;
kontynuacja [zadania 7](07-dashboard-z-wtyczka-data.md)).

**Cel:** domknąć przepływ z zadania 7: uruchomić skill analizy
statystycznej na tych samych danych, a potem jednym poleceniem zamienić
wszystko, co powstało, w prezentację PowerPoint dla przełożonego –
i sprawdzić, ile to kosztowało (zużycie limitu).
**Poziom:** średni (praktyka w Cowork)
**Czas:** ok. 20 minut (w tym kilka minut generowania prezentacji)
**Wymaga:** Cowork z zainstalowaną wtyczką **Data**, folder
`Pulpit\analiza-danych` z plikami i wynikami z zadania 7.

## Problem, który to rozwiązuje

Dashboard i wyczyszczony plik to dopiero półprodukt. Do Skarbnika, Rady
czy banku idzie **prezentacja**: kilka slajdów z liczbami, wykresami i
wnioskami (Proces 3). Zwykle to osobne popołudnie: przepisywanie liczb,
wklejanie wykresów, dopasowanie do szablonu. Tu agent robi to z wyników,
które już ma w folderze – a Wy oceniacie, czy slajdy mówią prawdę.

## Skill ≠ komenda – jak je uruchamiać

W zadaniu 7 używaliście **komend** (`/explore-data`, `/validate`,
`/build-dashboard`) – to gotowe przepływy krok po kroku. Wtyczka ma też
**skille** – wiedzę, którą agent stosuje, gdy go o to poprosicie, np.
`statistical-analysis` (statystyki opisowe, trendy, wartości odstające).
Po wpisaniu `/` widać jedne i drugie; skill uruchamia się tak samo
(`/data:statistical-analysis`), tylko zamiast sztywnego przepływu agent
sam planuje podzadania i **często uruchamia kilku subagentów równolegle**
(zadanie 6) – zobaczycie to po prawej, gdy kilka pozycji odhacza się
niemal jednocześnie.

## Materiały

- Folder `Pulpit\analiza-danych` z zadania 7 (pliki `.xlsx`, `_v1.xlsx`,
  dashboard `.html`, ewentualne wykresy `.png`).
- (Opcjonalnie) pusty **szablon prezentacji** `.pptx` Urzędu wrzucony do
  tego samego folderu – szablon nie zawiera danych, więc może być
  prawdziwy; agent sam go rozpozna, można mu to też napisać wprost.

## Kroki

1. **Analiza statystyczna.** W tym samym zadaniu Cowork (albo nowym,
   w tym samym folderze) wpiszcie `/` → `statistical-analysis` i
   doprecyzujcie: *„na pliku `zestawienie_roczne_2026.xlsx`, arkusz
   `Wykonanie`: statystyki opisowe wykonania miesięcznego po działach,
   trend I–VIII, wartości odstające, które działy odbiegają od reszty."*
   Po prawej pojawią się podzadania (statystyki opisowe → wartości
   odstające → różnice między działami → raport). Zwróćcie uwagę, że
   równolegle uruchomił się też skill Excel – to on czyta arkusz.
2. **Przeczytajcie „najsilniejsze ustalenia".** Agent pokaże 3–5
   najważniejszych wniosków i link do pełnego raportu. Sprawdźcie **jeden
   wniosek ręcznie** w Excelu (np. „dział 801 ma najwyższą zmienność
   miesięczną" – policzcie min/max w wierszu). Jeśli wniosek jest
   sformułowany ostrzej, niż uzasadniają liczby – zapiszcie to; przyda
   się w kroku 3 jako uwaga do prezentacji.
3. **Prezentacja.** Jedno polecenie, bez komendy:
   *„Podsumuj wszystko, co wygenerowałeś w tym folderze (profil danych,
   walidacja, dashboard, analiza statystyczna), w prezentacji PowerPoint
   dla mojego przełożonego: maks. 8 slajdów, każdy slajd jedna myśl,
   liczby w PLN z separatorem tysięcy, te same wykresy co w dashboardzie
   (odtworzone jako obrazy), na końcu
   wnioski i proponowane następne kroki. Zapisz jako
   `wykonanie_2026_prezentacja.pptx` w tym folderze."*
   Jeśli macie szablon: dopiszcie *„użyj szablonu `szablon_UM.pptx`"*.
4. **Obserwujcie etapy po prawej.** Uruchamia się skill PowerPoint:
   projekt slajdów → generowanie pliku → **konwersja slajdów do obrazów
   i kontrola wizualna** → poprawki → dopiero potem oddanie pliku. To ta
   sama „samokontrola" co przy dashboardzie w zadaniu 7 – agent ogląda
   własne slajdy, zanim Wy je zobaczycie.
5. **Odbiór.** Otwórzcie `.pptx` w PowerPoincie. Sprawdźcie po kolei:
   czy liczby na slajdach zgadzają się z arkuszem (min. 2 wartości);
   czy wykresy mają podpisane osie i jednostki; czy wniosek z kroku 2,
   który uznaliście za zbyt ostry, nie trafił na slajd „bez
   złagodzenia"; czy slajd „następne kroki" proponuje coś, co Wy byście
   zaproponowali. Poprawki zlecajcie **po polsku, konkretnie**: *„Na
   slajdzie 4 zamień wykres kołowy na słupkowy i dodaj wartości."*
6. **Ile to kosztowało.** Cowork → **Settings → Usage**: zobaczycie
   procent wykorzystanego limitu tygodniowego i bieżącej sesji oraz
   czas do resetu. Zapiszcie liczby przed i po zadaniach 7–8. W
   **Settings → Capabilities** sprawdźcie, że włączone są *code
   execution* i *file creation* – bez nich skille Excel/PowerPoint nie
   zadziałają.

## Na co zwrócić uwagę

- **Model do wyboru, jakość do wyboru.** Najmocniejszy model (Opus) daje
  najlepsze raporty i slajdy, ale zużywa najwięcej tokenów. Do szybkich,
  prostych rzeczy (jedna tabela, jeden wykres) można przełączyć się na
  tańszy i szybszy model (Sonnet, Haiku) – tylko nie oczekujcie tej samej
  głębi analizy. Wybór modelu to decyzja *przed* uruchomieniem, nie po.
- **Limity są tygodniowe i sesyjne.** Jedno pełne przejście zadań 7–8
  potrafi zjeść kilkanaście procent tygodniowego limitu. Uruchamiajcie
  cały przepływ, gdy naprawdę robicie zestawienie – nie „na próbę" pięć
  razy dziennie.
- **Prezentacja od agenta = pierwsza wersja, nie finalna.** Slajdy
  wyglądają dobrze, ale to Wy odpowiadacie za każdą liczbę i każdy
  wniosek. Dzień 3 (DataPOV, storytelling) pokaże, jak z „poprawnych
  slajdów" zrobić prezentację, która przekonuje – to zadanie daje tylko
  surowiec.
- **Szablon to nie dane.** Pusty `.pptx` Urzędu można dać agentowi – to
  wygląd, nie treść. Ale prezentacja z **prawdziwymi** liczbami Urzędu
  to już dane Zamawiającego: tylko za pisemną zgodą (Blok B).
- **Wszystko ląduje w jednym folderze.** Raport statystyczny, dashboard,
  prezentacja – obok źródłowych plików. Warto od razu wprowadzić nawyk
  podfolderów (`wyniki/`, `kopie/`), jak w zadaniach Claude Code + Excel.
- **Na później: harmonogram.** Cowork pozwala zaplanować zadanie
  (**Scheduled**) – np. co miesiąc 1. dnia „uruchom `/validate` na nowym
  eksporcie i przygotuj prezentację". To temat na koniec Dnia 2, kiedy
  Proces 1 i 2 będą już opisane jako komenda `/zamknij-miesiac`.

## Notatki własne

- Który wniosek statystyczny sprawdziliście ręcznie i czy się potwierdził?
- Ile procent limitu tygodniowego zużyły zadania 7–8 razem?
- Co z tej prezentacji zostawilibyście bez zmian, a co przepisalibyście
  po swojemu przed pokazaniem przełożonemu?
