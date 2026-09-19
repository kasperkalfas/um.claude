# Zadanie 6: Plany i limity – darmowy Claude, plan Team urzędu, Claude Code

> **Materiał dodatkowy – poza Blokiem C.** Urząd pracuje na planie **Team**
> (szczegóły w ściągawce niżej), więc na szkoleniu limity nie są problemem –
> ale warto rozumieć, czym plan Team różni się od darmowego konta, na którym
> być może ćwiczycie po godzinach, i co z tego wynika dla Claude Code.

**Cel:** zrozumieć, co obejmuje darmowy plan claude.ai, na czym polega plan
Team, na którym pracuje Urząd, oraz czym jest Claude Code (narzędzie CLI) i
od jakiego planu jest dostępne.
**Poziom:** podstawowy

## Materiały

- Przeglądarka i strona [claude.ai/pricing](https://claude.ai/pricing).
- Własne konto Claude (z zadania 1).

## Kroki

1. Wejdź na [claude.ai/pricing](https://claude.ai/pricing) i porównaj
   dostępne plany (Free, Pro, Max, Team, Enterprise).
2. W swoim koncie sprawdź, na jakim planie obecnie pracujesz (ikona/avatar
   w lewym dolnym rogu).
3. Przeczytaj poniższą ściągawkę i zastanów się, czy Twoje dotychczasowe
   użycie Claude mieściło się w limitach darmowego planu.

## Ściągawka: co obejmuje darmowa wersja Claude (claude.ai)

**Objęte:**

- Czat na web/iOS/Android/desktop, dostęp do modeli **Sonnet i Haiku**
  (najmocniejszy model Opus wymaga planu płatnego) – z wyraźnie niższymi
  limitami niż w planach płatnych.
- Okno kontekstu: **200k tokenów** (tyle samo co w planach płatnych).
- Web search, pamięć między rozmowami, tworzenie plików i wykonywanie
  kodu, generowanie treści/wizualizacji danych.
- Rozszerzone myślenie (extended thinking) do trudniejszych zadań.
- Integracje ze Slack, Google Workspace, konektory MCP, rozszerzenia
  desktopowe.

**Limity liczby wiadomości:** Anthropic nie podaje sztywnej liczby (np.
"X wiadomości dziennie") – limity są dynamiczne i zależą od obciążenia
serwerów. Plan Pro ma limity wielokrotnie wyższe niż plan darmowy; limit
odnawia się co kilka godzin.

**Czego NIE ma w darmowym planie:** dostępu do Claude Code CLI – to
zaczyna się dopiero od planu **Pro**.

## Ściągawka: plan Team – na takim pracuje Urząd Miejski w Opolu

Urząd ma licencję na planie **Team**, więc to on jest realnie istotny dla
uczestników (ważniejszy niż darmowy plan opisany wyżej).

**Dwa typy miejsc (seat) w jednej organizacji – można je mieszać:**

| | Standard | Premium |
|---|---|---|
| Cena (rozliczenie roczne) | ok. 20 USD/os./mies. | ok. 100 USD/os./mies. |
| Cena (rozliczenie miesięczne) | ok. 25 USD/os./mies. | ok. 125 USD/os./mies. |
| Limit użycia | wszystkie funkcje Claude, więcej niż w planie Pro | ok. **5×** więcej niż Standard |

- Plan Team wymaga min. **2 miejsc** i skaluje się (samoobsługowo) do ok.
  **150 miejsc** – powyżej tego wchodzi się w plan Enterprise (dodatkowo:
  SSO/SCIM zaawansowane, audit logi, IP allowlisting, custom retention
  danych itd.).
- Administrator organizacji (np. dział IT Urzędu) decyduje, kto dostaje
  jakie miejsce – w praktyce osoby intensywnie korzystające z Claude Code
  (CLI) często dostają Premium ze względu na wyższy limit, ale **dostęp do
  Claude Code mają oba typy miejsc**, nie tylko Premium.

**Co obejmuje plan Team (ponad to, co jest w planie darmowym/Pro):**

- Dostęp do modeli **Fable, Opus, Sonnet i Haiku** (najmocniejszy model –
  Opus – niedostępny w planie darmowym).
- Okno kontekstu do **1 mln tokenów** (zależnie od modelu; w praktyce
  dużo więcej niż standardowe 200k).
- **Claude Code** i **Claude Cowork**, a także Claude Design, Slides,
  Docs, Claude Science.
- Integracja z **Microsoft 365**, wyszukiwanie w danych całej organizacji
  ("enterprise search"), konektory MCP.
- Administracja: centralny billing na jedną fakturę, **SSO** (logowanie
  firmowym kontem), kontrola nad tym, jakie konektory (lokalne/zdalne)
  wolno podłączać pracownikom, zdalne zarządzanie aplikacją desktopową.
- **Domyślnie brak trenowania modeli na danych organizacji** – to istotne
  z punktu widzenia klauzuli poufności w umowie szkoleniowej (patrz
  `CLAUDE.md` → sekcja o bezpieczeństwie danych), ale **nie zwalnia** to z
  zakazu wprowadzania danych osobowych/poufnych bez pisemnej zgody –
  ustawienie "bez trenowania" dotyczy tego, czy Anthropic uczy się na
  danych, a nie tego, czy dane trafiają do systemu AI w ogóle.

> Ceny i limity zmieniają się – przed szkoleniem/rozmową z Urzędem warto
> zweryfikować aktualny stan na [claude.com/pricing](https://claude.com/pricing)
> (kwoty powyżej pochodzą z tej strony, stan na wrzesień 2026).

## Ściągawka: Claude Code CLI – ile tokenów?

Nie ma jednej odpowiedzi "X tokenów" – zależy od sposobu autoryzacji:

| Sposób dostępu | Jak liczone są limity |
|---|---|
| **Plan Pro/Max/Team/Enterprise** (logowanie przez `/login`) | Limit "miejsca" (seat allowance) w oknie **5-godzinnym** i **tygodniowym**, współdzielony z czatem Claude i Cowork. Konkretna liczba tokenów zależy od poziomu miejsca (Standard/Premium) i nie jest podana jako sztywna liczba – zużycie widać komendą `/usage` w CLI. |
| **Klucz API** (Claude Console, pay-as-you-go) | Brak górnego limitu poza budżetem, który sam ustawisz (workspace spend limits); płacisz za każdy token wg cennika API. |
| **Amazon Bedrock / Vertex / Foundry** | Rozliczane per token przez dostawcę chmury. |

Orientacyjny koszt dla firm (dane Anthropic): ok. **13 USD/dzień** i
**150–250 USD/miesiąc** na aktywnego developera (90% użytkowników poniżej
30 USD/dzień) – to zużycie tokenów API, nie darmowy limit.

**Podsumowanie:** Claude Code nie działa w ogóle na darmowym koncie –
wymaga minimum planu Pro (limity odnawiane w oknach 5-godzinnych
i tygodniowych, bez sztywnej liczby tokenów) albo płatnego klucza API
(bez górnego limitu, płatność za tokeny).

## Na co zwrócić uwagę

- Darmowy plan w zupełności wystarcza do zadań z tego warsztatu (czat,
  analiza dokumentów, pisanie) – limit dotyczy liczby wiadomości, nie
  funkcji.
- Limity i ceny zmieniają się – warto zawsze sprawdzić aktualny stan na
  [claude.ai/pricing](https://claude.ai/pricing) przed szkoleniem.

## Notatki własne

- Na jakim planie pracujesz na co dzień?
- Czy limit wiadomości darmowego planu kiedykolwiek Ci przeszkodził?
