# Zadanie 1: Claude w Excelu – instalacja dodatku i pierwsze uruchomienie

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
**Dzień 2, Blok B: Praca na komórkach i strukturze danych w Excelu** –
wariant „Claude bezpośrednio w arkuszu", uzupełniający Claude Code).

**Cel:** dodać Claude do własnego Excela jako dodatek, zalogować się
kontem Urzędu, wybrać model – i zobaczyć, że od tej chwili Claude „widzi"
otwarty arkusz bez wgrywania pliku do czatu.
**Poziom:** podstawowy
**Czas:** ok. 10 minut (instalacja 3 min, reszta – pierwszy kontakt)
**Wymaga:** Excel z pakietu Microsoft 365 (desktop na Windows albo Excel
w przeglądarce), konto Claude w planie Team Urzędu, dostęp do sklepu
dodatków Office (jeśli zablokowany – patrz „Na co zwrócić uwagę").

## Problem, który to rozwiązuje

W Dniu 1 Claude dostawał Excela na dwa sposoby: **wgrany do czatu**
(kopia pliku wędruje do przeglądarki) albo **czytany przez Claude Code**
skryptem z dysku. Oba działają, ale oba są „obok" Excela. Dodatek
**Claude w Excelu** siedzi w panelu bocznym otwartego skoroszytu: widzi
arkusze, zakresy i formuły, pisze do komórek, poprawia formuły – bez
przełączania okien i bez wysyłania pliku ręcznie. To najkrótsza droga dla
osoby, która i tak spędza dzień w Excelu.

## Materiały

- Kopia `materialy/Human_Resources.xlsx` na Pulpicie – fikcyjny,
  anglojęzyczny zbiór kadrowy: 1 470 pracowników (numer zamiast
  nazwiska), 35 kolumn (wiek, dział, stanowisko, wynagrodzenie
  miesięczne, nadgodziny, lata pracy, oceny, odejścia z firmy
  `Attrition`…). Kilka komórek jest celowo pustych – klucz w README
  folderu.
- Login i hasło do konta Claude w organizacji Urzędu.

> **Jedyny plik, jaki otwieracie z włączonym dodatkiem, to plik
> fikcyjny.** Dodatek wysyła zawartość arkusza do Anthropic tak samo jak
> wklejenie jej do czatu. Realne zestawienia kadrowe czy budżetowe Urzędu
> – wyłącznie po pisemnej zgodzie Zamawiającego (zasada z Dnia 1, Blok B).
> Na czas ćwiczeń zamknijcie wszystkie inne skoroszyty.

## Kroki

1. **Otwórzcie** `Human_Resources.xlsx` w Excelu. Rzućcie okiem na
   arkusz `Human_Resources`: 35 kolumn, 1 470 wierszy, nagłówki po
   angielsku. Nic więcej na razie nie róbcie – to za dużo, żeby czytać
   ręcznie, i o to chodzi.
2. **Dodatki.** Na wstążce znajdźcie przycisk **Dodatki** (Add-ins) –
   w Excelu 365 zwykle po prawej stronie karty *Narzędzia główne* albo
   na karcie *Wstawianie → Pobierz dodatki*. Kliknijcie.
3. **Wyszukajcie** `Claude`. Na liście powinna pojawić się pozycja
   **Claude by Anthropic** (w opisie: *Claude in Excel*). Kliknijcie
   **Dodaj**. Instalacja trwa kilkanaście sekund; potem na wstążce
   pojawia się ikona Claude, a po prawej stronie – panel boczny.
4. **Zalogujcie się** w panelu kontem Claude Urzędu (to samo, którym
   logowaliście się do czatu i Cowork). Jeśli byliście już zalogowani w
   przeglądarce, panel może połączyć się od razu.
5. **Wybierzcie model** na górze panelu. Do ćwiczeń: najmocniejszy
   dostępny (**Opus**) – najlepiej radzi sobie z formułami i strukturą
   arkusza, kosztem większego zużycia limitu. Do drobnych pytań
   („co jest w B7?") wystarczy **Sonnet**. Zmiana modelu to jedno
   kliknięcie, więc nie ma złej decyzji – jest za droga.
6. **Pierwszy kontakt** – w panelu wpiszcie po polsku, bez wgrywania
   czegokolwiek:
   *„Co jest w tym arkuszu? Opisz po polsku grupy kolumn, liczbę
   wierszy i do czego ten plik może służyć."*
   Claude powinien odpowiedzieć z **odwołaniami do konkretnych
   komórek i zakresów** (np. `A2:AI1471`, kolumna `B` = wynagrodzenie
   miesięczne, `C` = czy pracownik odszedł) i pogrupować 35 kolumn w
   sensowne bloki (dane osobowe bez nazwisk, stanowisko, wynagrodzenie,
   satysfakcja, staż). To różnica wobec czatu: dodatek nie zgaduje z
   kopii, tylko czyta otwarty skoroszyt. **Sprawdzian:** zapytajcie
   *„ile wierszy ma zakres danych?"* – poprawna odpowiedź: 1 470.
7. **Zapisane w panelu podpowiedzi** (np. *buduj model finansowy*,
   *uporządkuj bałagan w danych*, *znajdź błąd w formule*) – przejrzyjcie,
   ale nie klikajcie jeszcze niczego, co zmienia komórki. Zmiany w
   arkuszu to zadanie 2.

## Na co zwrócić uwagę

- **Dodatek widzi tylko otwarty skoroszyt** – nie dysk, nie inne pliki.
  Do pracy na kilku plikach naraz (Proces 1 → Proces 2) nadal lepszy
  jest Claude Code (Blok C). Dodatek jest od pracy *w* arkuszu.
- **Panel boczny to ta sama rozmowa co w czacie** – z tymi samymi
  limitami planu Team, tym samym oknem kontekstu (Dzień 1, folder
  „tokeny i okno kontekstu") i tą samą zasadą: to, co Claude czyta z
  arkusza, opuszcza Wasz komputer.
- **Jeśli przycisku Dodatki nie ma albo sklep jest pusty**, to nie błąd
  Claude – administrator Microsoft 365 w Urzędzie blokuje dodatki ze
  sklepu. Poproście IT o dopuszczenie dodatku *Claude by Anthropic* dla
  Waszej grupy. Warto to zgłosić **przed** Dniem 2, nie w trakcie.
- **Model = koszt i jakość.** Opus do ćwiczeń i do formuł; Sonnet do
  pytań. Zużycie limitu widać w ustawieniach konta Claude (jak w Cowork:
  *Settings → Usage*).
- **Nic się jeszcze nie zmieniło w pliku.** W tym zadaniu Claude tylko
  czyta. Zanim w zadaniu 2 pozwolicie mu pisać do komórek – zapiszcie
  kopię pliku (nawyk z Dnia 1: kopia przed zmianą).

## Notatki własne

- Czy dodatek zainstalował się od razu, czy potrzebna była zgoda IT?
- Które odwołania do komórek w odpowiedzi Claude z kroku 6 były trafne,
  a które nie? Czy podał 1 470 wierszy?
- Do którego z Waszych codziennych arkuszy najbardziej chcielibyście
  mieć taki panel obok – i czy ten arkusz zawiera dane, których do Claude
  wprowadzać nie wolno?
