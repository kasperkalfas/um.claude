# Zadanie 9: Model finansowy z założeń – czy termomodernizacja szkoły się opłaca

**Dzień 2, Blok B** · ok. 20 min · dodatek Claude w Excelu, kopia
`materialy/termomodernizacja_zalozenia_zad9.xlsx` (zapisana z
[`materialy/termomodernizacja_zalozenia.xlsx`](materialy/termomodernizacja_zalozenia.xlsx)), model **Opus**; Claude Czat
do kroku 6.

**Cel:** z arkusza założeń zbudować jednym poleceniem model (NPV, okres
zwrotu, IRR, harmonogram kredytu, tabela wrażliwości) **wyłącznie z
formuł** odwołujących się do założeń.

**Założenia** (`Zalozenia`, `A5:D15`, fikcyjna SP nr 99): nakład
4 200 000 zł, dotacja 45 %, oszczędność energii 310 000 zł/rok +4 %/rok,
serwis 15 000 zł +3 %/rok, horyzont 15 lat, stopa 6 %, wartość rezydualna
20 % nakładu, kredyt 5,5 % / 10 lat / raty równe.
[`materialy/generuj_termomodernizacja.py`](materialy/generuj_termomodernizacja.py) odtwarza plik i wypisuje klucz.

**Minimum teorii:** dyskontowanie – 310 000 zł za rok jest dziś warte
`310 000 / 1,06 = 292 453`; NPV = suma zdyskontowanych oszczędności netto
+ zdyskontowana rezydualna − wkład własny; rata równa = `PMT`.

## Polecenia

### 1. Założenia oczami Claude

> Co jest w tym arkuszu? Wypisz założenia z adresami komórek.

Sprawdź: odróżnia procenty (`B6` = 45 %) od kwot (`B5` = 4 200 000);
zauważył `A18` (wkład własny finansowany kredytem).

### 2. Polecenie w czterech częściach

> **Kontekst:** Jesteś analitykiem w Wydziale Finansowym Urzędu Miasta.
> Wydział inwestycji przedstawił termomodernizację budynku szkoły; Skarbnik
> ma ocenić, czy inwestycja się zwraca i jak obciąży budżet spłata kredytu
> na wkład własny. Wynik trafi do wieloletniej prognozy finansowej i do
> banku.
>
> **Instrukcje:** Zbuduj w nowym arkuszu `Model` w pełni dynamiczny model
> na podstawie założeń z arkusza `Zalozenia`:
> 1. wkład własny gminy = nakład − dofinansowanie;
> 2. tabela lat 1–15: oszczędność energii (rosnąca o wzrost cen), koszt
>    serwisu (rosnący o swój wzrost), oszczędność netto, współczynnik
>    dyskontowy, wartość bieżąca oszczędności netto;
> 3. wartość rezydualna po roku 15 i jej wartość bieżąca;
> 4. NPV dla gminy = suma wartości bieżących + zdyskontowana wartość
>    rezydualna − wkład własny; prosty okres zwrotu wkładu (rok, w którym
>    skumulowane oszczędności netto przekraczają wkład); IRR;
> 5. w arkuszu `Kredyt`: harmonogram spłaty wkładu własnego w 10 ratach
>    rocznych równych (PMT): rata, odsetki, kapitał, saldo; suma odsetek;
> 6. w arkuszu `Model`: tabela wrażliwości NPV dla stopy dyskontowej
>    4 / 6 / 8 / 10 % i wzrostu cen energii 0 / 2 / 4 / 6 %.
>
> **Wejście:** arkusz `Zalozenia` (A5:D15). Każda liczba w modelu ma być
> **formułą odwołującą się do komórek założeń** – nie wpisuj wyników jako
> liczb. Nie zmieniaj arkusza `Zalozenia`.
>
> **Wyjście:** arkusze `Model` i `Kredyt` z podstawowym formatowaniem
> (nagłówki, format walutowy bez groszy, procenty), sekcja „Podsumowanie"
> na górze `Model` z NPV, okresem zwrotu, IRR i ratą roczną – z linkami do
> komórek.

Plan wypisany przed pracą ma odpowiadać punktom 1–6.

### 3. Klucz – Podsumowanie

| Pozycja | Klucz |
|---|---|
| wkład własny | **2 310 000 zł** |
| suma PV oszczędności netto (1–15) | 3 677 245 zł |
| PV wartości rezydualnej | 350 503 zł |
| **NPV** | **≈ 1 717 748 zł** |
| prosty okres zwrotu | **7 lat** |
| IRR | **≈ 14,1 %** |
| rata roczna | **306 463 zł** (odsetki razem ≈ 754 625) |

Rok 1: 310 000 − 15 000 = 295 000; × 0,9434 = **278 302**. Jeśli 292 453 –
zdyskontował brutto bez serwisu; jeśli 295 000 – nie zdyskontował.

### 4. Test „formuła, nie liczba" – trzy zmiany w `Zalozenia`

| Zmiana | NPV ma wynieść |
|---|---|
| `B6` dotacja 45 % → **0 %** | ≈ **−172 000** (rata ≈ 557 000) |
| `B12` stopa 6 % → 10 % | ≈ 696 000 |
| `B8` wzrost cen 4 % → 0 % | ≈ 876 000 |

Wracajcie do wartości wyjściowej po każdej próbie. Jeśli coś nie drgnęło:

> Które komórki w Model i Kredyt nie są formułami? Zamień je na formuły.

### 5. Tabela wrażliwości

Narożniki: 4 % / 0 % → **1 400 748**; 10 % / 6 % → **1 060 418**; środek
6 % / 4 % = NPV z Podsumowania.

> Jak zbudowałeś tabelę wrażliwości – tabelą danych Excela czy osobnymi
> formułami?

Obie odpowiedzi poprawne.

### 6. To samo w Claude Czat

claude.ai → nowa rozmowa → załącznik: **oryginalny**
[`materialy/termomodernizacja_zalozenia.xlsx`](materialy/termomodernizacja_zalozenia.xlsx) → to samo polecenie z kroku 2.
Porównajcie: NPV to samo (± zaokrąglenia); dodatek buduje **w Waszym
pliku** z linkami, czat oddaje **nowy plik** z opisem obliczeń – pobrany zapiszcie w
`materialy/`, nie w *Pobranych*. Dane
opuszczają komputer w obu przypadkach.

### 7. Pytanie Skarbnika

> W dwóch zdaniach dla Skarbnika: czy rekomendujesz inwestycję i przy jakich
> założeniach przestaje się opłacać?

Dobra odpowiedź nazywa **próg** (bez dotacji NPV ujemne; 10 % i stałe ceny
energii → NPV ≈ 115 000, blisko zera). Rekomendację podpisuje człowiek.

## Pamiętaj

- Cztery części polecenia (kontekst / instrukcje / wejście / wyjście) to
  nie ozdoba: bez „każda liczba formułą" dostaniecie wpisane wyniki, bez
  „nie zmieniaj Zalozenia" Claude „poprawi" założenia, bez listy 1–6
  pominie tabelę wrażliwości. Ten sam szablon działa w czacie, dodatku i
  Claude Code.
- Sprawdzajcie **jeden wiersz ręcznie** (rok 1 – 20 sekund na kalkulatorze).
- Założenia są Wasze – Claude ich nie zweryfikuje. Kolumna `D` (źródło
  każdej liczby) to obrona modelu za rok.
- Rata (306 tys.) ≈ oszczędność netto roku 1 (295 tys.) – zdanie na slajd
  w Dniu 3, nie tabela.
- Realny kosztorys i oferta banku – tylko za zgodą. Alternatywa: model na
  fikcyjnych liczbach, realne wpisać po zamknięciu panelu.
