# Zadanie 4: Nowy slajd z podanego źródła i zmiana tonu dla innego odbiorcy

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
**Dzień 2**, ścieżka „Claude w PowerPoincie"; kontynuacja
[zadania 3](03-notatki-prelegenta.md)).

**Cel:** dwie typowe poprawki „po pierwszej wersji": (1) dołożyć jeden
slajd na podstawie **wskazanej strony internetowej** – w stylu reszty
prezentacji, z notatką i źródłem; (2) przepisać **jeden slajd i jego
notatkę** pod zupełnie innego odbiorcę, nie ruszając pozostałych. Po
drodze: jak sprawdzić liczby, które Claude wyciągnął ze strony.
**Poziom:** podstawowy
**Czas:** ok. 12 minut
**Wymaga:** dodatek Claude w PowerPoincie, prezentacja z zadań 2–3
(budżet obywatelski, z notatkami), **kopia**, tryb zgód „pytaj".

## Problem, który to rozwiązuje

Prezentacja jest „prawie gotowa", a potem: „dołóż slajd o tym, co
ogłosili w zeszłym tygodniu" albo „to samo, ale dla młodzieży / dla
Rady / dla banku". W klasycznym PowerPoincie to kopiowanie stylu z
sąsiedniego slajdu i przepisywanie tekstu od zera. Tu mówicie, **co**
ma się zmienić i **skąd** wziąć treść – a styl i układ Claude bierze z
tego, co już jest w pliku.

## Materiały

- Kopia prezentacji z zadań 2–3 (np. `budzet_obywatelski_zad4.pptx`).
- **Jawne źródło** do kroku 1 – jedna publiczna strona, np.:
  - ustawa o samorządzie gminnym w ISAP (art. 5a – budżet obywatelski):
    `https://isap.sejm.gov.pl/isap.nsf/DocDetails.xsp?id=WDU19900160095`
  - albo strona miasta / BIP z zasadami aktualnej edycji budżetu
    obywatelskiego (publiczna, więc wolno ją podać).
  **Nie** podajemy linków do dokumentów wewnętrznych ani do plików na
  dysku Urzędu.

## Kroki

1. **Slajd ze źródła.** W panelu:
   *„Dodaj po slajdzie 3 jeden slajd o podstawie prawnej budżetu
   obywatelskiego, na podstawie tej strony: [link]. Zachowaj styl
   reszty prezentacji, dodaj notatkę prelegenta i podaj źródło na dole
   slajdu."*
   Obserwujcie panel: Claude **pobiera stronę**, wyciąga z niej treść
   (artykuł, terminy, progi), wstawia slajd w tym samym motywie, pisze
   notatkę i **sam sprawdza** nowy slajd (czy tekst się mieści, czy
   czcionka nie jest za mała). Trwa 1–3 minuty.
2. **Kontrola liczb ze strony – obowiązkowa.** Otwórzcie źródło w
   przeglądarce i porównajcie **każdą liczbę i każdy cytat** ze slajdu
   z oryginałem: numer artykułu, procent, termin, kwota. Claude
   streszcza dobrze, ale potrafi: zaokrąglić, wziąć liczbę z innego
   akapitu, zlepić dwa zdania w jedno „cytowanie". Jeśli coś się nie
   zgadza – *„Na nowym slajdzie popraw X na Y, zgodnie ze źródłem."*
3. **Przypis źródła.** Sprawdźcie, że na dole slajdu jest źródło
   (nazwa + adres, ewentualnie data dostępu). Jeśli Claude wpisał tylko
   „Źródło: internet" – *„Wpisz pełny adres strony i dzisiejszą datę
   jako datę dostępu."* Na prezentacji dla Rady przypis to nie
   ozdoba – to odpowiedź na pytanie „skąd Pani to ma?".
4. **Zmiana tonu jednego slajdu.** *„Przepisz **tylko slajd 1** i jego
   notatkę prelegenta dla uczniów szkół średnich (Młodzieżowa Rada
   Miasta): energiczny język, krótkie zdania, bez urzędowych zwrotów.
   Pozostałych slajdów nie zmieniaj."*
   Claude wyczyści slajd 1 i zbuduje go na nowo – inny tytuł, inny
   układ, czasem inna grafika – a potem przepisze notatkę. Sprawdźcie
   dwie rzeczy: (a) slajdy 2–7 są **nietknięte** (porównajcie z kopią),
   (b) notatka do slajdu 1 rzeczywiście zmieniła ton, a nie tylko
   slajd.
5. **W drugą stronę.** *„Teraz przepisz slajd 1 i notatkę w tonie
   formalnym, dla sesji Rady Miasta: pełne zdania, bez wykrzykników,
   bez kolokwializmów."* Porównajcie trzy wersje slajdu 1 (oryginał z
   kopii, młodzież, Rada). Ta sama treść, trzy różne prezentacje –
   różni je wyłącznie odbiorca. To jest punkt wyjścia DataPOV w Dniu 3.
6. **Granica.** Zapytajcie: *„Które sformułowania z wersji dla
   młodzieży byłyby niestosowne w piśmie urzędowym i dlaczego?"* –
   dobra odpowiedź pokaże, że Claude rozróżnia rejestry; a Wy
   zapiszecie, gdzie dla Was przebiega granica „energicznie" vs
   „niepoważnie".

## Na co zwrócić uwagę

- **Link ≠ prawda.** Claude pobrał stronę i streścił ją – ale to Wy
  odpowiadacie za każdą liczbę na slajdzie. Kontrola ze źródłem (krok
  2) to 2 minuty; brak kontroli to ryzyko przytoczenia na sesji
  „art. 5a ust. 7", który mówi coś innego.
- **Tylko jawne źródła.** Publiczna strona, BIP, ISAP, komunikat prasowy
  – tak. Link do dokumentu na SharePoincie Urzędu, do skanu pisma, do
  wewnętrznej notatki – **nie** bez pisemnej zgody (Dzień 1, Blok B).
  Zasada obejmuje też „wklej treść strony" – jeśli nie jest publiczna,
  nie wchodzi do okna kontekstu.
- **„Tylko slajd 1" trzeba powiedzieć wprost.** Bez tego Claude może
  „ujednolicić" całą prezentację. Zakres zmiany zawsze nazywajcie:
  numer slajdu, elementy (tytuł / treść / notatka), czego nie ruszać.
  Kopia pliku sprzed zmiany to Wasz dowód, co się zmieniło.
- **Ton to decyzja o odbiorcy, nie o ozdobnikach.** Wersja dla
  młodzieży nie jest „gorsza", wersja dla Rady nie jest „lepsza" –
  każda jest właściwa dla swojej sali. Ale w urzędzie granica
  stosowności jest bliżej niż w firmie: krok 6 ma ją nazwać.
- **Nowy slajd dostaje własną notatkę** – w tonie reszty prezentacji.
  Po zmianie tonu slajdu 1 notatki 2–7 nadal są w starym tonie:
  spójność między slajdami a notatkami to Wasza kontrola przed
  wystąpieniem (zadanie 3, krok 4).
- **Wszystko edytowalne.** Slajd ze źródła i przebudowany slajd 1 to
  zwykłe obiekty PowerPointa; drobiazgi (za mała czcionka w przypisie,
  wyrównanie) szybciej poprawić ręcznie.

## Notatki własne

- Ile liczb/cytatów ze slajdu ze źródła zgadzało się z oryginałem, a ile
  wymagało poprawki?
- Czy po kroku 4 slajdy 2–7 na pewno pozostały bez zmian?
- Gdzie dla Was przebiega granica tonu „energicznego" w materiale
  sygnowanym przez Urząd?
