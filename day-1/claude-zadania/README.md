# Zadania: Claude — Blok C, Dzień 1

Zestaw ćwiczeń praktycznych do szkolenia „Wykorzystanie systemu AI Claude we
współpracy z Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w
Opolu, prowadzący: Kasper Kalfas).

**Miejsce w agendzie:** Dzień 1, **Blok C (60 min, 9:45–10:45): Claude Czat
w przeglądarce** — pogłębione poznanie interfejsu Claude (funkcje, dobre
praktyki promptowania). Pełna agenda: `../../agenda/Agenda_szkolenia.md`.

Claude to asystent AI od firmy Anthropic – prowadzi rozmowę w naturalnym
języku (również po polsku), analizuje wgrane dokumenty i pomaga w pisaniu,
planowaniu oraz pracy z tekstem i arkuszami.

## Wymagania wstępne

- Przeglądarka internetowa i dostęp do [claude.ai](https://claude.ai).
- Adres e-mail lub konto Google do założenia konta.
- Ukończone 18 lat – tego wymaga regulamin usługi.

## Jak zacząć pracę z Claude

1. Wejdź na stronę [claude.ai](https://claude.ai).
2. Kliknij **"Sign up"** (Zarejestruj się), a jeśli masz już konto –
   **"Log in"** (Zaloguj się).
3. Wybierz sposób logowania:
   - **Kontem Google** – najszybciej, tym samym kontem co do Gmaila, albo
   - **adresem e-mail** – wtedy otrzymasz kod weryfikacyjny w wiadomości,
     który trzeba przepisać na stronie.
4. Po zalogowaniu zobaczysz pole do wpisania wiadomości na środku ekranu –
   to tutaj wpisujesz swoje pytania i polecenia.
5. Wpisz pierwszą wiadomość i naciśnij Enter. Nową rozmowę zaczniesz
   przyciskiem **"New chat"** (Nowa rozmowa); wcześniejsze rozmowy znajdziesz
   na liście po lewej stronie.

## ⚠️ Zasada bezpiecznego użycia danych (przypomnienie z Bloku B)

We wszystkich zadaniach poniżej pracujemy wyłącznie na danych
**fikcyjnych/zanonimizowanych**, wzorowanych na realnych procesach urzędu.
**Nie wklejaj i nie wgrywaj do Claude prawdziwych danych budżetowych z ERP
ani innych danych osobowych/poufnych urzędu** bez pisemnej zgody
Zamawiającego – to wymóg umowy szkoleniowej, nie tylko dobra praktyka.

## Spis zadań — Blok C, na żywo (60 min)

1. [01 – Formuła P.K.Z.O.](01-formula-pkzo.md) *(ok. 20 min)* – budowanie
   skutecznych promptów: Persona, Kontekst, Zadanie, Ograniczenia, na
   przykładach z pracy urzędu. Podstawa, z której korzystają kolejne
   zadania – nie pomijać.
2. [02 – Funkcje interfejsu Claude](02-funkcje-interfejsu.md) *(ok. 20 min)*
   – wgrywanie plików, Artifacts (tabele/dokumenty), styl odpowiedzi,
   pamięć, historia rozmów.
3. [03 – Bezpieczna analiza arkusza budżetowego](03-analiza-dokumentu-excel.md)
   *(ok. 20 min)* – Claude czyta fikcyjny plik Excel wzorowany na Procesie
   1, wykrywa typowe błędy z Bloku B i przygotowuje podsumowanie. Najbliższe
   temu, co czeka Was w Dniu 2.

To domyka Blok C. Materiał dodatkowy poniżej to praca własna, nie na żywo.

## Pliki wsadowe

Wszystkie w [`../materialy/`](../materialy/), wygenerowane wcześniej jako
fikcyjne dane wzorowane na Procesie 1 – zgodnie z zasadą bezpieczeństwa
powyżej.

| Plik | Używany w | Zawartość | Rola w ćwiczeniu |
|---|---|---|---|
| [`zestawienie_przykladowe.xlsx`](../materialy/zestawienie_przykladowe.xlsx) | [Zadanie 2](02-funkcje-interfejsu.md) oraz [Zadanie 8](08-skille-z-internetu.md), Część 1 | 7 wydziałów, wrzesień 2026, bez błędów | poznanie interfejsu (upload, Artifacts) na czystych danych; w zadaniu 8 – test zasady „formuły, nie wpisane wyniki" ze skilla `xlsx` (wiersz Razem) |
| [`zestawienie_miesieczne_PRZYKLAD.xlsx`](../materialy/zestawienie_miesieczne_PRZYKLAD.xlsx) | [Zadanie 3](03-analiza-dokumentu-excel.md), Część 1 (i punkt wyjścia do Części 3) | 9 wierszy (1 pusty), wrzesień 2026 | 3 celowe błędy z Bloku B: pusty wiersz (5), niespójny format daty (wiersze 4 i 8: „2026-09", „09.2026" zamiast „wrzesień 2026"), scalona komórka Miesiąc (D9:D10) – klucz odpowiedzi dla prowadzącego |
| [`zestawienie_miesieczne_PODSUMOWANIE.xlsx`](../materialy/zestawienie_miesieczne_PODSUMOWANIE.xlsx) | [Zadanie 3](03-analiza-dokumentu-excel.md), Część 2; [Zadanie 7](07-skill-notatka-budzetowa.md); [Zadanie 8](08-skille-z-internetu.md), Część 3 | 10 wydziałów, październik 2026, bez błędów | 7 z 10 wydziałów przekracza plan (od +112 000 do +7 000 zł) – limit „max 6 wierszy" w prompcie P.K.Z.O. wymusza realny wybór i sortowanie; w zadaniu 7 testuje własny skill (próg istotności 5% / 20 000 zł), w zadaniu 8 – raport statusu ze skilla `internal-comms` |

Zadania **bez pliku wsadowego** (celowo): 1 (samo promptowanie), 4 i 5
(pracują na prywatnym kalendarzu / konektorach podróży), 6 (lektura +
sprawdzenie własnego planu). W Części 3 zadania 3 uczestnik **sam** psuje
kolejną komórkę w pliku `zestawienie_miesieczne_PRZYKLAD.xlsx` (np. kwota
jako tekst) i wgrywa zmodyfikowaną kopię – nie ma osobnego pliku na ten
krok.

## Materiał dodatkowy — do samodzielnej pracy po szkoleniu

Poniższe zadania pokazują, jak podłączyć do Claude własne, **prywatne**
usługi (Kalendarz, wyszukiwarki podróży), jak rozumieć plany i limity
(w tym plan Team, na którym pracuje Urząd), jak zbudować własny skill do
cyklicznej notatki budżetowej i jak bezpiecznie korzystać z gotowych skilli
z internetu. Ciekawe i przydatne, ale **wykraczają poza zakres
60-minutowego Bloku C** – nie omawiamy ich na żywo.

**Zanim podłączysz jakąkolwiek usługę:**

1. **Podłączaj wyłącznie własne, prywatne konta** – nigdy skrzynki/dysku/
   kalendarza służbowego urzędu ani cudzego konta, bez pisemnej zgody i
   wiedzy IT/PNT. Ta sama zasada bezpieczeństwa danych z Bloku B dotyczy
   integracji z usługami, nie tylko wklejanych plików.
2. **Przeczytaj ekran zgód** przy podłączaniu – zobaczysz tam, do czego
   dokładnie przyznajesz dostęp (ten sam mechanizm, co logowanie przez
   Google do innych aplikacji).
3. **Po zakończeniu pracy odłącz usługi**, jeśli ćwiczysz na komputerze,
   który nie jest Twój – patrz „Jak odłączyć usługę" niżej.

### Jak podłączyć / odłączyć usługę

- **Podłączanie:** w oknie rozmowy kliknij **"Search and tools"** (przy
  polu wiadomości) → **"Add connectors"** (albo wejdź na
  [claude.ai/customize/connectors](https://claude.ai/customize/connectors)),
  znajdź usługę i kliknij **"Connect"**, zaloguj się i zaakceptuj zakres
  uprawnień.
- **Odłączanie:** wejdź w **Ustawienia → Connectors** na
  [claude.ai](https://claude.ai) i kliknij **"Disconnect"** przy wybranej
  usłudze. Dodatkowo możesz cofnąć dostęp po stronie Google:
  [myaccount.google.com/permissions](https://myaccount.google.com/permissions).

### Spis zadań dodatkowych

4. [04 – Google Calendar](04-google-calendar.md) – sprawdzanie dostępności,
   tworzenie i modyfikowanie wydarzeń (spotkania zespołu budżetowego z
   wydziałami).
5. [05 – Podróże: Booking.com i Kiwi.com](05-podroze-booking-kiwi.md) –
   wyszukiwanie lotów i noclegów, porównanie ofert; z rozróżnieniem od
   procedury delegacji służbowej.
6. [06 – Plany i limity](06-plany-i-limity.md) – darmowy Claude, plan Team
   Urzędu (miejsca Standard/Premium), Claude Code (CLI) i jego limity.
7. [07 – Własny skill: notatka o odchyleniach budżetowych](07-skill-notatka-budzetowa.md)
   – budowa własnego skilla od zera (próg istotności, dwa formaty:
   wewnętrzny i dla banku/rady miasta); wymaga włączonego wykonywania kodu
   w Ustawieniach.
8. [08 – Gotowe skille z internetu](08-skille-z-internetu.md) – przegląd
   oficjalnego repozytorium Anthropic pod kątem przydatności w Urzędzie
   (`xlsx`/`pptx`/`docx`/`pdf` – wbudowane, warto znać zasady;
   `internal-comms` – do instalacji), checklist bezpieczeństwa, instalacja
   `internal-comms`, test na fikcyjnym zestawieniu i **dostosowanie skilla
   do zasad Urzędu**. Najlepiej po zadaniu 7.

## Jak korzystać z tych plików

Każdy plik `.md` można otworzyć w dowolnym edytorze tekstu lub czytniku
Markdown. Uczestnicy zapisują swoje odpowiedzi bezpośrednio pod pytaniami w
sekcji "Notatki własne" na końcu każdego zadania.
