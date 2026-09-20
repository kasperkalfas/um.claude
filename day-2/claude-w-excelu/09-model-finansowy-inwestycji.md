# Zadanie 9: Model finansowy z założeń – czy termomodernizacja szkoły się opłaca i jak ją spłacić

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
**Dzień 2, Blok B: Praca na komórkach i strukturze danych w Excelu**;
kontynuacja [zadania 8](08-braki-danych.md)).

**Cel:** z jednego arkusza założeń (nakład, dotacja, oszczędności
energii, stopa dyskontowa, warunki kredytu) zbudować w Excelu – jednym,
dobrze ułożonym poleceniem – **działający model**: zdyskontowane
oszczędności rok po roku, wartość bieżąca netto (NPV), okres zwrotu,
harmonogram spłaty kredytu i tabelę wrażliwości. Model ma składać się
z **formuł odwołujących się do komórek z założeniami**, tak żeby zmiana
jednej liczby przeliczała wszystko. Na koniec: to samo polecenie w
Claude Czat z załączonym plikiem – żeby zobaczyć, czym różnią się obie
drogi.
**Poziom:** średni
**Czas:** ok. 20 minut
**Wymaga:** dodatek Claude w Excelu, `materialy/termomodernizacja_zalozenia.xlsx`
(kopia), model **Opus** – to zadanie ma wiele kroków zależnych od
siebie; dostęp do Claude Czat (krok 6).

## Problem, który to rozwiązuje

Wydział Finansowy dostaje od wydziału inwestycji kosztorys i audyt
energetyczny, od banku ofertę kredytu, od instytucji dotującej – procent
dofinansowania. Pytania Skarbnika: *czy to się zwraca, w ile lat, ile
wyniesie rata, co jeśli energia podrożeje wolniej, co bez dotacji* – i
te same liczby trafiają potem do wieloletniej prognozy finansowej i do
banku (Proces 2). Zwykle to arkusz budowany od zera, po godzinach, z
formułami, które za rok nikt nie pamięta. Claude buduje taki arkusz w
kilka minut – **jeśli** dostanie założenia w jednym miejscu i polecenie,
które mówi, co ma powstać.

## Materiały

- `materialy/termomodernizacja_zalozenia.xlsx` – jeden arkusz
  `Zalozenia`, 11 pozycji w `A5:D15` (fikcyjna Szkoła Podstawowa
  nr 99): nakład 4 200 000 zł, dotacja 45 %, oszczędność energii
  310 000 zł w roku 1 rosnąca 4 %/rok, serwis 15 000 zł rosnący 3 %,
  horyzont 15 lat, stopa dyskontowa 6 %, wartość rezydualna 20 %
  nakładu, kredyt 5,5 % na 10 lat w ratach równych.
  `generuj_termomodernizacja.py` odtwarza plik i wypisuje klucz.
- Minimum teorii (tyle, ile trzeba, żeby sprawdzić Claude):
  - **Dyskontowanie**: 310 000 zł oszczędzone za rok jest dziś warte
    mniej niż 310 000 zł – przy stopie 6 % dokładnie
    `310 000 / 1,06 = 292 453`. Za dwa lata: `/ 1,06²`, itd. Stopa
    dyskontowa to tu **koszt długu gminy** – tyle kosztuje pieniądz,
    którym finansujecie wkład własny.
  - **NPV** (wartość bieżąca netto) = suma zdyskontowanych oszczędności
    netto + zdyskontowana wartość rezydualna − wkład własny. Dodatnia
    = inwestycja zwraca więcej, niż kosztuje pieniądz.
  - **Wartość rezydualna**: po 15 latach ocieplony budynek nadal ma
    wartość – przyjmujemy 20 % nakładu i też dyskontujemy.
  - **Rata równa** (annuitetowa) kredytu to w Excelu `=PMT(...)`.

## Kroki

1. **Otwórzcie plik i przeczytajcie założenia z Claude.** *„Co jest w
   tym arkuszu? Wypisz założenia z adresami komórek."* Sprawdźcie, czy
   Claude odróżnia procenty (`B6` = 45 %) od kwot (`B5` = 4 200 000) i
   czy zauważył zdanie w `A18` (wkład własny finansowany kredytem).
2. **Polecenie – cztery części.** Wklejcie w panel (po zaznaczeniu
   „Akceptuj wszystkie edycje" albo z zatwierdzaniem – jak wolicie):

   > **Kontekst:** Jesteś analitykiem w Wydziale Finansowym Urzędu
   > Miasta. Wydział inwestycji przedstawił termomodernizację budynku
   > szkoły; Skarbnik ma ocenić, czy inwestycja się zwraca i jak
   > obciąży budżet spłata kredytu na wkład własny. Wynik trafi do
   > wieloletniej prognozy finansowej i do banku.
   >
   > **Instrukcje:** Zbuduj w nowym arkuszu `Model` w pełni dynamiczny
   > model na podstawie założeń z arkusza `Zalozenia`:
   > 1. wkład własny gminy = nakład − dofinansowanie;
   > 2. tabela lat 1–15: oszczędność energii (rosnąca o wzrost cen),
   >    koszt serwisu (rosnący o swój wzrost), oszczędność netto,
   >    współczynnik dyskontowy, wartość bieżąca oszczędności netto;
   > 3. wartość rezydualna po roku 15 i jej wartość bieżąca;
   > 4. NPV dla gminy = suma wartości bieżących + zdyskontowana wartość
   >    rezydualna − wkład własny; prosty okres zwrotu wkładu (rok, w
   >    którym skumulowane oszczędności netto przekraczają wkład); IRR;
   > 5. w arkuszu `Kredyt`: harmonogram spłaty wkładu własnego w 10
   >    ratach rocznych równych (PMT): rata, odsetki, kapitał, saldo;
   >    suma odsetek;
   > 6. w arkuszu `Model`: tabela wrażliwości NPV dla stopy dyskontowej
   >    4 / 6 / 8 / 10 % i wzrostu cen energii 0 / 2 / 4 / 6 %.
   >
   > **Wejście:** arkusz `Zalozenia` (A5:D15). Każda liczba w modelu ma
   > być **formułą odwołującą się do komórek założeń** – nie wpisuj
   > wyników jako liczb. Nie zmieniaj arkusza `Zalozenia`.
   >
   > **Wyjście:** arkusze `Model` i `Kredyt` z podstawowym formatowaniem
   > (nagłówki, format walutowy bez groszy, procenty), sekcja
   > „Podsumowanie" na górze `Model` z NPV, okresem zwrotu, IRR i ratą
   > roczną – z linkami do komórek.

   Obserwujcie plan, który Claude wypisuje przed pracą – ma odpowiadać
   punktom 1–6. Potem kilka minut budowy.
3. **Klucz – Podsumowanie.** Kliknijcie linki:
   - wkład własny: **2 310 000 zł**;
   - suma wartości bieżących oszczędności netto (lata 1–15):
     **3 677 245 zł**; PV wartości rezydualnej: **350 503 zł**;
   - **NPV ≈ 1 717 748 zł** (dodatnia);
   - prosty okres zwrotu: **7 lat**; IRR ≈ **14,1 %**;
   - rata roczna kredytu: **306 463 zł**, odsetki razem ≈ **754 625 zł**.
   Pierwszy wiersz tabeli: rok 1 – oszczędność 310 000, serwis 15 000,
   netto 295 000, współczynnik 0,9434, PV **278 302**. Jeśli PV roku 1
   wynosi 292 453 – Claude zdyskontował oszczędność brutto, bez
   serwisu. Jeśli 295 000 – nie zdyskontował wcale.
4. **Test „formuła, nie liczba" – trzy zmiany w `Zalozenia`.**
   - Dotacja `B6`: 45 % → **0 %**. NPV ma spaść do ok. **−172 000 zł**
     (ujemna – bez dofinansowania inwestycja nie broni się przy tej
     stopie), rata do ok. 557 000 zł. Wróćcie do 45 %.
   - Stopa `B12`: 6 % → 10 %. NPV ≈ **696 000 zł**. Wróćcie.
   - Wzrost cen energii `B8`: 4 % → 0 %. NPV ≈ **876 000 zł**. Wróćcie.
   Jeśli któraś liczba w `Model` **nie drgnęła** – jest wpisana na
   sztywno. Poproście: *„Które komórki w Model i Kredyt nie są
   formułami? Zamień je na formuły."*
5. **Tabela wrażliwości.** Sprawdźcie narożniki: 4 % / 0 % →
   **1 400 748**; 10 % / 6 % → **1 060 418**; środek 6 % / 4 % → ta sama
   liczba co NPV w Podsumowaniu. Zapytajcie: *„Jak zbudowałeś tabelę
   wrażliwości – tabelą danych Excela czy osobnymi formułami?"* Obie
   odpowiedzi są poprawne; tabela danych (*Dane → Analiza warunkowa*)
   przelicza się wolniej, ale jest odporna na przebudowę modelu.
6. **Ta sama praca w Claude Czat.** Otwórzcie claude.ai, nowa rozmowa,
   załączcie **oryginalny** `termomodernizacja_zalozenia.xlsx` i wklejcie
   **to samo polecenie** z kroku 2. Claude uruchomi kod, zbuduje plik i
   da go do pobrania. Porównajcie:
   - NPV powinno wyjść to samo (± zaokrąglenia);
   - w dodatku model powstał **w Waszym otwartym pliku**, z linkami do
     komórek; w czacie dostajecie **nowy plik** – bez linków, ale za
     to z pełnym opisem, co i jak policzono, i możliwością dalszej
     rozmowy o wyniku;
   - obie drogi liczą kodem po stronie dostawcy – dane opuszczają
     komputer w obu przypadkach.
   Trzecia droga – Claude Code na plikach w folderze – to ścieżka z
   [`../../day-1/claude-code-cli/`](../../day-1/claude-code-cli/README.md).
7. **Pytanie Skarbnika.** *„W dwóch zdaniach dla Skarbnika: czy
   rekomendujesz inwestycję i przy jakich założeniach przestaje się
   opłacać?"* Dobra odpowiedź nazywa **próg** (bez dotacji NPV ujemne;
   przy stopie 10 % i stałych cenach energii NPV ≈ 115 000 zł – blisko
   zera), a nie tylko powtarza „NPV dodatnie". Odpowiedź to punkt
   wyjścia, nie rekomendacja – rekomendację podpisuje człowiek.

## Na co zwrócić uwagę

- **Polecenie w czterech częściach – kontekst, instrukcje, wejście,
  wyjście – to nie ozdoba.** Bez „każda liczba formułą" dostaniecie
  ładną tabelę z wpisanymi wynikami; bez „nie zmieniaj Zalozenia"
  Claude może „poprawić" założenia; bez listy 1–6 pominie tabelę
  wrażliwości. Ten sam szablon działa w czacie, w dodatku i w Claude
  Code – zapiszcie go sobie.
- **Sprawdzajcie jeden wiersz ręcznie.** Rok 1 z klucza (278 302 zł)
  liczy się na kalkulatorze w 20 sekund: `(310 000 − 15 000) / 1,06`.
  Jeśli rok 1 się zgadza, a formuły ciągną się w dół – reszta zwykle
  też. Jeśli nie – nie czytajcie dalej, poprawcie najpierw to.
- **Założenia są Wasze, arytmetyka jest Claude.** Stopa 6 %, wzrost
  cen 4 %, rezydualna 20 % – każde z nich zmienia NPV o setki tysięcy
  (tabela wrażliwości). Claude ich nie zweryfikuje; do tego jest audyt
  energetyczny, oferta banku i doświadczenie Wydziału. Model bez
  arkusza założeń z podanym **źródłem** każdej liczby (kolumna `D`) to
  model, którego za rok nikt nie obroni.
- **NPV to jedna miara, nie decyzja.** Gmina nie kupuje szkoły dla
  zysku: dochodzą obowiązki wobec uczniów, limity zadłużenia,
  harmonogram innych inwestycji, ryzyko wykonawcy. Model odpowiada na
  „czy oszczędności pokryją koszt pieniądza", nie na „czy robić".
- **Rata ≈ oszczędność.** W tym przykładzie rata roczna (306 tys.) jest
  prawie równa oszczędności netto roku 1 (295 tys.) – przez pierwsze
  lata inwestycja jest dla budżetu bieżącego niemal neutralna, potem
  oszczędności rosną, a rata nie. To jest zdanie, które trafia do
  prezentacji w Dniu 3, nie tabela.
- **Wpisane liczby to dług techniczny.** Model, w którym część
  komórek jest formułą, a część liczbą, jest gorszy niż model bez
  formuł – bo **wygląda** na dynamiczny. Test z kroku 4 (zmień
  założenie, patrz co się rusza) róbcie na każdym arkuszu, który
  dostaniecie od Claude – i od człowieka.
- **Dane fikcyjne, szablon prawdziwy.** Polecenie z kroku 2 i układ
  `Zalozenia → Model → Kredyt` możecie przenieść na realną inwestycję –
  ale realny kosztorys, oferta banku i dane szkoły to informacje
  Urzędu; do dodatku i czatu tylko za pisemną zgodą (Blok B Dnia 1).
  Alternatywa bez wysyłania danych: zbudować model na fikcyjnych
  liczbach, a realne **wpisać samodzielnie** do `Zalozenia` po
  zamknięciu panelu.

## Notatki własne

- Czy plan wypisany przez Claude przed budową miał wszystkie sześć
  punktów?
- Które komórki (jeśli jakieś) okazały się liczbami zamiast formuł w
  kroku 4?
- Która inwestycja z Waszej prognozy wieloletniej zasługuje na taki
  model jako pierwsza – i skąd wzięlibyście każde z 11 założeń?
