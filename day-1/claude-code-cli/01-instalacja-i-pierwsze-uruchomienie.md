# Zadanie 1: Instalacja Claude Code i pierwsze uruchomienie

**Cel:** zainstalować Claude Code, zalogować się kontem Urzędu, uruchomić
w bezpiecznym folderze roboczym i przejść pierwszą rozmowę z pytaniem
o zgodę.
**Poziom:** podstawowy
**Czas:** ok. 20 minut
**Blok:** Dzień 1 — wprowadzenie (samodzielnie). Jeśli instalacja była
w Bloku D (`../claude-code/06-instalacja-claude-code-cli.md`) – zacznij od
Części 2.

> Claude Code działa w terminalu **w konkretnym folderze na dysku**: czyta
> pliki, tworzy nowe, zmienia istniejące, uruchamia skrypty – za każdym
> razem pytając o zgodę. Dlatego uruchamiamy go tylko w folderze z danymi
> fikcyjnymi.

## Wymagania

- Windows 10/11, uprawnienia do instalacji (albo IT instaluje wcześniej).
- Konto Claude w organizacji Urzędu (plan Team).
- **Git for Windows** ([git-scm.com](https://git-scm.com/download/win)).
- **Python 3** ([python.org](https://www.python.org/downloads/), zaznacz
  „Add Python to PATH") + `pip install openpyxl pandas`. Claude Code czyta
  Excela skryptami w Pythonie – bez tego zadania 3–10 nie zadziałają.

## Kroki

### Część 1: Instalacja

1. Otwórz **PowerShell** (Start → wpisz „PowerShell").
2. Wklej i zatwierdź Enterem:

   ```powershell
   irm https://claude.ai/install.ps1 | iex
   ```

3. Zamknij i otwórz PowerShell ponownie. Sprawdź:

   ```powershell
   claude --version
   python -c "import openpyxl, pandas; print('OK')"
   ```

   **Sprawdź:** numer wersji i `OK`. Jeśli drugie polecenie zwraca błąd –
   `pip install openpyxl pandas`.

### Część 2: Folder roboczy

4. Utwórz folder:

   ```powershell
   mkdir C:\Szkolenie\dzien-1\praca
   ```

5. Skopiuj **zawartość** `claude-code-cli/materialy/` (pendrive od
   prowadzącego) do `C:\Szkolenie\dzien-1\praca\`. Oryginały zostają na
   pendrive – gdy coś pójdzie nie tak, kopiujesz ponownie.
6. Wejdź do folderu:

   ```powershell
   cd C:\Szkolenie\dzien-1\praca
   ```

### Część 3: Pierwsza rozmowa

7. Uruchom:

   ```powershell
   claude
   ```

   Przy pierwszym uruchomieniu wybierz logowanie kontem Claude – otworzy
   się przeglądarka, zaloguj się kontem Urzędu, wróć do terminala.

8. Pierwsze pytanie, po polsku:

   ```
   W jakim folderze jesteśmy i jakie pliki tu widzisz? Opisz krótko,
   nic jeszcze nie zmieniaj.
   ```

9. **Pytanie o zgodę.** Claude pokaże, co chce uruchomić, i opcje
   **Yes / Yes, and don't ask again / No**. Przeczytaj i wybierz **Yes**
   (strzałki + Enter). Na szkoleniu nie używamy „don't ask again".

   **Sprawdź:** odpowiedź wymienia `01_sandbox/`, dwa eksporty CSV i trzy
   pliki `.xlsx`.

10. Trzy komendy do zapamiętania:

    ```
    /help
    ```

    ```
    /status
    ```

    – na jakim koncie i w jakim folderze pracujesz. Plus: `/clear` = nowa
    rozmowa, **Esc** = przerwij, `/exit` = zamknij.

11. Zakończ:

    ```
    /exit
    ```

## Na co zwrócić uwagę

- **Zawsze najpierw `cd` do folderu roboczego, potem `claude`.** Nigdy
  w `C:\`, `Dokumentach` ani w folderze zsynchronizowanym z OneDrive /
  SharePoint Urzędu.
- Rozmowa jest kontekstowa jak w czacie – nie powtarzasz, o jaki plik
  chodzi.
- Wszystko, co napiszesz, i pliki, które Claude przeczyta, trafiają do
  Anthropic (plan Team – bez trenowania, ale poza Urzędem). Stąd: **tylko
  dane fikcyjne**.

## Notatki własne

- Co wypisał `claude --version` i `/status`?
- Na co Claude Code poprosił o zgodę przy pierwszym pytaniu?
