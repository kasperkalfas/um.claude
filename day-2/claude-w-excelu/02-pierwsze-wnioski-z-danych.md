# Zadanie 2: „Daj mi ogólne wnioski" – pierwsza analiza danych w Excelu i jej kontrola

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
**Dzień 2, Blok B: Praca na komórkach i strukturze danych w Excelu**;
kontynuacja [zadania 1](01-claude-w-excelu-instalacja.md)).

**Cel:** jednym zdaniem po polsku uzyskać od Claude przegląd zbioru
1 470 pracowników (co w nim jest, jakie liczby, co z nich wynika) – a
potem **sprawdzić trzy liczby z tego przeglądu formułami w Excelu**,
bo Claude potrafi podać podsumowanie brzmiące pewnie i błędne.
**Poziom:** podstawowy
**Czas:** ok. 15 minut (analiza 3–4 min, kontrola ~8 min)
**Wymaga:** dodatek Claude w Excelu (zadanie 1), otwarty
`Human_Resources.xlsx`, model Opus.

## Problem, który to rozwiązuje

Dostajecie nowy arkusz – 35 kolumn, półtora tysiąca wierszy. Zanim
cokolwiek policzycie, chcecie wiedzieć: co tu jest, czy są braki, jakie
są typowe wartości i **co z tego wynika**. Analityk robi to w godzinę
(tabele przestawne, kilka wykresów). Claude w panelu robi to w kilka
minut – tylko trzeba umieć odróżnić, kiedy ma rację, a kiedy pewnym
tonem opowiada bzdury.

## O danych – dwa zdania kontekstu

Każdy wiersz to pracownik; kolumna `Attrition` mówi, czy **odszedł
z firmy** (`Yes`) czy został (`No`). Dla działu kadr to pytanie za
duże pieniądze: rekrutacja nowej osoby kosztuje więcej niż zatrzymanie
obecnej, więc warto wiedzieć, **kto jest zagrożony odejściem i dlaczego**
(nadgodziny? staż? wynagrodzenie? podróże?). Reszta kolumn to potencjalne
przyczyny. W urzędzie to samo pytanie brzmi: „którzy pracownicy odchodzą
i co możemy z tym zrobić" – dane byłyby inne, mechanika identyczna.

## Materiały

- `Human_Resources.xlsx` otwarty w Excelu, panel Claude po prawej
  (zadanie 1). Zapiszcie kopię pliku – w tym zadaniu Claude tylko czyta,
  ale nawyk jest nawykiem.
- Klucz odpowiedzi dla prowadzącego – w sekcji „Na co zwrócić uwagę".

## Kroki

1. **Jedno zdanie.** W panelu wpiszcie:
   *„Podaj ogólne wnioski z tych danych."*
   Nic więcej – bez opisu kolumn, bez tłumaczenia, co to `Attrition`.
   Chodzi o to, ile Claude sam wyciągnie z nagłówków i wartości.
2. **Obserwujcie panel.** Claude najpierw **czyta cały arkusz**
   (zobaczycie komunikaty w rodzaju „czytam nagłówki", „czytam
   wiersze 1–1470"), potem **pisze i uruchamia kod** w Pythonie do
   analizy (rozwińcie „pokaż więcej" – nie musicie go rozumieć, ale
   warto wiedzieć, że liczby nie biorą się „z głowy" modelu, tylko z
   obliczeń na Waszych danych). Trwa to 2–4 minuty na Opusie.
3. **Przeczytajcie wynik.** Typowa odpowiedź ma trzy części:
   - **przegląd**: liczba wierszy i kolumn, braki danych, typowe
     wartości (średni wiek, mediana wynagrodzenia, struktura działów);
   - **liczby o odejściach**: ogólny odsetek, kto odchodzi częściej;
   - **wnioski „do działania"**: 3–5 punktów w stylu „nadgodziny to
     główny czynnik odejść", „stanowisko X wymaga uwagi".
4. **Kontrola – trzy liczby formułami.** W wolnym miejscu arkusza (np.
   kolumna `AK`) policzcie samodzielnie, **bez Claude**:
   - odsetek odejść: `=LICZ.JEŻELI(C:C;"Yes")/LICZ.JEŻELI(C:C;"<>")`
     (kolumna `C` = `Attrition`; w nagłówku też jest tekst, więc
     odejmijcie 1 od mianownika albo policzcie na `C2:C1471`);
   - braki danych: `=LICZ.PUSTE(A2:AI1471)` – ile pustych komórek w
     całym zakresie;
   - medianę wynagrodzenia: `=MEDIANA(B2:B1471)`.
   Porównajcie z tym, co napisał Claude. **Jeśli któraś liczba się nie
   zgadza – nie poprawiajcie Claude, zapiszcie rozbieżność.** To jest
   najważniejszy wynik tego zadania.
5. **Dopytajcie o jeden wniosek.** Wybierzcie punkt „do działania", który
   brzmi najmocniej (np. o nadgodzinach), i zapytajcie:
   *„Skąd ten wniosek? Podaj liczby: ile osób z nadgodzinami odeszło, a
   ile bez, i jaki to procent w każdej grupie."*
   Sprawdźcie jedną z tych liczb tabelą przestawną (Wstawianie → Tabela
   przestawna: wiersze `OverTime`, kolumny `Attrition`, wartości –
   licznik). Zgadza się?
6. **Poproście o wersję dla przełożonego.** *„Streść to w 5 punktach po
   polsku, dla naczelnika wydziału kadr, bez żargonu, każdy punkt z jedną
   liczbą."* – to będzie surowiec do notatki lub slajdu.

## Na co zwrócić uwagę

- **Claude potrafi się mylić w podsumowaniu, mimo że liczył kodem.**
  Najczęstsze pułapki: podaje odsetek z jednej podgrupy jako ogólny
  (np. odsetek odejść wśród osób z nadgodzinami zamiast w całej firmie),
  albo pisze „brak braków danych", bo sprawdził tylko część kolumn.
  Dlatego krok 4 jest obowiązkowy – **trzy formuły to 2 minuty**, a
  ratują przed wysłaniem błędnej liczby dalej.
- **Klucz odpowiedzi (dla prowadzącego):** 1 470 wierszy × 35 kolumn;
  **odejścia 16,1 %** (237 z 1 470); **braki danych: 13 pustych komórek
  w 7 wierszach** (wiersz 8 ma ich 7); średni wiek 36,9; wynagrodzenie
  miesięczne: średnia 6 505, **mediana 4 908**; nadgodziny: odchodzi
  **30,5 %** osób z nadgodzinami vs 10,4 % bez; `Sales Representative`
  odchodzi 39,8 % (33 z 83) – najwięcej ze wszystkich stanowisk; brak
  opcji na akcje (`StockOptionLevel` 0): 24,4 % odejść vs 7,6–9,4 % przy
  poziomie 1–2; częste podróże: 24,9 % vs 8,0 % bez podróży; single
  25,5 %; poziom stanowiska 1: 26,3 %; mediana wynagrodzenia
  odchodzących 3 187 vs 5 206 zostających.
- **Wnioski ≠ przyczyny.** „Osoby z nadgodzinami odchodzą 3× częściej"
  to fakt z danych. „Nadgodziny powodują odejścia" to hipoteza – może
  być odwrotnie (osoby, które i tak chcą odejść, dostają gorsze
  grafiki). Claude formułuje wnioski w trybie przyczynowym; Wy w
  notatce dla przełożonego piszcie w trybie „współwystępuje".
- **Kod, którego nie widać, też liczy się do okna kontekstu** (Dzień 1).
  Cały arkusz został wczytany do rozmowy – 1 470 × 35 komórek to
  kilkadziesiąt tysięcy tokenów. Kolejne pytania w tej samej rozmowie
  są tańsze (dane już są w oknie), ale nowa rozmowa zaczyna od zera.
- **Dane osobowe – raz jeszcze.** Ten zbiór ma numery zamiast nazwisk i
  jest wymyślony. Prawdziwe zestawienie kadrowe Urzędu z tym samym
  poleceniem to przekazanie danych osobowych dostawcy – bez pisemnej
  zgody Zamawiającego nie wolno (Dzień 1, Blok B), a RODO ma tu
  zastosowanie niezależnie od umowy.

## Notatki własne

- Które z trzech liczb z kroku 4 zgadzały się z podsumowaniem Claude, a
  które nie?
- Jaki był najmocniej sformułowany wniosek i jak brzmiałby po
  przepisaniu na „współwystępuje"?
- Gdyby to były dane Waszego wydziału: które 3 kolumny chcielibyście
  mieć, a których nie wolno by Wam było wprowadzić?
