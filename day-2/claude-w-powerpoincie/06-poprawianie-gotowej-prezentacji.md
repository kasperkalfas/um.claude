# Zadanie 6: Poprawianie gotowej prezentacji słowami – tytuł z tezą, ikona, slajd bez ściany tekstu (i liczby, które muszą przeżyć)

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
**Dzień 2**, ścieżka „Claude w PowerPoincie"; kontynuacja
[zadania 5](05-prezentacja-w-szablonie-urzedu.md); pierwsze zadanie na
**prezentacji z liczbami** – zapowiedź Dnia 3, Bloków B–C i DataPOV).

**Cel:** wziąć **istniejącą**, przeciętną prezentację o wykonaniu
budżetu (5 slajdów: tytuł, ściana tekstu, tabela, wypunktowanie,
wnioski) i poprawić ją trzema poleceniami po polsku – bez dotykania
myszy: (1) tytuł, który mówi, co wynika z danych, (2) ikona na slajdzie
tytułowym, (3) slajd 2 z 46 liczb w jednym akapicie → układ wizualny.
Potem sprawdzić to, czego nie widać na pierwszy rzut oka: **czy wszystkie
liczby przetrwały przeróbkę** i czy wnioski nadal zgadzają się z danymi.
**Poziom:** średni
**Czas:** ok. 25 minut
**Wymaga:** dodatek Claude w PowerPoincie, tryb zgód „pytaj" (kroki
2–4) – zobaczycie, co Claude chce zmienić, zanim to zrobi; model Opus
(praca na układzie slajdu wymaga kilku rund „zrzut ekranu → poprawka →
zrzut ekranu"). Kopia `materialy/wykonanie_budzetu_2026_8m.pptx` (np.
`wykonanie_budzetu_zad6.pptx`).

## Problem, który to rozwiązuje

Prezentacje dla Komisji Budżetowej, Rady i banku powstają zwykle tak:
ktoś wkleja akapit ze sprawozdania na slajd, dodaje tabelę i pisze
„Wnioski". Nikt tego nie czyta – czyta się tytuł i patrzy na obrazki.
Zbudowanie slajdu od nowa zajmuje godzinę; **poprawienie** go z Claude
– kilka minut. Ale przeróbka wizualna to moment, w którym liczby
najłatwiej znikają albo zmieniają się „po drodze" – a w materiale dla
Rady każda liczba jest sprawdzalna.

## Materiały

- `materialy/wykonanie_budzetu_2026_8m.pptx` – 5 slajdów, dane
  fikcyjne (wykonanie wydatków wg 8 działów po 8 miesiącach 2026 r.,
  te same liczby co w `zestawienie_roczne_2026.xlsx` ze ścieżki Claude Code).
  `materialy/generuj_prezentacja.py` odtwarza plik i wypisuje **klucz**:
  wszystkie 46 liczb ze slajdu 2 i wnioski, które z nich wynikają.
- Klucz w skrócie: plan 157 500 000 zł, wykonanie 101 984 000 zł
  (64,8 % przy upływie 66,7 % roku), prognoza roczna 152 976 000 zł
  (**−2,9 %** do planu); prognoza **powyżej** planu w dwóch działach:
  **750** Administracja (+0,8 %) i **851** Ochrona zdrowia (+1,5 %);
  największe niedowykonanie **926** Kultura fizyczna (−6,0 %), największa
  kwota **801** Oświata (−1 814 000 zł).

## Kroki

1. **Przeczytajcie prezentację z Claude, zanim cokolwiek zmienicie.**
   *„Przeczytaj tę prezentację i powiedz w trzech zdaniach, co z niej
   wynika dla Komisji Budżetowej."* Dobra odpowiedź: prognoza −2,9 % do
   planu, dwa działy nad planem, wykonanie poniżej proporcji roku. Jeśli
   Claude powtórzy tylko tytuły slajdów – to znaczy, że prezentacja
   **nie ma tezy**. Bo nie ma.
2. **Tytuł z tezą (DataPOV).** *„Nie podoba mi się tytuł. Zamień go na
   jedno zdanie, które mówi, co wynika z danych – tak, żeby radny, który
   zobaczy tylko pierwszy slajd, znał wniosek. Podtytuł zostaw."*
   Klucz: tytuł ma zawierać **liczbę i kierunek**, np. „Budżet 2026 po
   8 miesiącach: prognoza 2,9 % poniżej planu, dwa działy wymagają
   korekty". Odrzućcie tytuły typu „Budżet 2026 – nowa perspektywa" –
   ładne, puste. Tytuł nie ma być „bardziej nowoczesny", ma być
   **prawdziwy i sprawdzalny** w tabeli na slajdzie 3.
3. **Ikona – i sprawdzian, czy Claude widzi slajd.** *„Dodaj na slajdzie
   tytułowym prostą ikonę budynku urzędu albo wykresu, po lewej stronie
   tytułu, w kolorze pasującym do reszty. Nie zasłaniaj tekstu."*
   Obserwujcie panel: Claude po zmianie **robi zrzut ekranu slajdu**,
   ogląda go i poprawia położenie/odstępy, jeśli coś nachodzi. To jest
   pętla „zrób → zobacz → popraw" – ten sam mechanizm, którym w
   [`../claude-w-excelu/`](../claude-w-excelu/04-wykresy-w-excelu.md)
   sprawdzał wykres, a w zadaniu 2 – każdy nowy slajd. Jeśli ikona zasłania tytuł, nie
   przesuwajcie jej ręcznie – powiedzcie: *„Ikona zasłania drugą linię
   tytułu, przesuń ją albo zmniejsz."*
4. **Slajd 2: ściana tekstu → układ wizualny.** *„Slajd 2 to jeden
   akapit z 46 liczbami – nikt tego nie przeczyta. Przebuduj go: osiem
   kart (po jednej na dział) z kodem, nazwą, % wykonania planu i
   odchyleniem prognozy od planu; działy z prognozą powyżej planu
   wyróżnij kolorem. Plan, wykonanie i prognozę w złotych przenieś do
   notatek prelegenta. Nie zmieniaj żadnej liczby."*
   Claude będzie pracował kilka minut i kilka razy poprawiał układ
   („karta nachodzi na kartę", „tekst nie mieści się w karcie") – to
   normalne. Poczekajcie na komunikat, że skończył i sprawdził slajd.
5. **Kontrola liczb – obowiązkowa.** Otwórzcie klucz z
   `generuj_prezentacja.py` (albo slajd 3 z tabelą, którego nie
   ruszaliście) i sprawdźcie **każdą** z 16 liczb na nowych kartach
   (8 × % planu, 8 × odchylenie) oraz to, czy w notatkach są kwoty.
   Typowe usterki, których szukacie:
   - zaokrąglenie zmieniło wartość (63,4 % → 63 %; −2,9 % → −3 %) – w
     materiale dla Rady to zmiana liczby, nie kosmetyka;
   - znak zniknął (+0,8 % zapisane jako 0,8 %) albo kolor „ponad plan"
     trafił na dział pod planem;
   - dwie karty zamieniły się nazwami (kod 852 z liczbami działu 851);
   - liczba **dopisana** „dla ozdoby" (np. „ok. 65 %" w nagłówku), której
     nie ma w źródle.
   Jeśli znajdziecie choć jedną – *„Na karcie 851 odchylenie ma być
   +1,5 %, nie 1,5 %. Popraw i sprawdź pozostałe karty względem
   slajdu 3."*
6. **Wnioski, które przeczą danym.** Slajd 5 zaczyna się od „Wykonanie
   wydatków przebiega zgodnie z planem" – a prognoza jest −2,9 % i dwa
   działy są nad planem. Zapytajcie: *„Czy wnioski na slajdzie 5 zgadzają
   się z liczbami na slajdach 2–4? Wskaż niezgodności, nie poprawiaj."*
   Klucz: pierwsze zdanie jest nieprawdziwe (albo przynajmniej
   nieprecyzyjne), „w dwóch działach" nie nazywa działów, „monitorowanie"
   nie jest rekomendacją. Dopiero po tej odpowiedzi: *„Przepisz slajd 5
   na trzy wnioski z liczbą i jedną rekomendację z terminem."*
7. **Wasze 20 %.** Zapiszcie plik pod nową nazwą i wprowadźcie
   samodzielnie jedną rzecz, której Claude nie wie: nazwę komisji, datę
   posiedzenia, herb w stopce, kolor z identyfikacji Urzędu. Claude robi
   80 % – układ, ikony, przepisanie; 20 % to Wasza wiedza o odbiorcy i
   podpis pod liczbami.

## Na co zwrócić uwagę

- **Tytuł to teza, nie temat.** „Informacja o wykonaniu budżetu" to
  temat; „prognoza 2,9 % poniżej planu, dwa działy nad planem" to teza.
  To sedno DataPOV (Dzień 3, Blok A) w jednym zdaniu: odbiorca ma
  poznać wniosek, zanim zobaczy dane. Claude na prośbę „lepszy tytuł" da tytuł
  **efektowniejszy**; o tezę trzeba poprosić wprost.
- **Przeróbka wizualna to najczęstsze miejsce utraty liczb.** Model
  przepisuje tekst na karty – i po drodze zaokrągla, gubi znak, dokłada
  liczbę „z głowy". Nawyk: po każdej przeróbce slajdu z liczbami –
  kontrola względem źródła (Excel albo nietknięty slajd z tabelą).
  46 liczb ręcznie to 3 minuty; jedna zła liczba przed Radą to
  posiedzenie.
- **Slajd 3 (tabela) celowo zostawiliście nietknięty** – to Wasze
  źródło prawdy w pliku. W realnym materiale rolę tę pełni
  `zestawienie_roczne` (Proces 2), a prezentacja (Proces 3) ma być z nim
  zgodna co do grosza.
- **Kolor „ponad plan" to decyzja, nie ozdoba.** Wyróżnienie 750 i 851
  mówi Komisji, gdzie patrzeć. Jak w
  [`../claude-w-excelu/07`](../claude-w-excelu/07-formatowanie-warunkowe.md):
  to Wy decydujecie, co jest na czerwono – Claude wykona polecenie dosłownie, także złe.
- **Kwoty w notatkach, nie na slajdzie** – slajd ma 16 liczb zamiast 46,
  a pełne kwoty są w notatkach prelegenta i w tabeli. Rada dostaje
  wydruk z tabelą; na ekranie ma widzieć wniosek.
- **Claude ogląda slajd jak człowiek** (zrzut ekranu → ocena → poprawka),
  dlatego układ zwykle wychodzi porządnie, ale kilka rund trwa. Mówcie
  o usterkach tak, jak powiedzielibyście grafikowi: „karta 926 wystaje
  poza slajd", nie „popraw".
- **Dane fikcyjne, prezentacja realna w formie.** Ten sam tok – tytuł z
  tezą, karty zamiast akapitu, kontrola liczb, wnioski z liczbą – stosuje
  się do prawdziwego materiału. Prawdziwy plik z wykonaniem budżetu to
  informacja publiczna po uchwaleniu, ale **robocze** prognozy i
  materiały dla banku przed publikacją – tylko za zgodą (Blok B Dnia 1).

## Notatki własne

- Czy Claude w kroku 1 podał tezę, czy streścił slajdy?
- Ile z 16 liczb na kartach było błędnych po pierwszej przeróbce?
- Który slajd z Waszej ostatniej prezentacji dla Rady jest „ścianą
  tekstu" – i jaka jest jego teza?
