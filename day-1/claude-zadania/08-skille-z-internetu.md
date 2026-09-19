# Zadanie 8: Gotowe skille z internetu – które przydadzą się w Urzędzie

> **Materiał dodatkowy – poza Blokiem C.** Do samodzielnej pracy po
> szkoleniu, najlepiej po [zadaniu 7](07-skill-notatka-budzetowa.md) –
> wtedy wiesz już, jak wygląda skill od środka, i łatwiej ocenisz cudzy.

**Cel:** przejrzeć oficjalne repozytorium skilli Anthropic, wybrać te, które
realnie przydadzą się w pracy Urzędu, jeden z nich (`internal-comms`)
zainstalować, przetestować na fikcyjnym zestawieniu i **dostosować do
zasad Urzędu** – zamiast pisać wszystko od zera jak w zadaniu 7.
**Poziom:** średniozaawansowany
**Czas:** ok. 40 minut

## Zanim zaczniesz: dwa rodzaje skilli w tabeli niżej

W repozytorium wszystkie skille wyglądają tak samo (folder z instrukcją
`SKILL.md`). Różnica jest tylko taka, **czy Anthropic już go dla Ciebie
włączył w claude.ai, czy nie**:

- **Wbudowane** (`xlsx`, `pptx`, `docx`, `pdf`) – to jak fabrycznie
  zainstalowana aplikacja w nowym telefonie. Działają same, bez żadnej
  instalacji – wystarczy wgrać plik i poprosić Claude o coś. W Części 1
  tylko **czytamy** ich instrukcję, żeby zrozumieć, dlaczego Claude robi
  to, co robi (np. wpisuje formułę zamiast liczby) – nic nie klikamy.
- **Do zainstalowania** (`internal-comms` i reszta) – to jak aplikacja ze
  sklepu: istnieje, jest gotowa, ale dopóki sam/sama jej nie pobierzesz i
  nie wgrasz, Twoje konto Claude w ogóle o niej nie wie. W Części 2
  faktycznie ją instalujemy (ZIP + upload), żeby to zobaczyć na własne
  oczy.

**Dowód w praktyce jest w krokach 7–9**: to samo pytanie o „raport
statusu" zadajesz najpierw bez skilla (porównanie z zadaniem 3), a potem
po jego wgraniu – i dopiero wtedy odpowiedź zmienia format. To pokazuje,
że instalacja naprawdę coś zmienia, a wbudowane skille działały od
początku, bez Twojego udziału.

## Co jest w repozytorium i co z tego przyda się w Urzędzie

Repozytorium [github.com/anthropics/skills](https://github.com/anthropics/skills),
folder `skills/` (stan: wrzesień 2026):

| Skill | Do czego | Przydatność w Urzędzie | Co z nim zrobić |
|---|---|---|---|
| `xlsx` | Excel: tworzenie i edycja arkuszy – formuły zamiast wpisanych wyników, kontrola błędów | **bardzo wysoka** – to Proces 1 i 2, cały Dzień 2 | **nie instalować** – jest wbudowany w claude.ai; **przeczytać**, żeby wiedzieć, jak Claude pracuje z Excelem (Część 1) |
| `pptx` | PowerPoint: tworzenie prezentacji z danych | wysoka – Proces 3, Dzień 3 | wbudowany; wrócimy do niego w Dniu 3 |
| `docx`, `pdf` | dokumenty Word, praca z PDF (pisma, protokoły, skany) | wysoka – korespondencja urzędowa | wbudowane; do samodzielnego przejrzenia |
| `internal-comms` | komunikaty wewnętrzne: raporty statusu, aktualizacje dla kierownictwa, odpowiedzi FAQ, aktualizacje 3P (postępy / plany / problemy) | **wysoka** – notatki dla Skarbnika i kierownictwa, powtarzalne odpowiedzi dla wydziałów | **zainstalować i dostosować** (Części 2–4) |
| `skill-creator` | buduje kolejne skille w rozmowie | średnia – gdy zad. 7 wejdzie w krew | wariant dla chętnych w zadaniu 7 |
| `brand-guidelines` | spójna identyfikacja wizualna w dokumentach | niska – ewentualnie zespół promocji miasta | pominąć |
| pozostałe (`frontend-design`, `mcp-builder`, `webapp-testing`, `web-artifacts-builder`, `claude-api`, `canvas-design`, `algorithmic-art`, `theme-factory`, `slack-gif-creator`, `doc-coauthoring`, `academy-guide`, `discernment-nudge`) | narzędzia dla programistów i projektantów | niska dla wydziału finansowego | pominąć |

## Skill `internal-comms` od środka

**Najprościej:** to gotowy szablon na wiadomości, które pisze się w pracy
regularnie – krótki raport dla szefostwa co się dzieje w zespole,
newsletter dla wszystkich, odpowiedzi na powtarzające się pytania.
Zamiast za każdym razem tłumaczyć Claude, jak ma wyglądać taki tekst
(format, długość, ton), ten skill już to „wie" – sam rozpoznaje, o jaki
rodzaj wiadomości prosisz, i używa gotowego wzoru. To trochę jak gotowy
wzór pisma urzędowego, który ktoś wcześniej przygotował – nie musisz za
każdym razem układać struktury od zera, podajesz tylko treść, a forma
jest już ustalona. Problem: wzór został przygotowany z myślą o zwykłej
firmie (Slack, ton „my zrobiliśmy" jak firma do pracowników), więc w
Części 4 dopisujemy własną sekcję zasad, żeby ten sam mechanizm pisał już
w stylu pasującym do Urzędu.

Zanim przejdziesz do instalacji (Część 2), warto wiedzieć, co jest w
środku – to ułatwi czytanie w kroku 4 i ocenę w kroku 9.

**Mechanizm:** `SKILL.md` sam w sobie nie ma treści komunikatów – to
„router". Na podstawie Twojej prośby wybiera **jeden** z czterech plików
w `examples/` i dopiero jego instrukcji się trzyma:

| Plik | Format | Dla kogo / kiedy |
|---|---|---|
| `3p-updates.md` | Progress/Plans/Problems – 3 linijki po 1–3 zdania, do przeczytania w 30–60 sek. | cykliczna aktualizacja zespołu dla kierownictwa (co tydzień) |
| `company-newsletter.md` | ok. 20–25 punktów w sekcjach z nagłówkami | newsletter dla całej organizacji (co tydzień/miesiąc) |
| `faq-answers.md` | `*Pytanie*: ... / *Odpowiedź*: ...` | powtarzające się pytania od wielu osób/wydziałów |
| `general-comms.md` | brak sztywnego formatu – najpierw dopytuje o odbiorcę, cel, ton | wszystko, co nie pasuje do trzech powyższych |

**Co w tym jest „firmowe" i nie pasuje wprost do Urzędu** (to lista, którą
i tak masz odtworzyć samodzielnie w kroku 9 – potraktuj jako podpowiedź,
jeśli utkniesz):

- Wszystkie trzy szczegółowe formaty każą Claude **samodzielnie szukać
  danych na Slacku**, w Google Drive i kalendarzu – Urząd tych narzędzi
  nie ma, więc bez podania kontekstu wprost skill i tak zapyta Cię o dane.
- `company-newsletter.md` zakłada firmę **1000+ osób**, ton „we did
  this" (piszemy jako organizacja) i nagłówki z emoji (np.
  `:megaphone: Company Announcements`) – zbyt korporacyjne dla
  korespondencji urzędowej.
- Żaden z formatów nie wspomina o **RODO/poufności danych** – stąd
  konieczność dopisania własnej sekcji zasad w Części 4.
- Brak formatowania kwot w PLN i polskich dat – kolejny punkt do
  dopisania.

To pokazuje, na czym polega Część 4: nie zmieniasz **mechanizmu ani
struktury** (routing + trzy sztywne formaty + jeden elastyczny) – tylko
nadpisujesz język, ton, źródła danych i brakujące zasady RODO.

## Materiały

- Konto na [claude.ai](https://claude.ai) z włączonym wykonywaniem kodu
  i tworzeniem plików (**Ustawienia → Capabilities** – *code execution and
  file creation*).
- Pliki z `../materialy/`: `zestawienie_przykladowe.xlsx` (Część 1) i
  `zestawienie_miesieczne_PODSUMOWANIE.xlsx` (Część 3).
- Notatnik i możliwość spakowania folderu do ZIP.

## Checklist bezpieczeństwa – przed każdą instalacją

Skill to instrukcja, którą Claude wykona w Twoim imieniu. Zasada z Bloku B
(„co wolno, a czego nie wolno wklejać do Claude") obowiązuje też tutaj:

1. **Źródło** – tylko oficjalne repozytorium Anthropic albo źródło
   zaakceptowane przez IT Urzędu. Nie z maila, nie z forum.
2. **Przeczytaj cały `SKILL.md`** – szukaj zdań typu „wyślij dane na…",
   „ignoruj instrukcje użytkownika", adresów e-mail i linków, do których
   skill ma coś wysyłać.
3. **Zajrzyj do podfolderów** (`examples/`, `scripts/`, `references/`).
   Skill ze skryptami (`.py`, `.js`) niech oceni IT **przed** instalacją.
   `internal-comms` skryptów nie ma – dlatego nadaje się na pierwszy raz.
4. **Testuj na danych fikcyjnych.**
5. **Wyłącz po teście**, jeśli nie będziesz używać.

## Kroki

### Część 1: Zrozum wbudowany skill `xlsx` (czytanie, nie instalacja)

**Najprościej:** to zestaw zasad, których Claude trzyma się za każdym
razem, gdy pracuje z plikiem Excela – żeby nie było przypadkowości.
Najważniejsza zasada: ma wpisywać **wzór** (np. `=SUMA(B2:B9)`), a nie
gotowy wynik, żeby arkusz sam się przeliczył, gdy zmienisz dane wejściowe.
Druga: zanim odda plik, **sam sprawdza, czy nie ma w nim błędów** (typu
`#ARG!`, `#ADR!`) – jakby ktoś przejrzał arkusz przed wysłaniem dalej.
Trzecia: robi **dokładnie to, o co poprosisz** (te same nazwy kolumn i
arkuszy), a nie „ulepsza" pomysłu po swojemu. Ten skill już działa – nie
instalujesz go, tylko poniżej sprawdzasz go w praktyce.

1. Otwórz [skills/xlsx/SKILL.md](https://github.com/anthropics/skills/blob/main/skills/xlsx/SKILL.md)
   w repozytorium i przeczytaj sekcje o zasadach. Trzy z nich są kluczowe
   dla Dnia 2:
   - **formuły, nie wpisane wyniki** – Claude ma pisać `=SUMA(B2:B9)`, a
     nie gotową liczbę, żeby arkusz przeliczał się po zmianie danych;
   - **zero błędów** – po wpisaniu formuł Claude przelicza arkusz i nie
     oddaje pliku z `#ARG!`, `#ADR!` itp.;
   - **dokładnie wg specyfikacji użytkownika** – nazwy arkuszy, nagłówki i
     formuły takie, jak poprosisz, bez „ulepszania" po swojemu.
2. Sprawdź to w praktyce: w claude.ai wgraj `zestawienie_przykladowe.xlsx`
   i poproś:
   *„Dodaj na dole wiersz »Razem« z formułą sumującą kolumny Kwota
   planowana i Kwota wykonana. Zwróć plik do pobrania."*
3. Pobierz plik, otwórz w Excelu i kliknij komórkę z sumą. Powinna
   zawierać **formułę** (`=SUMA(...)` / `=SUM(...)`), nie wpisaną liczbę –
   to właśnie zasada ze skilla. Jeśli jest liczba, napisz Claude: „Użyj
   formuły, nie wpisanej wartości" – i zobacz różnicę.

### Część 2: Zainstaluj `internal-comms`

4. Otwórz folder [skills/internal-comms](https://github.com/anthropics/skills/tree/main/skills/internal-comms).
   Przeczytaj `SKILL.md` i **każdy plik w `examples/`** (3P updates,
   newsletter, FAQ, general comms) – odhacz checklistę z sekcji wyżej.
5. Na stronie głównej repozytorium: **„Code" → „Download ZIP"**. Wypakuj
   archiwum, znajdź folder `internal-comms`, spakuj **tylko ten folder** do
   nowego ZIP-a (prawy przycisk → **Kompresuj do pliku ZIP**).
6. W Claude: **Customize → Skills → „+" → „Upload a skill"**, wgraj ZIP,
   włącz przełącznikiem.

### Część 3: Przetestuj na fikcyjnym zestawieniu

7. Wgraj `zestawienie_miesieczne_PODSUMOWANIE.xlsx` i poproś:
   *„Przygotuj raport statusu wykonania budżetu za październik dla Pani
   Skarbnik: co idzie zgodnie z planem, gdzie są przekroczenia, jakie
   problemy wymagają decyzji."*
   Skill powinien rozpoznać „raport statusu" i użyć swojego formatu –
   sprawdź, czy struktura odpowiedzi różni się od zwykłej odpowiedzi Claude
   (porównaj z tym, co dostawałeś/aś w zadaniu 3).
8. Sprawdź drugi format – odpowiedź FAQ, czyli powtarzalne pytanie od
   wydziałów:
   *„Napisz odpowiedź FAQ dla wydziałów: dlaczego zestawienie miesięczne
   musi być bez scalonych komórek i w jednym formacie daty."*
   (Argumenty masz w Bloku B.)
9. Zanotuj, co w tych odpowiedziach **nie pasuje** do Urzędu – ton, język
   angielskie nazwy sekcji, brak zasad RODO, format kwot. To lista zmian
   do Części 4.

### Część 4: Dostosuj skill do Urzędu

10. W wypakowanym folderze `internal-comms` otwórz w Notatniku plik
    `examples/general-comms.md` i dopisz na górze sekcję z zasadami
    Urzędu, np.:

    ```markdown
    ## Zasady Urzędu Miejskiego w Opolu (obowiązują we wszystkich formatach)

    - Zawsze po polsku, nazwy sekcji po polsku.
    - Ton rzeczowy, urzędowy, ale bez żargonu i skrótów bez rozwinięcia.
    - Kwoty w PLN z separatorem tysięcy (np. 112 000 zł).
    - Bez nazwisk pracowników i mieszkańców (RODO) – piszemy o wydziałach
      i liczbach, nie o osobach.
    - Jeśli przyczyna odchylenia nie wynika z danych – napisz „do
      potwierdzenia z wydziałem", nie zgaduj.
    ```

11. W `SKILL.md` zmień w nagłówku `name:` na `komunikaty-urzad-opole` i
    dopisz w `description`, że dotyczy komunikatów Urzędu Miejskiego w
    Opolu (raporty statusu dla Skarbnika, FAQ dla wydziałów, aktualizacje
    dla kierownictwa).
12. Spakuj folder ponownie do ZIP, wgraj jako nowy skill, **wyłącz
    oryginalny** `internal-comms` (żeby się nie dublowały) i powtórz
    krok 7. Porównaj: to samo polecenie, ale odpowiedź powinna już
    przestrzegać zasad Urzędu.
13. Na koniec wyłącz skille, z których nie będziesz korzystać na co dzień.

## Na co zwrócić uwagę

- **Najbardziej przydatne skille dla Urzędu (`xlsx`, `pptx`, `docx`,
  `pdf`) są już wbudowane w claude.ai** – nie trzeba ich instalować. Warto
  natomiast wiedzieć, jakie zasady w nich siedzą: to tłumaczy, dlaczego
  Claude w Dniu 2 będzie pisał formuły zamiast wpisywać liczby.
- **Gotowy skill + własna sekcja zasad** (Część 4) to najczęstszy realny
  scenariusz: nie piszesz od zera (zad. 7), tylko dostosowujesz sprawdzony
  szablon. Sekcja zasad Urzędu z kroku 10 jest wielokrotnego użytku –
  ten sam blok wkleisz do każdego kolejnego skilla.
- `internal-comms` powstał z myślą o firmie („company-preferred formats").
  Formaty raportu statusu, FAQ czy aktualizacji dla kierownictwa pasują do
  urzędu, ale język i przykłady – nie. Stąd Część 4.
- **`description` mówi, kiedy skill się włączy, ale nie – co zrobi.** To,
  co robi, jest w `SKILL.md` i w `examples/`. Dlatego czytamy wszystko,
  nie tylko opis.
- W Urzędzie warto prowadzić **listę zainstalowanych skilli** (kto, co,
  skąd, kiedy, czy zmodyfikowany) – jak listę oprogramowania. Przy planie
  Team ([zadanie 6](06-plany-i-limity.md)) administrator IT widzi
  konektory, ale skille wgrane przez użytkowników warto zgłaszać samemu.

## Notatki własne

- Czy w Części 1 komórka „Razem" zawierała formułę, czy wpisaną liczbę?
- Które elementy odpowiedzi `internal-comms` (przed dostosowaniem)
  najbardziej nie pasowały do Urzędu?
- Jaki inny powtarzalny komunikat w Twoim wydziale (np. przypomnienie o
  terminie, odpowiedź na pytanie radnego) dodałbyś/dodałabyś jako kolejny
  przykład do `examples/`?
