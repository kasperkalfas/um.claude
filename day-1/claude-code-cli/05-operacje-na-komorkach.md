# Zadanie 5: Operacje na komórkach w języku naturalnym

**Cel:** wykonywać konkretne operacje na komórkach i zakresach – odczyt,
wpis, formuła, przeniesienie między arkuszami i plikami, formatowanie –
mówiąc po polsku, bez formuł i bez makr. To „słownik" poleceń, z którego
skorzystacie w zadaniach 6–7.
**Poziom:** średni
**Czas:** ok. 30 minut
**Blok:** Dzień 1 — praca na komórkach

## Materiały

- `zestawienie_roczne_2026.xlsx` (Plik 2) i `zestawienie_miesieczne_SZABLON.xlsx`
  (Plik 1) w folderze roboczym. Pliki **zamknięte** w Excelu.

## Kroki

1. `cd C:\Szkolenie\dzien-1\praca`, `claude`. Na początek:
   *„Skopiuj oba pliki xlsx do `kopie` z datą i godziną w nazwie."*

### Część 1: Odczyt i zapis pojedynczych komórek

2. *„W `zestawienie_roczne_2026.xlsx`, arkusz `Wykonanie`: jaka wartość
   jest w komórce K8 i co ona oznacza (który dział, który miesiąc)?"*
3. *„Wpisz do komórki L6 wartość 2 150 000 (to wykonanie działu 600 za
   wrzesień). Nie zmieniaj niczego innego."* Otwórz plik: czy P6 (Razem) i
   Q6 (% planu) przeliczyły się same? Zamknij plik.
4. *„Cofnij: wyczyść L6."*

### Część 2: Formuły

5. *„W arkuszu `Wykonanie` dodaj w komórce R5 nagłówek »Średnia I–VIII«, a
   w R6:R13 formułę liczącą średnią z kolumn D–K dla każdego wiersza.
   Format walutowy jak w kolumnie P."*
6. Otwórz plik i kliknij R6 – powinna tam być **formuła** (`=AVERAGE(D6:K6)`
   lub `=ŚREDNIA(...)`), nie wpisana liczba. Jeśli jest liczba:
   *„Zamień na formułę, nie na wartość"*. Zamknij plik.
7. *„Czy w tym arkuszu są komórki z formułami, które zwracają błąd albo
   odwołują się do pustych zakresów?"*

### Część 3: Przenoszenie między arkuszami i plikami

8. *„Porównaj plan roczny w `Wykonanie!C6:C13` z planem w
   `zestawienie_miesieczne_SZABLON.xlsx`, arkusz `Zestawienie`, C6:C13 –
   dopasowując po kodzie działu z kolumny A, nie po kolejności. Wypisz
   tabelę: dział, plan w rocznym, plan w szablonie, różnica. Jeśli
   czegoś brakuje w szablonie – uzupełnij z pliku rocznego."*
   Dobra odpowiedź: Claude najpierw porównuje kody działów, potem
   wartości. W czystych plikach plany są identyczne – to celowe: ćwiczymy
   nawyk „najpierw porównaj, potem przenoś", który w zadaniu 7 chroni
   przed przesunięciem o wiersz.
9. *„Wpisz w szablonie miesięcznym B2 = »wrzesień«."*
10. *„Przepisz z pliku rocznego do szablonu miesięcznego, kolumna E
    (Wykonanie narastająco), sumę miesięcy I–VIII dla każdego działu."*
    Zauważ: to dokładnie ruch „z Pliku 2 do Pliku 1", tylko w drugą
    stronę niż zwykle. W zadaniu 7 zrobimy właściwy kierunek.

### Część 4: Formatowanie

11. *„W szablonie miesięcznym: kolumny C–E format `# ##0 zł` bez miejsc
    po przecinku, kolumna F procent z jednym miejscem, nagłówki
    pogrubione, szerokość kolumn dopasuj do treści."*
12. *„Sprawdź, czy w obu plikach wszystkie daty są w formacie
    RRRR-MM-DD, a kwoty są liczbami, nie tekstem. Wypisz wyjątki."*

## Na co zwrócić uwagę

- **Adresy komórek działają najlepiej.** „Wpisz do L6" jest jednoznaczne;
  „wpisz wrzesień dla transportu" wymaga, żeby Claude sam znalazł wiersz
  i kolumnę – zwykle mu się udaje, ale każ pokazać, gdzie wpisze.
- **Formuła kontra wartość** – zawsze mów, czego chcesz. Wartość „zamraża"
  liczbę; formuła przelicza się po zmianie danych. W zestawieniach dla
  banku chcecie formuł.
- Excel po polsku pokazuje `=SUMA`, Claude zapisuje `=SUM` – to ta sama
  formuła, Excel ją przetłumaczy przy otwarciu.
- Claude zapisuje plik przez Python: **utracone mogą być** rzadkie
  elementy (makra, niektóre wykresy, sprawdzanie poprawności). Dla
  Waszych zestawień to zwykle nie problem – ale to kolejny powód, by mieć
  kopię.

## Notatki własne

- Które polecenie Claude wykonał inaczej, niż się spodziewałeś/aś?
- Które operacje z Procesu 1 / Procesu 2 dałoby się już teraz zapisać
  jako listę takich poleceń?
