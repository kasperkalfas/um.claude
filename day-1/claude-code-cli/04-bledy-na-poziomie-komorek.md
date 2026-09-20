# Zadanie 4: Błędy na poziomie komórek – znajdź i napraw

**Cel:** Claude Code wskazuje niespójności i braki w arkuszu z dokładnością
do konkretnej komórki (nie „gdzieś są scalone komórki", tylko „B10:B11"),
a potem – na wyraźne polecenie i po zrobieniu kopii – naprawia je.
**Poziom:** podstawowy → średni
**Czas:** ok. 30 minut
**Blok:** Dzień 1 — praca na komórkach

## Materiały

- `zestawienie_bledy.xlsx` – zestawienie miesięczne za sierpień z
  **ośmioma** celowo wprowadzonymi błędami z „checklisty Bloku B" (Dzień 1).
  Klucz odpowiedzi dla prowadzącego jest w [README](README.md#klucz-odpowiedzi).

## Kroki

1. `cd C:\Szkolenie\dzien-1\praca`, `claude`. **Zamknij ten plik w
   Excelu**, jeśli jest otwarty – Claude nie zapisze zmian do otwartego
   pliku (patrz „Na co zwrócić uwagę").

### Część 1: Diagnoza

2. *„Sprawdź `zestawienie_bledy.xlsx` pod kątem: scalonych komórek, kwot
   zapisanych jako tekst, pustych wierszy w środku danych, brakujących
   nagłówków, ukrytych kolumn lub wierszy, niespójnych formatów dat,
   formuł zwracających błąd oraz brakujących wartości. Wypisz każdy
   problem z adresem komórki lub zakresu. Nic nie zmieniaj."*
3. Porównaj z kluczem odpowiedzi (prowadzący) albo z własnym przeglądem w
   Excelu: ile z 8 błędów Claude znalazł? Który pominął?
4. Dopytaj o pominięte, ale **bez podpowiadania adresu**, np.:
   *„Czy suma w wierszu Razem (D15) uwzględnia wszystkie działy? Dlaczego?"*
   – dobra odpowiedź: nie, bo D7 jest tekstem, więc `SUM` ją pomija.

### Część 2: Kopia, potem naprawa

5. *„Zanim cokolwiek zmienisz: skopiuj plik do podfolderu `kopie` z
   dopiskiem daty i godziny w nazwie."* Sprawdź w Eksploratorze, że kopia
   istnieje. **To nawyk na całe szkolenie.**
6. Naprawiaj po jednym, żeby widzieć każdy krok:
   - *„Rozdziel scalone komórki B10:B11 i uzupełnij brakującą nazwę
     działu 852 – to »Pomoc społeczna«."*
   - *„Zamień tekst w D7 na liczbę, zachowaj format walutowy jak w D6."*
   - *„Usuń pusty wiersz 9 i przesuń dane w górę. Uwaga: formuły w
     kolumnie F i w wierszu Razem muszą po tym nadal wskazywać właściwe
     wiersze."*
   - *„Odkryj kolumnę E."*
   - *„Wpisz brakujący nagłówek w F5: »% wykonania planu«."*
   - *„Uzupełnij plan działu 921 w kolumnie C – plan roczny to
     7 400 000 zł – i sprawdź, czy formuła % w tym wierszu przestała
     zwracać błąd."*
   - *„Ujednolić daty w komórkach »Sporządzono« i »Zatwierdzono« do
     formatu RRRR-MM-DD."*
7. *„Wypisz jeszcze raz pełną listę kontrolną z kroku 2 – czy coś zostało?"*
8. Otwórz plik w Excelu: czy `Razem` w D się zmieniło (powinno wzrosnąć o
   kwotę z D7)? Czy `#DIV/0!` zniknął?

### Część 3: Jedna komenda zamiast siedmiu

9. Skopiuj **oryginalny** plik z pendrive'a jeszcze raz (albo z `kopie`)
   jako `zestawienie_bledy_2.xlsx` i poproś:
   *„Zrób kopię do `kopie`, a potem napraw w `zestawienie_bledy_2.xlsx`
   wszystkie problemy z listy z kroku 2. Po naprawie wypisz tabelę: co
   było, gdzie, co zrobiłeś."*
10. Porównaj oba naprawione pliki. Gdzie Claude „domyślił się" inaczej niż
    Ty w Części 2 (np. inny format daty, inna nazwa działu)? To pokazuje,
    dlaczego przy zbiorczej naprawie doprecyzowujemy oczekiwania z góry.

## Na co zwrócić uwagę

- **Plik otwarty w Excelu jest zablokowany do zapisu.** Claude dostanie
  błąd `PermissionError` i zwykle sam o tym powie. Zamknij plik, poproś
  *„spróbuj ponownie"*.
- **Kopia przed zmianą** – Claude Code nie ma „cofnij" dla plików
  binarnych. Kopia w `kopie/` to Wasze cofnij.
- Naprawa pustego wiersza to najbardziej ryzykowna operacja: przesuwa
  wiersze, a formuły muszą „nadążyć". Dlatego w poleceniu mówimy o tym
  wprost. Po takiej operacji **zawsze** sprawdzamy sumy w Excelu.
- Claude może zaproponować „poprawki", o które nie prosiłeś (np.
  przeformatować cały arkusz). Odmawiaj (**No**) i pisz: *„tylko to, o co
  prosiłem"*.

## Notatki własne

- Ile z 8 błędów Claude znalazł za pierwszym razem?
- Który błąd byłby najtrudniejszy do zauważenia ręcznie w prawdziwym,
  większym zestawieniu?
