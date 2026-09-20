# Zadanie 1: Instalacja Claude Code i pierwsze uruchomienie

**Cel:** zainstalować Claude Code na Windows, zalogować się kontem Urzędu,
uruchomić go w bezpiecznym folderze roboczym i zrozumieć, jak wygląda
rozmowa w terminalu – łącznie z pytaniami o zgodę.
**Poziom:** podstawowy
**Czas:** ok. 20 minut
**Blok:** Dzień 1 — wprowadzenie (samodzielnie; jeśli instalację zrobiono już w
Bloku D Dnia 1 wg `../claude-code/06-instalacja-claude-code-cli.md` –
przejdź od razu do Części 2)

> **Czym różni się Claude Code od czatu z Dnia 1?** Czat odpowiada w
> przeglądarce i nie dotyka Twojego komputera. Claude Code działa w
> terminalu **w konkretnym folderze na dysku**: czyta pliki, które tam są,
> tworzy nowe, zmienia istniejące i uruchamia polecenia – za każdym razem
> pytając o zgodę. To dlatego uruchamiamy go tylko w folderze z danymi
> fikcyjnymi, nigdy w folderze z prawdziwymi zestawieniami.

## Wymagania

- Windows 10/11, uprawnienia do instalacji programów (jeśli nie – IT
  Urzędu instaluje przed szkoleniem).
- Konto Claude w organizacji Urzędu (plan Team) – login przez przeglądarkę.
- **Git for Windows** ([git-scm.com](https://git-scm.com/download/win)) –
  Claude Code używa dostarczanego z nim Git Bash.
- **Python 3** ([python.org](https://www.python.org/downloads/), przy
  instalacji zaznacz „Add Python to PATH") oraz biblioteki:
  `pip install openpyxl pandas`. Claude Code nie „otwiera" Excela sam –
  pisze krótkie skrypty w Pythonie i je uruchamia. Bez Pythona zadania
  3–10 nie zadziałają.

## Kroki

### Część 1: Instalacja

1. Otwórz **PowerShell** (Start → wpisz „PowerShell").
2. Wklej i zatwierdź Enterem:
   ```powershell
   irm https://claude.ai/install.ps1 | iex
   ```
3. Zamknij PowerShell i otwórz ponownie (żeby system „zobaczył" nowy
   program). Sprawdź: `claude --version` – powinien wypisać numer wersji.

### Część 2: Folder roboczy

4. Utwórz folder roboczy i skopiuj do niego materiały:
   ```powershell
   mkdir C:\Szkolenie\dzien-1\praca
   ```
   Skopiuj **zawartość** folderu `claude-code-cli/materialy/` (od prowadzącego, np. z
   pendrive'a) do `C:\Szkolenie\dzien-1\praca\`. Oryginały zostają na
   pendrive – gdy coś pójdzie nie tak, kopiujesz ponownie.
5. Wejdź do folderu: `cd C:\Szkolenie\dzien-1\praca`

### Część 3: Pierwsza rozmowa

6. Uruchom: `claude`. Przy pierwszym uruchomieniu wybierz logowanie
   kontem Claude – otworzy się przeglądarka, zaloguj się kontem Urzędu i
   wróć do terminala.
7. Napisz pierwsze pytanie (po polsku, jak w czacie):
   *„W jakim folderze jesteśmy i jakie pliki tu widzisz? Opisz krótko,
   nic jeszcze nie zmieniaj."*
8. Obserwuj: Claude Code najpierw **pyta o zgodę** na odczyt/uruchomienie
   polecenia. Zobaczysz opcje w stylu **Yes / Yes, and don't ask again /
   No**. Wybierz **Yes** (strzałki + Enter). Przeczytaj, co proponuje
   zrobić, zanim się zgodzisz – to Twoja główna kontrola.
9. Wpisz `/help` – lista komend. Potem `/status` – na jakim koncie i w
   jakim folderze pracujesz. Zapamiętaj trzy komendy:
   - `/clear` – nowa rozmowa (czysta karta, jak „New chat" w czacie),
   - `Esc` – przerwij to, co Claude właśnie robi,
   - `/exit` – zamknij Claude Code.
10. Zakończ `/exit`.

## Na co zwrócić uwagę

- **Claude Code widzi tylko folder, w którym go uruchomiono** (i jego
  podfoldery). Dlatego zawsze najpierw `cd` do folderu roboczego, a dopiero
  potem `claude`. Nigdy nie uruchamiaj go w `C:\`, w `Dokumentach` ani w
  folderze zsynchronizowanym z OneDrive/SharePoint Urzędu.
- **Pytanie o zgodę to nie formalność.** „Yes, and don't ask again"
  wyłącza pytania dla tego typu polecenia do końca sesji – na szkoleniu
  wybieramy zwykłe **Yes**, żeby widzieć każdy krok.
- Rozmowa jest kontekstowa jak w czacie: nie musisz powtarzać, o jaki plik
  chodzi, jeśli mówiliście o nim przed chwilą.
- Wszystko, co napiszesz, i wszystkie pliki, które Claude przeczyta w tym
  folderze, trafiają do Anthropic (plan Team – bez trenowania na Waszych
  danych, ale nadal poza Urzędem). Stąd zasada: **tylko dane fikcyjne**.

## Notatki własne

- Co wypisał `claude --version` i `/status`?
- Na co Claude Code poprosił o zgodę przy pierwszym pytaniu?
