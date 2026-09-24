# Zadanie 1: Claude w Excelu – instalacja dodatku i pierwsze uruchomienie

**Dzień 2, Blok B** · ok. 10 min · Excel z Microsoft 365, konto Claude
Urzędu (plan Team), dostęp do sklepu dodatków Office.

**Cel:** dodać Claude do Excela jako dodatek i sprawdzić, że panel widzi
otwarty arkusz bez wgrywania pliku.

**Plik:** [`materialy/Human_Resources.xlsx`](materialy/Human_Resources.xlsx) (fikcyjne
kadry, 1 470 wierszy × 35 kolumn, numer zamiast nazwiska). Folder
`materialy/` to jedyne miejsce pracy – pliki startowe i wszystkie kopie
z zadań 1–9 zostają w nim, nic na Pulpicie ani w *Pobranych*.

> Dodatek wysyła zawartość otwartego arkusza do dostawcy modelu. Z
> włączonym dodatkiem otwieramy **tylko plik fikcyjny**; inne skoroszyty
> zamknijcie. Realne dane Urzędu – wyłącznie za pisemną zgodą.

## Instalacja (3 min)

1. Otwórzcie [`materialy/Human_Resources.xlsx`](materialy/Human_Resources.xlsx).
2. Wstążka → **Dodatki** (albo *Wstawianie → Pobierz dodatki*) → wyszukajcie
   `Claude` → **Claude by Anthropic** → **Dodaj**. Po chwili: ikona na wstążce
   i panel po prawej.
3. Zalogujcie się kontem Claude Urzędu (to samo co do czatu i Cowork).
4. Model (góra panelu): **Opus** do formuł i większych zadań, **Sonnet** do
   prostych pytań. Zmiana modelu to jedno kliknięcie.

## Polecenia

### 1. Co widzi panel

> Co jest w tym arkuszu? Opisz po polsku grupy kolumn, liczbę wierszy i do
> czego ten plik może służyć.

Sprawdź: odpowiedź ma **adresy komórek i zakresów** (np. `A2:AI1471`,
`B` = wynagrodzenie, `C` = odejścia) i grupuje 35 kolumn w bloki.

### 2. Sprawdzian

> Ile wierszy ma zakres danych?

Klucz: **1 470**.

### 3. Podpowiedzi panelu

Przejrzyjcie zapisane podpowiedzi (*buduj model finansowy*, *uporządkuj
bałagan w danych*, *znajdź błąd w formule*) – nie klikajcie niczego, co
zmienia komórki. Zmiany zaczynają się w zadaniu 2.

## Pamiętaj

- Dodatek widzi **tylko otwarty skoroszyt** – do pracy na wielu plikach
  (Proces 1 → 2) jest Claude Code.
- Brak przycisku Dodatki / pusty sklep = blokada administratora M365 →
  zgłoszenie do IT o dopuszczenie *Claude by Anthropic* (przed Dniem 2).
- `materialy/Human_Resources.xlsx` zostaje nietknięty jako oryginał. Od zadania 2
  Claude pisze do komórek, więc każde zadanie zaczyna się od *Plik →
  Zapisz jako* w `materialy/`: `Human_Resources_zad2.xlsx`,
  `_zad3.xlsx` itd.
