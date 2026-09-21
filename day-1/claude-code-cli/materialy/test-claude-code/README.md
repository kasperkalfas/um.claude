# Folder startowy do Bloku D (zadania 7–15) — DANE FIKCYJNE

Jeden folder, przez który zadania 7–15 z `day-1/claude-code/` przechodzą
**liniowo, bez resetowania** między zadaniami. Wszystkie kwoty i wydziały
są fikcyjne (materiał szkoleniowy, zgodnie z zasadą bezpieczeństwa danych
z Bloku B).

## Przygotowanie (przed Blokiem D)

Folder jest częścią `claude-code-cli/materialy/` – jednego zestawu
materiałów Claude Code, który w całości kopiuje się do
`C:\Szkolenie\dzien-1\praca\` (zadanie 1 z `claude-code-cli/`). Zadania 7–15
uruchamiacie w `C:\Szkolenie\dzien-1\praca\test-claude-code` (na każdym
komputerze albo tylko u prowadzącego, jeśli blok idzie jako demo) – **w
kopii**, nie w repozytorium. Żeby zresetować stan po ćwiczeniach — skopiuj
podfolder z pendrive'a jeszcze raz.

## Zawartość

| Plik | Miesiąc | Wierszy | Rola |
|---|---|---|---|
| `zestawienie_przykladowe.xlsx` | wrzesień 2026 | 7 | zad. 8–10 (odczyt, wiersz „Razem", zmiana nazwy) |
| `zestawienie_wrzesien_wydzialy.xlsx` | wrzesień 2026 | 8 | drugi plik wrześniowy do sortowania (zad. 13) |
| `zestawienie_pazdziernik_wydzialy.xlsx` | październik 2026 | 8 | plik październikowy do sortowania (zad. 13) |
| `zestawienie_pazdziernik_PODSUMOWANIE.xlsx` | październik 2026 | 10 | zawiera najwyższą kwotę wykonaną (zad. 14) |
| `notatka_do_zestawienia.txt` | — | — | plik nie-Excel do odczytu (zad. 8) i wskazówka o archiwum |
| `archiwum/zestawienie_sierpien.xlsx` | sierpień 2026 | 8 | podfolder do nawigacji (zad. 12) |
| `archiwum/zal_3_korekta.xlsx` | lipiec 2026 | 5 | plik o **nieoczywistej nazwie**, zawiera Zieleni Miejskiej (zad. 14) |

Wszystkie pliki `.xlsx` mają te same kolumny: **Dział, Kwota planowana,
Kwota wykonana, Miesiąc** — dzięki temu zad. 15 (zestawienie z wielu
plików) działa bez czyszczenia danych. Żaden plik nie jest celowo
zepsuty (zepsuty `zestawienie_miesieczne_PRZYKLAD.xlsx` zostaje w
`day-1/materialy/` tylko do zad. 3 z Bloku C).

## Jak folder zmienia się w trakcie zadań

- zad. 9: w `zestawienie_przykladowe.xlsx` pojawia się wiersz „Razem"
  z formułą,
- zad. 10: ten plik zmienia nazwę na `zestawienie_wrzesien_2026.xlsx`,
- zad. 11: wszystkie `.xlsx` w folderze głównym dostają prefiks `UM_`
  (archiwum bez zmian),
- zad. 13: powstają foldery `Wrzesien/` i `Pazdziernik/`, pliki z folderu
  głównego trafiają do nich wg miesiąca **z danych**,
- zad. 14–15: tylko odczyt, nic się nie zmienia.

## Klucz odpowiedzi dla prowadzącego

**Zad. 14 – „Zieleni Miejskiej"** występuje we **wszystkich 6 plikach
.xlsx**, w tym w ukrytym `archiwum/zal_3_korekta.xlsx` (85 000 / 96 000).
Sens ćwiczenia: Claude Code znajduje go też w pliku, którego nazwa nic
nie sugeruje.

**Zad. 14 – najwyższa Kwota wykonana:** **860 000 zł, Wydział
Inwestycji**, plik `zestawienie_pazdziernik_PODSUMOWANIE.xlsx`.

**Zad. 15 – suma przekroczeń (wykonanie − plan, tylko dodatnie) per
miesiąc, wszystkie pliki łącznie z archiwum:**

| Miesiąc | Plan | Wykonanie | Suma przekroczeń |
|---|---|---|---|
| lipiec 2026 | 1 980 000 | 1 940 000 | 20 000 |
| sierpień 2026 | 2 381 000 | 2 373 000 | 60 000 |
| wrzesień 2026 | 5 320 000 | 5 216 000 | 98 000 |
| **październik 2026** | 6 555 000 | 6 811 000 | **393 000** |

Odpowiedź: **październik** — z dużym marginesem, więc nie ma
niejednoznaczności. Uwaga: jeśli zad. 9 zostało wykonane, w
`zestawienie_przykladowe.xlsx` (po zad. 10–11: `UM_zestawienie_wrzesien_2026.xlsx`)
jest wiersz „Razem" — Claude Code powinien go pominąć przy sumowaniu;
jeśli go doliczy, wrzesień wyjdzie zawyżony. To dobry moment na
komentarz „zawsze sprawdzaj, co weszło do sumy".
