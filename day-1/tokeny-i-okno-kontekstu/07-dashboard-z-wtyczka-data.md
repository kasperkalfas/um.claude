# Zadanie 7: Od surowego Excela do dashboardu – wtyczka Data w Cowork

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**demo prowadzącego na koniec Bloku D** albo praca własna po szkoleniu).

**Cel:** przejść cały przepływ pracy analityka danych jedną wtyczką:
poznaj dane → sprawdź jakość → wyczyść → zbuduj interaktywny dashboard –
i zobaczyć, jak komendy `/`, skille i subagenci z zadania 6 działają w
praktyce.
**Poziom:** średni (praktyka w Cowork)
**Czas:** ok. 25 minut (w tym kilka minut czekania na dashboard)
**Wymaga:** Claude Cowork (aplikacja desktopowa), konto w planie Team
Urzędu, zainstalowana wtyczka **Data** (krok 1).

## Problem, który to rozwiązuje

Zanim zestawienie trafi do prezentacji dla interesariuszy (Proces 3),
ktoś musi: otworzyć plik, sprawdzić, czy nie ma pustych wierszy i
dziwnych dat, poprawić je, policzyć plan vs wykonanie i zrobić wykresy.
To praca na godziny. Wtyczka Data ma te kroki opisane jako komendy –
uruchamiacie je po kolei, a Wy zostajecie tym, kto **sprawdza i decyduje**.

## Materiały

Folder roboczy na Pulpicie: `C:\Users\<Wy>\Desktop\analiza-danych\`, a w nim
**kopie** dwóch fikcyjnych plików z tego repozytorium:

| Plik | Skąd | Do czego |
|---|---|---|
| `zestawienie_miesieczne_PRZYKLAD.xlsx` | `../materialy/` | 8 wydziałów (9 wierszy, 1 pusty), plan/wykonanie za wrzesień; **3 celowe błędy**: pusty wiersz (5), niespójne formaty miesiąca (`wrzesień 2026` / `2026-09` / `09.2026`, wiersze 4 i 8), scalona komórka Miesiąc D9:D10 (ostatni wiersz wygląda na pusty) | kroki 3–5 (poznaj, sprawdź, wyczyść) |
| `zestawienie_roczne_2026.xlsx` | `../claude-code-cli/materialy/` | arkusz `Wykonanie`: 8 działów (600–926), plan roczny, wykonanie za miesiące I–VIII | krok 6 (dashboard) |

> Pliki są fikcyjne. Do folderu roboczego **nie kopiujemy** prawdziwych
> zestawień Urzędu. Przed startem zamknijcie oba pliki w Excelu – agent
> będzie je czytał i zapisywał nowe wersje obok.

## Kroki

1. **Instalacja wtyczki (raz).** W Cowork: pasek po lewej → **Customize**
   → **Browse plugins** → kategoria **Data** („Write SQL, explore
   datasets, build visualizations and dashboards") → **Install**. Po
   instalacji w **Customize → Personal plugins → Data** zajrzyjcie do
   trzech zakładek:
   - **Skills** – m.in. `data-visualization` (kiedy wykres liniowy, kiedy
     słupkowy, czego nie robić, dostępność kolorów) i `statistical-analysis`;
     otwórzcie jeden `SKILL.md` – to wiedza analityka spisana po ludzku;
   - **Connectors** – źródła danych (bazy, hurtownie); **nic nie podpinamy**;
   - **Commands** – `/explore-data`, `/validate`, `/create-viz`,
     `/build-dashboard`… Kliknijcie `/create-viz` i przeczytajcie opis
     przepływu (źródło → typ wykresu → cel → odbiorca). To jest „komenda =
     opisany przepływ pracy" z zadania 6.
2. **Folder roboczy.** Nowe zadanie (**New task**) → wybór folderu
   (*Choose a different folder*) → `Pulpit\analiza-danych` → **Allow**.
   Wybierzcie najmocniejszy dostępny model (Opus).
3. **Poznaj dane.** Wpiszcie `/` – zobaczycie listę komend, konektorów i
   skilli. Wybierzcie `/explore-data` (pełna nazwa: `/data:explore-data`;
   dokładne nazwy komend mogą się różnić między wersjami wtyczki – po
   wpisaniu `/` wybierajcie z listy, nie z pamięci).
   Na pytanie o źródło odpowiedzcie: *arkusz Excel, plik
   `zestawienie_miesieczne_PRZYKLAD.xlsx`*. Po prawej stronie pojawi się
   lista podzadań (wczytaj → profil kolumn → jakość → rekomendacje) –
   obserwujcie, jak agent je odhacza. **Sprawdźcie wynik z kluczem:**
   czy wykrył pusty wiersz, trzy formaty miesiąca i scaloną komórkę
   (agent może ją zgłosić jako „brak miesiąca w ostatnim wierszu")?
   Jeśli czegoś nie wykrył – zapiszcie co.
4. **Sprawdź jakość.** `/validate` (`/data:validate`) na tym samym pliku.
   Agent sprawdzi metodykę, wyrywkowo przeliczy wartości i przygotuje
   raport z sekcją „zastrzeżenia dla odbiorców". Porównajcie z
   krokiem 3: czy raport walidacji dodał coś nowego?
5. **Wyczyść – do nowego pliku.** Zwykłym poleceniem (bez komendy):
   *„Wyczyść dane: usuń pusty wiersz, ujednolić kolumnę Miesiąc do formatu
   `2026-09`, rozdziel scaloną komórkę i uzupełnij miesiąc w ostatnim
   wierszu. Zapisz
   wynik jako `zestawienie_miesieczne_PRZYKLAD_v1.xlsx` – **nie nadpisuj
   oryginału**."* Zwróćcie uwagę, że agent sięga po skill Excel, a po
   zapisaniu **sam sprawdza plik wynikowy** (formuły, błędy) zanim Wam go
   pokaże. Otwórzcie `_v1.xlsx` w Excelu i sprawdźcie 3 poprawki.
6. **Dashboard.** `/build-dashboard` (`/data:build-dashboard`) z
   doprecyzowaniem: *„na pliku `zestawienie_roczne_2026.xlsx`, arkusz
   `Wykonanie`: KPI plan roczny vs wykonanie narastająco i % planu,
   wykres wykonania miesięcznego po działach, tabela z filtrem po dziale."*
   Poczekajcie kilka minut – po prawej zobaczycie etapy: czytanie danych,
   budowa interaktywnej strony HTML, weryfikacja renderowania. Otwórzcie
   gotowy plik `.html` w przeglądarce i **przetestujcie filtry**: wybierzcie
   jeden dział, potem wszystkie; sprawdźcie, czy suma „Razem" zgadza się z
   arkuszem (policzcie jedną kolumnę ręcznie w Excelu).
7. (Opcjonalnie) `/create-viz` – zamiast całego dashboardu jeden wykres,
   np. *„% wykonania planu po działach, wykres słupkowy poziomy, do
   wklejenia w prezentację"*. Wynik to obraz PNG – gotowy materiał do
   Dnia 3.

## Na co zwrócić uwagę

- **Cztery komendy = cztery kroki pracy analityka.** Nie tłumaczycie
  agentowi „wczytaj arkusz, policz braki, zrób wykres" – to wszystko jest
  już opisane w komendzie. Wy podajecie tylko plik i to, co Was interesuje.
- **Agent sprawdza sam siebie.** Po każdym etapie (czyszczenie, dashboard)
  wtyczka uruchamia kontrolę wyniku, zanim go pokaże. To podnosi jakość –
  ale **nie zastępuje Waszej kontroli**: klucz odpowiedzi z kroku 3 i
  ręczne przeliczenie jednej kolumny w kroku 6 to minimum.
- **Nigdy nie nadpisujemy oryginału.** `_v1` w nazwie to nawyk z zadań
  Claude Code + Excel (kopia przed zmianą). Jeśli agent nadpisze plik –
  to błąd polecenia, nie „inteligencja" narzędzia.
- **To zjada tokeny.** Cały przepływ (cztery komendy, subagenci, kontrole)
  potrafi zużyć sporą część dziennego limitu w planie Team. Uruchamiajcie
  go świadomie, na plikach, które tego warte – nie „żeby zobaczyć".
  Podgląd zużycia: pasek kontekstu po prawej (zadanie 3).
- **Dashboard HTML ≠ Power BI.** To jednorazowa strona z danymi
  „wypieczonymi" w środku – świetna do szybkiego przeglądu i do
  prezentacji, ale nie odświeży się sama po zmianie pliku. Trzeba
  uruchomić komendę ponownie. Odświeżalne raporty to temat Bloku E.
- **Zasada danych bez wyjątków.** Wtyczka czyta cały plik do okna
  kontekstu i wysyła go do dostawcy modelu. Na realnych zestawieniach
  Urzędu – wyłącznie po pisemnej zgodzie Zamawiającego i ustaleniach z IT.

## Notatki własne

- Które z trzech błędów w `PRZYKLAD.xlsx` agent wykrył sam, a które
  przeoczył?
- Czy suma w dashboardzie zgadzała się z arkuszem? Jeśli nie – gdzie była
  różnica?
- Który krok (poznaj / sprawdź / wyczyść / dashboard) oszczędziłby Wam
  najwięcej czasu w realnym Procesie 2 lub 3?
