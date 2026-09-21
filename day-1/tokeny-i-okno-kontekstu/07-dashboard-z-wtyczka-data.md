# Zadanie 7: Od surowego Excela do dashboardu – wtyczka Data w Cowork

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
**demo prowadzącego na koniec Bloku D** albo praca własna po szkoleniu).

**Cel:** przejść jedną wtyczką cały przepływ analityka: poznaj dane →
sprawdź jakość → wyczyść → zbuduj dashboard. Komendy `/`, skille
i subagenci z zadania 6 w praktyce.
**Poziom:** średni (praktyka w Cowork)
**Czas:** ok. 25 minut (w tym kilka minut czekania na dashboard)
**Wymaga:** Cowork (desktop), plan Team, wtyczka **Data** (krok 1).

## Co powstanie

1. raport z profilu i walidacji `zestawienie_miesieczne_PRZYKLAD.xlsx`,
2. wyczyszczony plik `..._PRZYKLAD_v1.xlsx` (oryginał nietknięty),
3. interaktywny dashboard `.html` z `zestawienie_roczne_2026.xlsx`.

## Przygotowanie

Folder `Pulpit\analiza-danych\` z **kopiami** dwóch fikcyjnych plików.
Zamknijcie je w Excelu przed startem.

| Plik | Skopiuj z | Klucz |
|---|---|---|
| `zestawienie_miesieczne_PRZYKLAD.xlsx` | `../materialy/` | **3 celowe błędy:** pusty wiersz (5), trzy formaty miesiąca (`wrzesień 2026` / `2026-09` / `09.2026`, wiersze 4 i 8), scalona komórka D9:D10 |
| `zestawienie_roczne_2026.xlsx` | `../claude-code-cli/materialy/` | arkusz `Wykonanie`: 8 działów (600–926), plan roczny, miesiące I–VIII |

## Kroki

### Krok 1: Zainstaluj wtyczkę Data (raz, 3 min)

Cowork → **Customize → Browse plugins → Data → Install**. Potem
**Customize → Personal plugins → Data** – zajrzyjcie do trzech zakładek:

- **Skills** – otwórzcie `data-visualization` (`SKILL.md`): to wiedza
  analityka spisana po ludzku;
- **Connectors** – **nic nie podpinamy**;
- **Commands** – kliknijcie `/create-viz` i przeczytajcie opis przepływu.
  To „komenda = opisany przepływ" z zadania 6.

### Krok 2: Folder roboczy (1 min)

**New task** → *Choose a different folder* → `Pulpit\analiza-danych` →
**Allow**. Model: najmocniejszy dostępny (Opus).

### Krok 3: Poznaj dane (5 min)

Wpiszcie `/` i wybierzcie z listy `/explore-data` (nazwy komend mogą się
różnić między wersjami – wybierajcie z listy). Na pytanie o źródło:

```
Arkusz Excel: plik zestawienie_miesieczne_PRZYKLAD.xlsx
```

Po prawej lista podzadań (wczytaj → profil kolumn → jakość →
rekomendacje).

**Sprawdź z kluczem:**

- [ ] pusty wiersz 5
- [ ] trzy formaty miesiąca
- [ ] scalona komórka (agent może zgłosić jako „brak miesiąca
      w ostatnim wierszu")

Czego nie wykrył – zapiszcie.

### Krok 4: Sprawdź jakość (3 min)

`/validate` na tym samym pliku. **Sprawdź:** czy raport walidacji dodał
coś, czego nie było w kroku 3?

### Krok 5: Wyczyść do nowego pliku (5 min)

Zwykłym poleceniem, bez komendy:

```
Wyczyść dane: usuń pusty wiersz, ujednolić kolumnę Miesiąc do formatu
2026-09, rozdziel scaloną komórkę i uzupełnij miesiąc w ostatnim wierszu.
Zapisz wynik jako zestawienie_miesieczne_PRZYKLAD_v1.xlsx.
Nie nadpisuj oryginału.
```

Agent sięga po skill Excel i po zapisaniu **sam sprawdza plik wynikowy**.

**Sprawdź** w Excelu (`_v1.xlsx`):

- [ ] brak pustego wiersza
- [ ] kolumna Miesiąc: wszędzie `2026-09`
- [ ] ostatni wiersz ma miesiąc, brak scalonych komórek
- [ ] oryginał **bez zmian**

### Krok 6: Dashboard (8 min)

`/build-dashboard` z doprecyzowaniem:

```
Na pliku zestawienie_roczne_2026.xlsx, arkusz Wykonanie: KPI plan roczny
vs wykonanie narastająco i % planu, wykres wykonania miesięcznego
po działach, tabela z filtrem po dziale.
```

Poczekajcie kilka minut (czytanie → budowa HTML → weryfikacja
renderowania). Otwórzcie `.html` w przeglądarce.

**Sprawdź:**

- [ ] filtr działa: jeden dział → wszystkie
- [ ] KPI „wykonanie narastająco" = suma kolumn I–VIII w arkuszu
      (policzcie jedną kolumnę ręcznie w Excelu)

### Krok 7 (opcjonalnie): jeden wykres

`/create-viz`:

```
% wykonania planu po działach, wykres słupkowy poziomy, do wklejenia
w prezentację.
```

Wynik `.png` – materiał na Dzień 3.

## Na co zwrócić uwagę

- **Cztery komendy = cztery kroki analityka.** Wy podajecie plik i to,
  co Was interesuje.
- **Agent sprawdza sam siebie – ale nie zastępuje Was.** Klucz z kroku 3
  i ręczne przeliczenie w kroku 6 to minimum.
- **Nigdy nie nadpisujemy oryginału.** `_v1` to nawyk.
- **To zjada tokeny.** Cały przepływ potrafi zużyć sporą część limitu.
  Uruchamiajcie świadomie, nie „żeby zobaczyć".
- **Dashboard HTML ≠ Power BI.** Nie odświeży się sam – trzeba uruchomić
  komendę ponownie. Odświeżalne raporty to Blok E.
- **Wtyczka czyta cały plik do okna i wysyła do dostawcy.** Na realnych
  zestawieniach – tylko za pisemną zgodą i po ustaleniach z IT.

## Notatki własne

- Które z trzech błędów agent wykrył sam, a które przeoczył?
- Czy suma w dashboardzie zgadzała się z arkuszem?
- Który krok oszczędziłby Wam najwięcej czasu w realnym Procesie 2 lub 3?
