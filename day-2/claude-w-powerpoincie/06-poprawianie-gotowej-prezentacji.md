# Zadanie 6: Poprawianie gotowej prezentacji słowami – tytuł z tezą, ikona, slajd bez ściany tekstu

**Dzień 2** · ok. 25 min · dodatek Claude w PowerPoincie, tryb „pytaj",
model Opus; kopia `materialy/wykonanie_budzetu_2026_8m.pptx` (np.
`wykonanie_budzetu_zad6.pptx`). Pierwsze zadanie na **prezentacji z
liczbami** – most do DataPOV (Dzień 3).

**Cel:** poprawić przeciętną prezentację o wykonaniu budżetu (5 slajdów)
trzema poleceniami – i sprawdzić, **czy wszystkie liczby przetrwały**.

**Klucz** (`materialy/generuj_prezentacja.py` wypisuje pełny): plan
157 500 000 zł, wykonanie 101 984 000 zł (64,8 % przy 66,7 % roku),
prognoza 152 976 000 zł (**−2,9 %**); nad planem **750** Administracja
(+0,8 %) i **851** Ochrona zdrowia (+1,5 %); największe niedowykonanie
**926** (−6,0 %), największa kwota **801** Oświata (−1 814 000 zł).

## Polecenia

### 1. Przeczytajcie z Claude, zanim coś zmienicie

> Przeczytaj tę prezentację i powiedz w trzech zdaniach, co z niej wynika
> dla Komisji Budżetowej.

Dobra odpowiedź: −2,9 %, dwa działy nad planem, wykonanie poniżej
proporcji roku. Jeśli powtórzy tytuły slajdów – prezentacja **nie ma tezy**.

### 2. Tytuł z tezą (DataPOV)

> Nie podoba mi się tytuł. Zamień go na jedno zdanie, które mówi, co wynika
> z danych – tak, żeby radny, który zobaczy tylko pierwszy slajd, znał
> wniosek. Podtytuł zostaw.

Klucz: **liczba i kierunek**, np. „Budżet 2026 po 8 miesiącach: prognoza
2,9 % poniżej planu, dwa działy wymagają korekty". Odrzućcie „Budżet 2026 –
nowa perspektywa".

### 3. Ikona – i sprawdzian, czy Claude widzi slajd

> Dodaj na slajdzie tytułowym prostą ikonę budynku urzędu albo wykresu, po
> lewej stronie tytułu, w kolorze pasującym do reszty. Nie zasłaniaj
> tekstu.

Claude robi zrzut slajdu, ogląda, poprawia (pętla zrób → zobacz → popraw).
Jeśli nachodzi – nie przesuwajcie ręcznie:

> Ikona zasłania drugą linię tytułu, przesuń ją albo zmniejsz.

### 4. Slajd 2: ściana tekstu → karty

> Slajd 2 to jeden akapit z 46 liczbami – nikt tego nie przeczyta.
> Przebuduj go: osiem kart (po jednej na dział) z kodem, nazwą, % wykonania
> planu i odchyleniem prognozy od planu; działy z prognozą powyżej planu
> wyróżnij kolorem. Plan, wykonanie i prognozę w złotych przenieś do
> notatek prelegenta. Nie zmieniaj żadnej liczby.

Kilka minut i kilka rund poprawek układu – normalne.

### 5. Kontrola liczb – obowiązkowa

Względem klucza albo nietkniętego slajdu 3 (tabela) sprawdźcie **16 liczb**
(8 × % planu, 8 × odchylenie) i kwoty w notatkach. Szukajcie:
zaokrąglenia (63,4 % → 63 %), zgubionego znaku (+0,8 % → 0,8 %), koloru na
złym dziale, zamienionych kart (852 ↔ 851), liczby **dopisanej** („ok.
65 %").

> Na karcie 851 odchylenie ma być +1,5 %, nie 1,5 %. Popraw i sprawdź
> pozostałe karty względem slajdu 3.

### 6. Wnioski, które przeczą danym

> Czy wnioski na slajdzie 5 zgadzają się z liczbami na slajdach 2–4?
> Wskaż niezgodności, nie poprawiaj.

Klucz: „zgodnie z planem" jest nieprawdziwe przy −2,9 %; „w dwóch
działach" nie nazywa działów; „monitorowanie" to nie rekomendacja. Dopiero
potem:

> Przepisz slajd 5 na trzy wnioski z liczbą i jedną rekomendację z
> terminem.

### 7. Wasze 20 %

Nowa nazwa pliku; ręcznie: nazwa komisji, data posiedzenia, herb w
stopce, kolor Urzędu. Claude robi 80 % (układ, ikony, przepisanie); 20 %
to wiedza o odbiorcy i podpis pod liczbami.

## Pamiętaj

- **Tytuł to teza, nie temat.** Na „lepszy tytuł" Claude da tytuł
  efektowniejszy; o tezę trzeba poprosić wprost.
- Przeróbka wizualna to najczęstsze miejsce utraty liczb. Po każdej –
  kontrola względem źródła. 46 liczb to 3 minuty; jedna zła przed Radą to
  posiedzenie.
- Slajd 3 (tabela) celowo nietknięty – źródło prawdy w pliku. W realnym
  Procesie 3 tę rolę pełni `zestawienie_roczne`.
- Kolor „ponad plan" to decyzja, nie ozdoba – jak w
  [`../claude-w-excelu/07`](../claude-w-excelu/07-formatowanie-warunkowe.md).
- Mówcie o usterkach jak grafikowi: „karta 926 wystaje poza slajd", nie
  „popraw".
- Robocze prognozy i materiały dla banku przed publikacją – tylko za
  zgodą.
