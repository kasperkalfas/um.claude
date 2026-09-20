# Zadanie 8: Kolejny miesiąc od początku do końca + raport kontrolny

**Cel:** przejść cały cykl miesięczny (Proces 1 → Proces 2) dla
października na czystym eksporcie, używając przepisów z zadań 6 i 7 –
i dołożyć raport kontrolny, który porównuje miesiąc do miesiąca i do
planu. To symulacja „zamknięcia miesiąca" w wersji, która pokaże, czy
przepisy naprawdę są powtarzalne.
**Poziom:** zaawansowany
**Czas:** ok. 30 minut
**Blok:** Dzień 1 — automatyzacja procesu (lub praca własna)

## Materiały

- `eksport_erp_2026-10.csv` – czysty eksport za październik (bez pułapek).
- `zestawienie_miesieczne_SZABLON.xlsx` – ze wrześniem (z zad. 6–7).
- `zestawienie_roczne_2026.xlsx` – z wpisanym wrześniem (z zad. 7).
- `przepis_proces1.md` i `proces2.py` z poprzednich zadań.

## Kroki

1. `cd C:\Szkolenie\dzien-1\praca`, `claude`.

### Część 1: Proces 1 dla października – z przepisu

2. *„Przeczytaj `przepis_proces1.md` i wykonaj go dla
   `eksport_erp_2026-10.csv`. Wynik wpisz do **nowego** pliku
   `zestawienie_miesieczne_2026-10.xlsx` utworzonego z kopii szablonu
   (wyczyść w nim D i E, B2 = »październik«). Września nie ruszaj."*
3. Porównaj sumy wg działów z kluczem odpowiedzi. Czy przepis zadziałał
   bez dopytywania? Jeśli Claude musiał o coś pytać – to znak, że
   `przepis_proces1.md` był niekompletny. Dopisz brakującą regułę.
4. *„Czy w eksporcie za październik były jakieś problemy z jakością?
   Jeśli nie – napisz to wprost w raporcie."* (Nie było – ale Claude ma
   to sprawdzić, nie zakładać.)

### Część 2: Proces 2 dla października – ze skryptu

5. Skrypt z zadania 7 czyta z `zestawienie_miesieczne_SZABLON.xlsx`.
   *„Zmień `proces2.py` tak, żeby nazwę pliku miesięcznego przyjmował jako
   drugi parametr. Uruchom: `proces2.py październik
   zestawienie_miesieczne_2026-10.xlsx`."*
6. Sprawdź w Excelu: `Wykonanie!M14` = 13 240 000 zł, `Prognoza!B2` = 10,
   kontrola OK.

### Część 3: Raport kontrolny

7. *„Wygeneruj `kontrola_2026-10.md` z trzema sekcjami:
   1) Porównanie październik vs wrzesień wg działów: kwota, różnica,
      różnica w % – posortowane malejąco po |różnicy|;
   2) Wykonanie narastająco po 10 miesiącach vs plan: % planu i ile
      powinno być »teoretycznie« (10/12 = 83,3%); zaznacz działy powyżej
      i poniżej;
   3) Lista kontroli: suma miesięczna = kolumna roczna (OK/BŁĄD), liczba
      działów w obu plikach, brakujące wartości.
   Kwoty w PLN z separatorem tysięcy. Bez nazwisk. Jeśli czegoś nie
   wiesz – napisz »do potwierdzenia«, nie zgaduj."*
8. Przeczytaj raport. Zweryfikuj **dwie** liczby w Excelu. Które działy
   są powyżej 83,3% planu po październiku? (Dla 801 powinno wyjść ok.
   81,7%.)
9. *„Dopisz do `przepis_proces1.md` sekcję »Po Procesie 2« z krokiem:
   wygeneruj raport kontrolny jak wyżej."*

### Część 4: Test „nowej osoby"

10. Wyjdź z Claude Code (`/exit`), uruchom ponownie (`claude`) – nowa
    sesja nie pamięta rozmowy. Poproś:
    *„Mam zamknąć listopad. Przeczytaj `przepis_proces1.md` i `proces2.py`
    i powiedz, jakich plików potrzebujesz ode mnie i co zrobisz krok po
    kroku. Nie wykonuj jeszcze."*
    Jeśli plan jest kompletny i zrozumiały – przepis jest gotowy do
    używania co miesiąc. Jeśli nie – widzisz dokładnie, czego brakuje w
    opisie.

## Na co zwrócić uwagę

- **Nowy plik miesięczny zamiast nadpisywania szablonu** – w prawdziwym
  procesie każdy miesiąc ma swój plik, a szablon zostaje czysty.
- Raport kontrolny liczy dwie rzeczy, których ręcznie nikt nie robi co
  miesiąc: zmianę m/m wg działów i tempo wykonania planu. To gotowy
  materiał na Dzień 3 (DataPOV: co dane mówią + co z tego wynika).
- **Test nowej osoby (Część 4)** to najlepszy sprawdzian przepisu: jeśli
  Claude w świeżej sesji wie, co robić, będzie to wiedział też za pół
  roku – i będzie to wiedziała koleżanka z wydziału.
- Zauważ: Claude nie pamięta poprzedniej sesji, ale pamięta **pliki**.
  Wszystko, co ma przetrwać, musi być w pliku (przepis, skrypt, raport) –
  o tym jest zadanie 10.

## Notatki własne

- Czy Proces 1 dla października przeszedł bez dopytywania?
- Które działy raport wskazał jako powyżej tempa planu?
- Czego zabrakło w przepisie w teście „nowej osoby"?
