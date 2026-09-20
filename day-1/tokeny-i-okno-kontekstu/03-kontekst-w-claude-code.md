# Zadanie 3: Kontekst w praktyce – Claude Code i Cowork

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
wstęp do **Bloku D: Claude Code – pierwszy kontakt**).

**Cel:** zobaczyć okno kontekstu „na liczniku" w Claude Code, poznać trzy
polecenia, które nim sterują (`/context`, `/compact`, `/clear`), i wynieść
kilka nawyków oszczędzania kontekstu.
**Poziom:** podstawowy
**Czas:** ok. 7 minut
**Wymaga:** zainstalowanego Claude Code
([`../claude-code/06-instalacja-claude-code-cli.md`](../claude-code/06-instalacja-claude-code-cli.md))
i folderu testowego `../materialy/test-claude-code/` skopiowanego na Pulpit.

## Problem, który to rozwiązuje

W czacie okno kontekstu jest niewidoczne – dowiadujecie się o nim dopiero,
gdy coś przestaje działać. Claude Code i Cowork pokazują je wprost:
Cowork ma pasek kontekstu po prawej stronie (widać, co go zajmuje i ile
zostało), a Claude Code ma polecenie `/context` i sam ostrzega, gdy
zbliża się do limitu. Warto wiedzieć, na co patrzeć.

## Materiały

- Terminal z Claude Code uruchomionym w folderze testowym na Pulpicie.
- (Opcjonalnie) Claude Cowork – do pokazania paska kontekstu.

## Kroki

1. Uruchomcie Claude Code w folderze testowym i **od razu**, zanim
   cokolwiek wpiszecie, wydajcie polecenie `/context`. Zobaczycie, że
   okno **nie jest puste**: instrukcje systemowe, opisy narzędzi,
   `CLAUDE.md` (jeśli jest) już zajmują miejsce. To „koszt stały" każdej
   rozmowy.
2. Poproście: *„Przeczytaj wszystkie pliki w tym folderze i streść, co w
   nich jest."* Po odpowiedzi znowu `/context`. Porównajcie: o ile
   urosło? Zwróćcie uwagę, że wczytane pliki i odpowiedź Claude liczą
   się razem – dokładnie jak w tabeli z zadania 2.
3. Wydajcie `/compact`. Claude Code **streści** dotychczasową rozmowę i
   zastąpi ją tym streszczeniem – `/context` pokaże spadek. Zapytajcie
   potem: *„Co było w plikach, które czytałeś przed chwilą?"* – Claude
   powinien odpowiedzieć ze streszczenia, ale może zgubić drobne
   szczegóły. Tak wygląda kompaktowanie, które Claude Code robi też
   **automatycznie**, gdy okno się zapełnia (komunikat o „compacting").
4. Wydajcie `/clear`. To czysta karta: rozmowa znika, zostaje tylko
   „koszt stały" z kroku 1. Sprawdźcie `/context`. Zasada: **nowy temat =
   `/clear`**, nie „ciągniemy" jednej rozmowy przez cały dzień.
5. (Jeśli jest Cowork) Otwórzcie Cowork i pokażcie pasek kontekstu po
   prawej – to ten sam mechanizm w wersji graficznej: widać, co zajmuje
   okno, i kiedy Cowork robi kompaktowanie.

## Na co zwrócić uwagę

- **`/context`** – ile okna zajęte i przez co. **`/compact`** – streść i
  zwolnij miejsce (tracicie szczegóły, zachowujecie sens). **`/clear`** –
  zacznij od zera (tracicie wszystko z rozmowy, zostaje `CLAUDE.md` i
  pliki na dysku). Pełna lista poleceń: [`../claude-code/17-polecenia-specjalne.md`](../claude-code/17-polecenia-specjalne.md).
- **Kompaktowanie to streszczenie, nie pamięć.** Po `/compact` Claude
  „pamięta" tylko to, co trafiło do streszczenia. Jeśli coś jest ważne
  (ustalona zasada, format kwot), zapiszcie to w `CLAUDE.md`
  ([`../claude-code/19-claude-md-pamiec-projektu.md`](../claude-code/19-claude-md-pamiec-projektu.md))
  – plik na dysku przeżyje każde kompaktowanie i każdy `/clear`.
- **Nawyki oszczędzania okna** (przydadzą się w Dniu 2):
  1. jeden temat = jedna rozmowa (`/clear` między zadaniami);
  2. proście o *podsumowanie* pliku, nie o *wklejenie całości*;
  3. duże Excele niech Claude Code czyta skryptem (Python/openpyxl) – do
     okna trafia wynik, nie tysiące komórek;
  4. `CLAUDE.md` krótki i konkretny – jest wczytywany do **każdej**
     rozmowy, więc każda zbędna linijka kosztuje tokeny za każdym razem;
  5. kiedy Claude zaczyna „gubić wątek", nie walczcie – `/compact` albo
     `/clear` i krótkie przypomnienie, o co chodzi.
- Skille, konektory i serwery MCP (zadania 4–8 w `../claude-zadania/`)
  też zajmują miejsce w oknie – ich opisy są wczytywane do rozmowy.
  Dziesięć podpiętych narzędzi „naraz" to realny koszt, nawet gdy ich
  nie używacie.

## Notatki własne

- Ile procent okna było zajęte po kroku 1 (przed jakąkolwiek pracą)? Ile
  po kroku 2?
- Które z Waszych typowych zadań warto rozbić na osobne rozmowy, a w
  których kompaktowanie nic nie zepsuje?
