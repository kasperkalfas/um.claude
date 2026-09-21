# Zadanie 4: Google Calendar – planowanie spotkań

> **Materiał dodatkowy – poza Blokiem C.** Nie wchodzi w zakres 60-minutowego
> bloku „Claude Czat w przeglądarce" (tam ćwiczymy formułę P.K.Z.O., interfejs
> i bezpieczną analizę arkusza – zadania 1–3). To zadanie do samodzielnej
> pracy po szkoleniu. **Podłączaj wyłącznie własne, prywatne konto Google –
> nigdy oficjalnego systemu/konta urzędu bez pisemnej zgody i wiedzy IT/PNT**
> (zasada z Bloku B dotyczy też integracji, nie tylko wklejanych danych).

**Cel:** podłączyć kalendarz Google i zlecić Claude realne zadania
planistyczne: sprawdzenie dostępności, utworzenie i modyfikację wydarzenia.
**Poziom:** średniozaawansowany

## Materiały

- Konto Claude z podłączonym kontem Google – instrukcja podłączania i
  odłączania usług w [README](README.md#jak-podłączyć--odłączyć-usługę).
- Własny, prywatny kalendarz Google.

## Zanim zaczniesz

W odróżnieniu od Gmaila, konektor kalendarza ma pełne uprawnienia
**do zapisu**: Claude może tworzyć, zmieniać i **usuwać** wydarzenia.
Ćwicz na wydarzeniach testowych, nie na prawdziwych spotkaniach, i czytaj
uważnie, co Claude proponuje zrobić, zanim potwierdzisz.

## Kroki

1. Podłącz **Google Calendar** w menu **"Search and tools" → "Add
   connectors"** (pełna instrukcja w README, sekcja „Jak podłączyć /
   odłączyć usługę").
2. Zacznij od odczytu – poproś o podsumowanie:

   ```
   Pokaż moje wydarzenia z najbliższych 7 dni w formie listy: data,
   godzina, nazwa. Zaznacz dni, w których nie mam nic zaplanowanego.
   ```

3. Poproś o znalezienie wolnego terminu:

   ```
   Znajdź w przyszłym tygodniu dwa wolne terminy po 60 minut, między 9:00
   a 15:00, w dni robocze.
   ```

4. Utwórz wydarzenie testowe promptem P.K.Z.O., np.:

   ```
   P: Jesteś asystentem organizującym moje spotkania.
   K: Planuję cykliczne spotkanie zespołu ds. zestawień budżetowych
      z przedstawicielami wydziałów urzędu.
   Z: Utwórz w moim kalendarzu wydarzenie testowe.
   O: Nazwa "TEST – spotkanie zespołu budżetowego", w przyszły wtorek
      o 10:00, czas trwania 45 minut, z opisem zawierającym trzy punkty
      agendy (np. przegląd wykonania budżetu, przygotowanie zestawienia
      miesięcznego, pytania do wydziałów).
   ```

5. Sprawdź w Google Calendar, czy wydarzenie się pojawiło i czy zgadzają
   się szczegóły.
6. Poproś o modyfikację:

   ```
   Przesuń wydarzenie TEST o godzinę później i dodaj link do Google Meet.
   ```

7. Na koniec posprzątaj: *"Usuń wydarzenie TEST z mojego kalendarza."*
   Sprawdź w kalendarzu, czy faktycznie zniknęło.

## Na co zwrócić uwagę

- **Zawsze weryfikuj efekt w samym kalendarzu.** Claude potwierdzi, że
  wykonał zadanie – ale to Ty odpowiadasz za to, co znalazło się w Twoim
  kalendarzu.
- Uważaj na polecenia usuwające. Sformułowanie w stylu *"wyczyść mi
  przyszły tydzień"* może usunąć więcej, niż zamierzasz. Bądź konkretny/a
  i najpierw poproś o listę tego, co ma zostać usunięte.
- Kalendarz to dane osobowe także innych osób – nazwy spotkań i listy
  uczestników. Dlatego to zadanie robimy tylko na prywatnym kalendarzu,
  nigdy na kalendarzu służbowym urzędu bez zgody IT/PNT.
- Największa realna oszczędność czasu w pracy urzędu to szukanie wspólnych
  terminów na spotkania z wydziałami i przypominanie o cyklicznych
  terminach (np. co miesiąc: zamknięcie zestawienia, przygotowanie
  materiału dla banku) – to właśnie ten mechanizm.

## A co z Outlookiem / kalendarzem Microsoft? (realia Urzędu)

To ćwiczenie robimy na **Google Calendar**, bo można je bezpiecznie wykonać
na własnym, prywatnym koncie. Urząd pracuje jednak w środowisku
**Microsoft 365**, więc warto wiedzieć, że mechanizm ma swój odpowiednik:
**connector Microsoft 365** (Outlook Mail, Outlook Kalendarz, OneDrive/
SharePoint, Teams). Działa analogicznie do Google Calendar – Claude może
czytać wydarzenia, a z włączonymi narzędziami zapisu także tworzyć,
edytować i usuwać wpisy w kalendarzu oraz wysyłać maile.

Formalnie jest to osobny produkt w Microsoft Marketplace –
[„M365 Connector for Claude" by Anthropic](https://marketplace.microsoft.com/pl-pl/product/saas/anthropic.microsoft-365-connector-for-claude?tab=overview)
– czyli aplikacja SaaS, którą **admin Microsoft 365 po stronie Urzędu**
musiałby świadomie zainstalować/autoryzować w swoim tenancie (podobnie
jak każdą inną aplikację z Marketplace wymagającą zgody na uprawnienia).

**Dostępność i wymagania (stan: wrzesień 2026, wg support.claude.com i
wpisu w Microsoft Marketplace):**

- Connector M365 jest dostępny na wszystkich planach, w tym na planie
  **Team**, na którym pracuje Urząd (patrz `06-plany-i-limity.md`).
- Wymaga **konta firmowego** – Microsoft Entra tenant na planie biznesowym
  (prywatne konto @outlook.com/@hotmail.com nie zadziała).
- Wymaga **jednorazowej zgody administratora** (Global Administrator
  Microsoft Entra po stronie IT Urzędu – to on instaluje/autoryzuje
  connector z Marketplace), a w organizacji na planie Team/Enterprise
  dodatkowo właściciel organizacji na Claude musi najpierw włączyć
  connector – dopiero potem poszczególni pracownicy łączą się
  indywidualnie.
- Uprawnienia są **delegowane** – Claude widzi tylko to, do czego dany
  pracownik już ma dostęp w M365, nie omija istniejących uprawnień.
- **Domyślnie tylko odczyt** (read-only) dla maila, kalendarza, czatu i
  SharePoint – zapis (wysyłanie maili, tworzenie/usuwanie wydarzeń,
  wiadomości na Teams) jest **zablokowany domyślnie** i admin musi go
  świadomie włączyć osobno.
- Architektura: to "Anthropic-hosted" proxy – dokumenty/maile/pliki
  fizycznie zostają w tenancie Microsoft Urzędu, ale **treść jest pobierana
  i przetwarzana przez Anthropic w momencie zapytania** (nie jest to więc
  sytuacja, w której dane "nigdy nie opuszczają Microsoftu"). Wyniki
  wywołań narzędzia (tool calls), jeśli chat jest zapisywany, **są
  zapisywane razem z tą rozmową** – czyli fragment maila/wydarzenia
  pobrany przez connector może zostać zapisany w historii czatu Claude.

**Uwaga kluczowa:** to już nie jest ćwiczenie na prywatnych, testowych
danych, tylko żywe podłączenie do realnej skrzynki/kalendarza, w którym
treść realnie przepływa przez systemy Anthropic i może zostać zapisana w
historii czatu. Zgodnie z zasadą z Bloku B i z `CLAUDE.md` (sekcja o
bezpieczeństwie danych), podłączenie connectora M365 do **służbowego**
konta Urzędu — i tym bardziej jakiekolwiek działanie na realnych danych
osobowych/poufnych przez ten connector — wymaga pisemnej zgody
Zamawiającego oraz ustaleń z IT/PNT, dokładnie tak samo jak w przypadku
kalendarza Google. To ćwiczenie na żywo pokazujemy więc tylko na koncie
demo/testowym, nigdy na prawdziwej skrzynce uczestniczek szkolenia.

## Notatki własne

- Czy Claude poprawnie zrozumiał określenia względne ("przyszły wtorek",
  "za dwa tygodnie")?
- Jakie zadanie kalendarzowe wykonujesz najczęściej w swojej pracy (np.
  umawianie spotkań z wydziałami, pilnowanie terminów sprawozdań) i czy
  dałoby się je w ten sposób przyspieszyć?
