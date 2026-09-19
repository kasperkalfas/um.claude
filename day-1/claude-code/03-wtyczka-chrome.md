# Zadanie 3: Wtyczka Claude in Chrome – instalacja i uprawnienia

> **Materiał wprowadzający**, ciąg dalszy [zadania 1](01-czym-jest-cowork.md).
> To osobne narzędzie od wbudowanej przeglądarki Cowork – warto poznać
> różnicę, zanim zaczniesz z niego korzystać.

**Cel:** zrozumieć, czym wtyczka **Claude in Chrome** różni się od
wbudowanej przeglądarki Cowork z zadania 1, zainstalować ją i świadomie
ustawić uprawnienia dla stron.
**Poziom:** podstawowy

## Czym jest Claude in Chrome

To **rozszerzenie do przeglądarki Chrome** – w odróżnieniu od wbudowanej
przeglądarki Cowork, działa **w Twojej prawdziwej, codziennej
przeglądarce**: na Twoich kartach, z Twoimi zalogowanymi sesjami i
kontami. Pozwala Claude klikać, wypełniać formularze, czytać treść stron
i robić zrzuty ekranu w Twoim imieniu.

## Wtyczka Chrome a wbudowana przeglądarka Cowork (zadanie 1) – to dwa różne narzędzia

| | Claude in Chrome (wtyczka) | Wbudowana przeglądarka Cowork |
|---|---|---|
| Gdzie działa | Twoja prawdziwa przeglądarka Chrome, z Twoimi loginami i sesjami | osobna, izolowana przeglądarka wewnątrz aplikacji Claude Desktop |
| Instalacja | trzeba doinstalować rozszerzenie z Chrome Web Store | nic nie instalujesz – jest od razu wbudowana |
| Ryzyko | wyższe – ma dostęp do wszystkiego, na czym akurat jesteś zalogowany/a w Chrome | niższe – osobna sesja, nie miesza się z Twoimi prywatnymi/służbowymi loginami |

Dostępność obu wybierasz w Ustawieniach – jedno nie wyklucza drugiego.

## Wymagania planu

Dostępne na planach płatnych: **Pro, Max, Team, Enterprise** – plan
**Team** Urzędu ([`../claude-zadania/06-plany-i-limity.md`](../claude-zadania/06-plany-i-limity.md))
jest objęty.

## Instalacja

1. Otwórz Chrome i wejdź na stronę rozszerzenia w Chrome Web Store
   (najprościej przez [claude.ai/chrome](https://claude.ai/chrome)).
2. Kliknij **„Add to Chrome"**, żeby dodać rozszerzenie.
3. Zaloguj się swoim kontem Claude.
4. **Przypnij rozszerzenie**: kliknij ikonę puzzli w pasku Chrome, potem
   pineskę przy „Claude" – żeby mieć do niego szybki dostęp.
5. Zaakceptuj wymagane uprawnienia przeglądarki, o które poprosi Chrome.

## Ustawienia – „Enable Claude in Chrome" i uprawnienia stron

To dokładnie ekran, który prawdopodobnie już widziałeś/aś:

- **„Enable Claude in Chrome"** – główny przełącznik włącz/wyłącz. Dotyczy
  **tylko wtyczki** – nie wpływa na wbudowaną przeglądarkę Cowork w
  aplikacji desktopowej.
- **„Site permissions"** – te uprawnienia dotyczą **obu** narzędzi naraz:
  wtyczki Claude in Chrome **i** wbudowanej przeglądarki w Claude
  Desktop.
- **„Default for all sites"** – decyduje, czy Claude ma domyślnie
  działać na każdej stronie, czy pytać/wymagać osobnej zgody dla
  konkretnej witryny. **Nie zostawiaj tego na najbardziej permisywnym
  ustawieniu** – patrz sekcja bezpieczeństwa niżej.

## Tryby zatwierdzania akcji (dropdown przy oknie czatu)

| Tryb | Co się dzieje |
|---|---|
| **Manual** (zalecany na start) | Claude zatrzymuje się i pyta o zgodę przed każdą akcją – Ty klikasz Zezwól/Odrzuć |
| **Auto** | Claude działa dalej, sam ocenia bezpieczeństwo każdej akcji, blokuje to, co uzna za niebezpieczne, i pyta tylko, gdy trzeba |
| **Skip** | Claude nic nie sprawdza i o nic nie pyta – tylko gdy w 100% ufasz zadaniu i stronie |

## Czego Claude nie zrobi niezależnie od trybu

Nawet po ustawieniu „zawsze zezwalaj" na danej stronie, Claude i tak
zapyta wprost o zgodę przed: pobraniem pliku, wpisaniem potencjalnie
wrażliwych danych na stronie, udzieleniem autoryzacji (np. OAuth).

Całkowicie zablokowane, niezależnie od trybu: zakupy/transakcje
finansowe, zakładanie kont, wpisywanie danych karty/dokumentów
tożsamości, trwałe usuwanie czegokolwiek, transakcje giełdowe.

## Uwaga bezpieczeństwa – ważniejsza niż przy Cowork z zadania 1

Skoro wtyczka działa **w Twojej prawdziwej przeglądarce**, ryzyko jest
wyższe niż przy izolowanej przeglądarce Cowork – jeśli jesteś zalogowany/a
w Chrome do prawdziwej poczty czy systemu Urzędu, Claude teoretycznie ma
do tego dostęp w tej samej sesji przeglądania:

- **Nie ustawiaj „Default for all sites" na szeroką, automatyczną zgodę**,
  jeśli w tej samej przeglądarce jesteś zalogowany/a do systemów
  służbowych Urzędu.
- Do testów używaj **osobnego profilu Chrome** albo przeglądarki, w
  której nie jesteś zalogowany/a do niczego służbowego – ta sama zasada,
  co przy Google Calendar i connectorze M365
  (patrz `../claude-zadania/04-google-calendar.md`).
- Zaczynaj od trybu **Manual**, żeby widzieć każdą akcję, zanim się
  wykona.
- Podłączenie wtyczki do realnych, służbowych kont/systemów Urzędu i
  działanie na nich wymaga tej samej pisemnej zgody Zamawiającego, co
  każda inna integracja (`CLAUDE.md`, sekcja o bezpieczeństwie danych).

## Kroki

1. Sprawdź plan (Ustawienia → Plan) – wtyczka wymaga konta płatnego.
2. Zainstaluj rozszerzenie z Chrome Web Store i zaloguj się.
3. Wejdź w ustawienia wtyczki → **Site permissions** → sprawdź, na co
   ustawione jest „Default for all sites" – jeśli jest zbyt szerokie,
   zawęź je.
4. W oknie czatu wybierz tryb **Manual**.
5. Przetestuj na neutralnej, publicznej stronie (np. poproś Claude o
   podsumowanie artykułu w Wikipedii albo wyszukanie czegoś w Google) –
   **nie na systemach ani skrzynce Urzędu**.
6. Obserwuj, o co Claude pyta przed wykonaniem akcji, i świadomie
   zatwierdzaj lub odrzucaj.

## Na co zwrócić uwagę

- To narzędzie o realnym dostępie do Twojej przeglądarki – traktuj je
  poważniej niż zwykłą rozmowę z Claude.
- „Site permissions" i „Default for all sites" to ustawienia **wspólne**
  dla wtyczki i wbudowanej przeglądarki Cowork – zmiana w jednym miejscu
  wpływa na oba narzędzia.
- Rozszerzenie wciąż jest wdrażane stopniowo („rolling out gradually") –
  jeśli go nie widzisz na swoim koncie, to nie błąd, tylko kwestia czasu.
- Jeśli pracujesz na komputerze służbowym Urzędu – dopilnuj, żeby
  „Default for all sites" nie był ustawiony szerzej, niż faktycznie
  potrzebujesz.

## Notatki własne

- Jak masz obecnie ustawione „Default for all sites" – czy świadomie, czy
  zostało domyślne?
- Do jakiego (nieistotnego, publicznego) zadania przetestowałbyś/abyś tę
  wtyczkę jako pierwsze, zanim rozważysz cokolwiek bardziej wrażliwego?
