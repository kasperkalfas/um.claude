# Zadanie 7: Proces 2 – powtarzalny „przepis" z miesięcznego do rocznego

**Cel:** zbudować z Claude Code powtarzalny przepis (prompt + skrypt),
który przenosi wykonanie z zestawienia miesięcznego (Plik 1) do właściwej
kolumny zestawienia rocznego (Plik 2), aktualizuje prognozę dla banku i
sam sprawdza, czy sumy się zgadzają. Raz przygotowany – uruchamiany co
miesiąc zamiast ręcznego przepisywania.
**Poziom:** średni → zaawansowany
**Czas:** ok. 40 minut
**Blok:** Dzień 1 — automatyzacja procesu

## Materiały

- `zestawienie_miesieczne_SZABLON.xlsx` wypełniony w zadaniu 6 (wrzesień,
  D6:D13 = sumy wg działów).
- `zestawienie_roczne_2026.xlsx` – miesiące I–VIII wypełnione, IX pusty;
  arkusz `Prognoza` z `B2 = 8` (liczba miesięcy z danymi).
- Klucz odpowiedzi – [README](README.md#klucz-odpowiedzi).

## Kroki

1. `cd C:\Szkolenie\dzien-1\praca`, `claude`, kopie obu plików do `kopie`.

### Część 1: Najpierw ręcznie – jeden raz, żeby wiedzieć, co ma robić skrypt

2. *„Przenieś wartości z `zestawienie_miesieczne_SZABLON.xlsx`,
   `Zestawienie!D6:D13` do `zestawienie_roczne_2026.xlsx`, arkusz
   `Wykonanie`, kolumna miesiąca wrzesień (L6:L13). Dopasuj po kodzie
   działu w kolumnie A obu plików. Zanim zapiszesz, pokaż tabelę: dział,
   wartość źródłowa, komórka docelowa."*
3. *„W arkuszu `Prognoza` zmień B2 z 8 na 9."*
4. *„Uzupełnij w szablonie miesięcznym kolumnę E (Wykonanie narastająco)
   sumą miesięcy I–IX z pliku rocznego dla każdego działu."*
5. Otwórz oba pliki w Excelu i sprawdź: `Wykonanie!L14` = 13 230 000 zł;
   `Prognoza` przeliczyła się (średnia = narastająco / 9); w szablonie
   kolumna F pokazuje % wykonania (np. dział 600: 17 357 000 / 24 000 000
   = 72,3%). Zamknij pliki.

### Część 2: Zamień to w przepis

6. *„Cofnij zmiany z Części 1: wyczyść L6:L13, ustaw `Prognoza!B2` = 8,
   wyczyść E6:E13 w szablonie."* (Albo przywróć z `kopie`.) Przepis
   testujemy na czystym stanie.
7. *„Napisz skrypt `proces2.py`, który przyjmuje jako parametr nazwę
   miesiąca po polsku (np. `wrzesień`) i:
   1) robi kopie obu plików do `kopie` z datą i godziną,
   2) czyta D6:D13 z szablonu miesięcznego,
   3) wpisuje je do właściwej kolumny miesiąca w `Wykonanie` (wrzesień = L,
      październik = M itd.), dopasowując po kodzie działu,
   4) ustawia `Prognoza!B2` na numer miesiąca,
   5) uzupełnia E6:E13 w szablonie sumą miesięcy od stycznia do tego
      miesiąca,
   6) na końcu wypisuje kontrolę: suma D w szablonie, suma wpisanej
      kolumny w rocznym, i OK/BŁĄD, jeśli się różnią.
   Nie nadpisuj kolumny, która już ma dane – zatrzymaj się i zapytaj.
   Wyjaśnij mi po polsku, co robi każdy fragment."*
8. Przeczytaj wyjaśnienie. Nie musisz rozumieć Pythona – musisz rozumieć
   **kroki** i **warunki** (kiedy skrypt się zatrzyma).
9. *„Uruchom `proces2.py wrzesień`."* Sprawdź w Excelu to samo, co w
   kroku 5. Wynik kontroli w terminalu: OK?

### Część 3: Test odporności

10. *„Uruchom jeszcze raz `proces2.py wrzesień`."* – kolumna L ma już
    dane, więc skrypt powinien **odmówić** i zapytać. Jeśli nadpisał bez
    pytania – *„Popraw: przed zapisem sprawdzaj, czy kolumna jest pusta"*.
11. *„Uruchom `proces2.py grudzień`"* – szablon ma dane września, więc
    wpisanie ich do grudnia byłoby błędem. Czy skrypt to wyłapie (B2 w
    szablonie mówi »wrzesień«)? Jeśli nie: *„Dodaj kontrolę: nazwa
    miesiąca w parametrze musi zgadzać się z B2 w szablonie"*.
12. Przywróć stan z kroku 9 (wrzesień wpisany, grudzień pusty).

## Na co zwrócić uwagę

- **Najpierw raz ręcznie, potem skrypt.** Dopóki sam(a) nie wiesz
  dokładnie, które komórki dokąd idą, nie da się tego dobrze opisać
  Claude'owi – ani sprawdzić, czy skrypt robi to samo.
- **Kontrola sum w skrypcie to nie dodatek, to sedno.** Ręczne
  przepisywanie nie ma wbudowanej kontroli; skrypt ma – i to jest główna
  przewaga, większa niż oszczędność czasu.
- Warunki „zatrzymaj się i zapytaj" (kolumna niepusta, zły miesiąc) to
  Wasze bezpieczniki. Wymyślcie własne: np. suma w szablonie równa zero,
  brak któregoś działu, plik roczny otwarty w Excelu.
- Skrypt jest plikiem w folderze roboczym – możesz go pokazać IT,
  zarchiwizować, poprosić Claude o zmianę za miesiąc. To nie jest „czarna
  skrzynka".

## Notatki własne

- Czy kontrola sum wypisała OK za pierwszym razem?
- Który „bezpiecznik" z Części 3 zadziałał, a który trzeba było dopisać?
- Jakie warunki zatrzymania dodałbyś/dodałabyś dla prawdziwego Pliku 2?
