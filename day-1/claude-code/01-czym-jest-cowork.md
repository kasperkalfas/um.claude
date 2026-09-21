# Zadanie 1: Czym jest Claude Cowork i jak go zainstalować

> **Materiał wprowadzający** (poza Blokiem C). Cowork to **nie** Claude
> Code z terminala – to osobny, klikany tryb pracy w aplikacji Claude.

**Cel:** uruchomić Cowork na koncie Urzędu (plan Team) i wykonać w nim
pierwsze zadanie na fikcyjnym folderze.
**Poziom:** podstawowy
**Czas:** ok. 15 minut

## Czym jest Cowork – w trzech zdaniach

W Claude Czat prowadzisz rozmowę krok po kroku. W Cowork **podajesz cel**,
a Claude sam pracuje w Twoich plikach i narzędziach, pokazuje na bieżąco,
co robi, i oddaje gotowy wynik do przejrzenia. To ten sam „silnik" co
Claude Code (zadanie 2), tylko bez terminala.

Wymaga konta płatnego (Pro/Max/Team/Enterprise) – plan **Team** Urzędu
jest objęty ([`../claude-zadania/06-plany-i-limity.md`](../claude-zadania/06-plany-i-limity.md)).

## Zasada bezpieczeństwa

Cowork ma dostęp do internetu i może samodzielnie klikać po stronach.
Dlatego:

- testujesz **tylko na fikcyjnych plikach** w osobnym folderze,
- podłączenie do zasobów służbowych (dyski, poczta, systemy) wymaga
  pisemnej zgody Zamawiającego i ustaleń z IT,
- zaczynasz od trybu **Manual** – widzisz i zatwierdzasz każdy krok.

## Kroki

1. **Sprawdź plan.** Ustawienia → Plan. Musi być Pro, Max, Team lub
   Enterprise.
2. **Wybierz wersję.** Do pierwszego testu wystarczy [claude.ai](https://claude.ai)
   w przeglądarce. Aplikacja desktopowa ([claude.ai/download](https://claude.ai/download),
   Windows 10+ / macOS 11+) jest potrzebna dopiero, gdy Cowork ma pracować
   na plikach z Twojego dysku – i musi być wtedy otwarta przez cały czas
   trwania zadania.
3. **Ustaw tryb Manual.** Ustawienia → Cowork → tryb uprawnień → **Manual**.
4. **Przygotuj folder testowy.** Utwórz na Pulpicie pusty folder
   `cowork-test` i skopiuj do niego `../materialy/zestawienie_przykladowe.xlsx`.
5. **Uruchom Cowork.** Przy polu wiadomości kliknij **Cowork** (obok
   „Chat"). Jeśli nie widzisz przycisku – masz nowszy interfejs, w którym
   rozmowa sama przechodzi w tryb Cowork, gdy zadanie tego wymaga.
   Wskaż folder `cowork-test` i podaj cel:

   ```
   Przejrzyj pliki w tym folderze i przygotuj krótkie podsumowanie tego,
   co w nich jest.
   ```

6. **Zatwierdź plan.** Cowork najpierw pokaże, jak zamierza to zrobić –
   przeczytaj i zatwierdź.
7. **Obserwuj i zatwierdzaj.** W panelu bocznym widać, jakie pliki otwiera
   i jakich narzędzi używa. W trybie Manual każdy krok czeka na Twoje
   „Zezwól".

**Sprawdź:**

- [ ] podsumowanie wymienia plik `zestawienie_przykladowe.xlsx` i jego
      kolumny (Dział, Kwota planowana, Kwota wykonana, Miesiąc)
- [ ] Cowork nie wyszedł poza folder `cowork-test`

## Na co zwrócić uwagę

- Opisuj **efekt końcowy**, nie kolejne kliknięcia – im precyzyjniej, tym
  lepszy wynik.
- W wersji web zadanie leci dalej, nawet gdy zamkniesz laptopa – przydatne
  przy dłuższych, powtarzalnych pracach; Cowork da się też **zaplanować
  cyklicznie** (np. cotygodniowy raport).
- Nie da się udostępnić całej sesji Cowork innej osobie – tylko
  pojedyncze wytworzone pliki. Usunięte zadanie znika z serwerów Anthropic
  w ciągu 30 dni.

## Notatki własne

- Jakie powtarzalne zadanie z Twojej pracy nadawałoby się na test Cowork
  (na fikcyjnych danych)?
- Który tryb uprawnień (Manual/Auto/Skip) wybrałbyś/wybrałabyś na
  początek i dlaczego?
