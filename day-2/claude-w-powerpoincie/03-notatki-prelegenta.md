# Zadanie 3: Notatki prelegenta do każdego slajdu – i co w nich sprawdzić, zanim wyjdziecie na mównicę

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
**Dzień 2**, ścieżka „Claude w PowerPoincie"; kontynuacja
[zadania 2](02-prezentacja-z-jednego-zdania.md)).

**Cel:** jednym poleceniem dopisać notatki prelegenta pod każdym slajdem
prezentacji z zadania 2, sprawdzić, czy trafiły **do pola notatek
PowerPointa** (a nie tylko do panelu), przeczytać je krytycznie – bo
notatki potrafią zawierać liczby, których nie ma na slajdach – i
dopasować je do odbiorcy, czasu i języka.
**Poziom:** podstawowy
**Czas:** ok. 10 minut (generowanie 1–3 min)
**Wymaga:** dodatek Claude w PowerPoincie, prezentacja z zadania 2
(część 1 – budżet obywatelski, albo część 2 – z punktów z Excela),
**kopia pliku**, tryb zgód „pytaj" albo „akceptuj" – świadomie.

## Problem, który to rozwiązuje

Slajdy są gotowe, a wystąpienie nie. Co powiedzieć przy każdym slajdzie,
w jakiej kolejności, jak przejść do następnego – to zwykle wieczór
przed prezentacją i kartka z punktami. PowerPoint ma na to miejsce od
lat: **pole notatek** pod slajdem, widoczne w widoku prezentera na
Waszym ekranie, niewidoczne dla sali. Claude potrafi je wypełnić dla
całej prezentacji naraz – a Wy robicie to, czego on nie zrobi: sprawdzacie
fakty i mówicie swoim głosem.

## Materiały

- Prezentacja z zadania 2 (kopia, np. `budzet_obywatelski_zad3.pptx`).
- Do kroku 6: dowolna **istniejąca** prezentacja bez notatek – np.
  `../../day-1/day1-claude.pptx` (materiał szkoleniowy, jawny).

## Kroki

1. **Sprawdźcie, że notatek nie ma.** *Widok → Normalny*, na dole okna
   przycisk **Notatki** – pole pod slajdem jest puste. Zapamiętajcie, jak
   je włączyć: tam będziecie sprawdzać wynik.
2. **Jedno polecenie** (można głosem): *„Dodaj notatki prelegenta do
   każdego slajdu."* Nic więcej – najpierw zobaczcie, co Claude zrobi z
   samym tym zdaniem. Obserwujcie panel: powinien napisać, że dopisuje
   notatki **do slajdów** (edycja pliku), a nie tylko wypisać je w
   rozmowie. Jeśli tylko wypisał – dopowiedzcie: *„Wpisz je w pole
   notatek każdego slajdu w tym pliku."*
3. **Kontrola miejsca.** Po zakończeniu: slajd 1 → pole **Notatki** na
   dole – ma być tekst. Przejdźcie strzałkami przez wszystkie slajdy:
   każdy ma notatkę? Ostatni też? (Typowe potknięcie: notatki na 5 z 6
   slajdów.) Alternatywnie *Widok → Strona notatek* – widać slajd i
   notatkę razem, jak na wydruku dla prelegenta.
4. **Kontrola treści – najważniejszy krok.** Przeczytajcie notatki do
   slajdu 1 i jednego ze środkowych. Zaznaczcie każdą **liczbę, datę,
   nazwę i twierdzenie, którego nie ma na slajdzie**. Claude dopisuje
   je z wiedzy ogólnej – brzmią wiarygodnie („zwykle 70–80 %…", „w
   większości miast…"), ale nie pochodzą z Waszych źródeł. Zasada:
   **do notatek wchodzi tylko to, co umiecie obronić** – resztę
   usuńcie albo każcie usunąć: *„Usuń z notatek wszystkie liczby i
   fakty, których nie ma na slajdach; zostaw tylko omówienie treści
   slajdu i przejście do następnego."*
5. **Dopasowanie.** Trzy krótkie polecenia, każde osobno, żeby widzieć
   efekt:
   - **czas**: *„Skróć notatki tak, żeby każdy slajd zajmował ok. 45
     sekund mówienia (ok. 90 słów)."* – 6 slajdów × 45 s = wystąpienie
     na 5 minut, typowy limit w punkcie sesji Rady;
   - **głos**: *„Przepisz notatki w pierwszej osobie, tonem rzeczowym,
     bez zwrotów typu 'ekscytujący', 'przełomowy'."* – notatki mają
     brzmieć jak Wy, nie jak reklama;
   - **przejścia**: *„Na końcu każdej notatki dodaj jedno zdanie
     przejścia do następnego slajdu."*
6. **Istniejąca prezentacja.** Otwórzcie **kopię** `day1-claude.pptx`
   (albo własną jawną prezentację), włączcie panel, tryb „pytaj", i
   powtórzcie krok 2. To scenariusz z życia: prezentacja sprzed roku,
   zrobiona przez kogoś innego, a jutro macie ją omawiać. Sprawdźcie,
   czy notatki trzymają się tego, co jest na slajdach – przy cudzych
   slajdach Claude ma większą pokusę „dopowiadania".
7. **Inny język / inny odbiorca (opcjonalnie).** *„Przetłumacz notatki
   na angielski, zachowując slajdy po polsku."* (delegacja partnerska)
   albo *„Przepisz notatki do slajdów 2–4 dla mieszkańców bez wiedzy
   o finansach publicznych, bez skrótów i żargonu."* Zobaczcie, że
   slajdy zostają nietknięte – zmieniają się tylko notatki.

## Na co zwrócić uwagę

- **Notatki to najłatwiejsze miejsce na nieprawdę.** Nikt na sali ich
  nie widzi, więc nikt ich nie zweryfikuje przed Wami – a Wy je
  **wypowiecie**. Każda liczba w notatce, której nie ma na slajdzie ani
  w Waszym źródle, to ryzyko powiedzenia na sesji czegoś, czego nie da
  się obronić. Krok 4 jest obowiązkowy, zawsze.
- **Notatka ≠ scenariusz do przeczytania.** Dobre notatki to 3–5 zdań:
  o czym jest slajd, jedna rzecz do podkreślenia, przejście. Jeśli
  Claude napisał akapit na pół strony – skróćcie (krok 5). Czytanie
  z notatek słowo w słowo słychać.
- **Widok prezentera.** `Alt + F5` uruchamia pokaz z notatkami na
  Waszym ekranie i samymi slajdami na rzutniku. Sprawdźcie to **przed**
  wystąpieniem – w sali 0.05 z jednym ekranem notatki trzeba wydrukować
  (*Plik → Drukuj → Strony notatek*).
- **Tryb zgód – jak w zadaniu 2.** Dopisywanie notatek nie rusza
  slajdów, ale to nadal edycja pliku. Na cudzej / ważnej prezentacji:
  kopia + „pytaj".
- **Copilot robi to samo.** Jeśli macie Copilota w PowerPoincie, ta
  funkcja też tam jest – na innych modelach i na umowie Microsoftu.
  Zasada danych (Dzień 1, Blok B) dotyczy obu: notatki do prezentacji
  z realnymi kwotami Urzędu = te kwoty u dostawcy.
- **Tłumaczenie notatek to nie tłumaczenie prezentacji.** Przy
  delegacji zagranicznej często wystarczy: slajdy po polsku (dla
  protokołu), notatki po angielsku (dla Was). Tańsze i bezpieczniejsze
  niż tłumaczenie całego pliku.

## Notatki własne

- Ile faktów/liczb spoza slajdów znaleźliście w notatkach z kroku 4?
- Które z trzech dopasowań (czas / głos / przejścia) najbardziej
  zmieniło jakość notatek?
- Najbliższe Wasze wystąpienie: ile slajdów, ile minut – i ile słów na
  slajd z tego wynika?
