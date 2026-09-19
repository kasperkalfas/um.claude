# Zadanie 1: Czym jest Claude Cowork i jak go zainstalować

> **Materiał wprowadzający.** To nie jest Claude Code (CLI z terminala) –
> Cowork to osobny produkt: wizualny, agentowy tryb pracy dostępny na
> stronie/w aplikacji Claude, bez terminala. Ten plik tylko wyjaśnia, czym
> jest i jak zacząć – nie jest częścią 60-minutowego Bloku C (patrz
> `../claude-zadania/README.md`).

**Cel:** zrozumieć, czym Claude Cowork różni się od zwykłej rozmowy z
Claude, sprawdzić dostępność na koncie Urzędu (plan Team) i zainstalować
dostęp (desktop/web).
**Poziom:** podstawowy

## Czym jest Claude Cowork

Cytat z oficjalnej strony produktu ([claude.com/product/cowork](https://claude.com/product/cowork)):

> "Claude Cowork completes tasks you can steer from anywhere. Give it a
> goal, and it works across your files and tools. You come back to
> polished work for your review."

Po polsku: **nie mówisz Claude krok po kroku, co ma zrobić – podajesz
cel**, a Claude sam:

- pracuje w Twoich plikach i podłączonych narzędziach (nie tylko w oknie
  czatu),
- w razie potrzeby otwiera i obsługuje przeglądarkę (wbudowaną,
  **oddzielną od Twojej prywatnej przeglądarki i loginów**),
- pokazuje na bieżąco, co robi – jakie pliki otworzył, jakich narzędzi
  użył, jakie decyzje podjął – więc możesz to śledzić i przekierować,
- działa **zdalnie, w chmurze** – zadanie leci dalej, nawet gdy zamkniesz
  laptopa,
- potrafi rozbić zadanie na części i pracować nad nimi równolegle
  (research + porządkowanie + szkic naraz),
- da się **zaplanować cyklicznie** (codziennie/co tydzień/co miesiąc) –
  np. cotygodniowy raport.

**W skrócie dla tej grupy**: to mechanizm Claude Code (agentowe,
wieloetapowe wykonywanie zadań) przeniesiony do zwykłego interfejsu –
bez terminala, klikane myszką.

## Na jakim planie działa

Wymaga **konta płatnego** – nie ma tego na planie darmowym:

| Platforma | Wymagany plan |
|---|---|
| Desktop (macOS/Windows) | Pro, Max, Team, Enterprise |
| Web (claude.ai) | Pro, Max, Team; Enterprise tam, gdzie włączone |
| Mobile (iOS/Android) | Pro, Max, Team; Enterprise tam, gdzie włączone |
| Panel boczny w Chrome | Max, Team; Pro w trakcie wdrażania |

Urząd pracuje na planie **Team** (patrz [`../claude-zadania/06-plany-i-limity.md`](../claude-zadania/06-plany-i-limity.md))
– Cowork jest więc dostępny na obu typach miejsc (Standard/Premium), bez
dodatkowej licencji.

## Jak zainstalować / uruchomić

### Wersja web (najprostsza, nic nie instalujesz)

1. Wejdź na [claude.ai](https://claude.ai) i zaloguj się.
2. Przy polu wiadomości poszukaj przycisku **"Cowork"** obok "Chat".
   *Jeśli go nie widzisz* – masz najnowszy, ujednolicony interfejs, w
   którym każda rozmowa może przejść w tryb Cowork automatycznie, gdy
   zadanie tego wymaga.
3. Opisz cel zadania (nie instrukcję krok po kroku).
4. Claude pokaże swoje podejście do zadania – **zatwierdź, zanim zacznie
   działać**.

### Aplikacja desktopowa (potrzebna do dostępu do plików lokalnych i
przeglądarki na Twoim komputerze)

1. Wejdź na [claude.ai/download](https://claude.ai/download).
2. Wybierz swój system (Windows 10+ lub macOS 11+) i pobierz instalator.
3. Otwórz pobrany plik, żeby zainstalować.
4. Uruchom Claude – z Menu Start (Windows) albo z folderu Aplikacje
   (Mac).
5. Zaloguj się swoim kontem Claude.
6. Aplikacja musi być **otwarta przez cały czas trwania zadania** – to
   przez nią Cowork sięga do plików i przeglądarki na Twoim komputerze.


## Uwaga bezpieczeństwa – ta sama zasada co przy connectorach

Cowork ma **dostęp do internetu i może samodzielnie przeglądać strony,
wypełniać formularze** – to realne, unikalne ryzyko (cytat z dokumentacji
Anthropic: „Cowork has unique risks due to its agentic nature and
internet access"). Obowiązuje więc dokładnie ta sama zasada, co przy
Google Calendar czy connectorze M365
(patrz `../claude-zadania/04-google-calendar.md`):

- **Testuj na fikcyjnych plikach/folderach**, nie na realnych danych
  budżetowych czy osobowych Urzędu.
- Podłączenie Cowork do **służbowych** zasobów Urzędu (dyski sieciowe,
  skrzynki, systemy) wymaga pisemnej zgody Zamawiającego i ustaleń z
  IT/PNT – zgodnie z `CLAUDE.md` (sekcja o bezpieczeństwie danych).
- Zacznij od trybu **Manual**, żeby widzieć i zatwierdzać każdy krok,
  zanim przejdziesz na szybszy, ale mniej nadzorowany tryb.

## Kroki

1. Sprawdź, na jakim planie pracujesz (Ustawienia → Plan) – Cowork wymaga
   płatnego konta (Pro/Max/Team/Enterprise).
2. Zainstaluj aplikację desktopową albo po prostu otwórz claude.ai w
   przeglądarce (do pierwszego testu wystarczy wersja web).
3. Ustaw tryb uprawnień na **Manual** w Ustawieniach → Cowork.
4. Stwórz na komputerze **testowy, pusty folder z fikcyjnymi plikami**
   (np. skopiuj do niego `zestawienie_przykladowe.xlsx` z
   `../materialy/`).
5. Uruchom Cowork i podaj cel, np.: *„Przejrzyj pliki w tym folderze i
   przygotuj krótkie podsumowanie tego, co w nich jest."*
6. Obserwuj krok po kroku, co Claude robi (jakie pliki otwiera, jakich
   narzędzi używa) i zatwierdzaj kolejne kroki w trybie Manual.

## Na co zwrócić uwagę

- To narzędzie do **celu**, nie do instrukcji krok po kroku – im
  precyzyjniej opiszesz oczekiwany efekt końcowy, tym lepiej Cowork sobie
  poradzi.
- Zadanie działa dalej, nawet gdy zamkniesz laptopa (wersja web/mobile) –
  warto to świadomie wykorzystać do dłuższych, powtarzalnych prac.
- Usunięte zadanie znika z backendu Anthropic **w ciągu 30 dni** – to
  informacja o retencji danych, nie o natychmiastowym usunięciu.
- Obecnie nie da się udostępnić całej sesji Cowork innej osobie – da się
  udostępnić tylko pojedyncze wytworzone pliki (artefakty).

## Notatki własne

- Jakie powtarzalne zadanie w Twojej pracy nadawałoby się na test Cowork
  (na fikcyjnych danych), zamiast robić je ręcznie co miesiąc?
- Który tryb uprawnień (Manual/Auto/Skip) wybrałbyś/wybrałabyś na
  początek i dlaczego?
