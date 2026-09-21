# Zadanie 7: Własny skill – notatka o odchyleniach budżetowych

> **Materiał dodatkowy – poza Blokiem C.** Budowa własnego skilla to temat
> na dłuższe, osobne zajęcia, nie na 60-minutowy blok „Claude Czat w
> przeglądarce" (tam ćwiczymy formułę P.K.Z.O., interfejs i bezpieczną
> analizę arkusza – zadania 1–3). Do samodzielnej pracy po szkoleniu.

**Cel:** zbudować od zera własny skill w Claude (przez przeglądarkę, bez
programowania), który na podstawie zestawienia plan/wykonanie przygotowuje
notatkę o odchyleniach budżetowych – zawsze w tym samym, stałym formacie –
zamiast za każdym razem tłumaczyć Claude, jak ma wyglądać taka notatka.
**Poziom:** średniozaawansowany

## Po co własny skill?

**Skill** to spakowany zestaw instrukcji, który uczy Claude wykonywania
konkretnego zadania w powtarzalny sposób. To dokładnie sytuacja z Procesu 2
i 3: co miesiąc powstaje to samo zestawienie i ta sama potrzeba – krótkie
wyjaśnienie, które wydziały odbiegają od planu i dlaczego. Zamiast za
każdym razem pisać ten sam długi prompt, zapisujemy go raz jako skill.

Skill będzie znał dwa stałe formaty notatki:

| Format | Dla kogo | Charakter |
|---|---|---|
| **Notatka wewnętrzna** | przełożona / kierownik wydziału | krótka, tylko istotne odchylenia, same liczby i jedno zdanie kontekstu |
| **Notatka dla interesariuszy** | bank / rada miasta | pełne zdania, kontekst przyczyny, konsekwencje, rekomendacja – nawiązuje do DataPOV, który poznacie w Dniu 3 |

## Materiały

- Konto na [claude.ai](https://claude.ai) z włączonym wykonywaniem kodu
  i tworzeniem plików (**Ustawienia → Capabilities** – *code execution
  and file creation*). **Skills działają także na darmowym planie.**
- Plik `../materialy/zestawienie_miesieczne_PODSUMOWANIE.xlsx` (ten sam,
  co w [zadaniu 3](03-analiza-dokumentu-excel.md), Część 2) – 10 wydziałów,
  7 przekracza plan.
- Notatnik (lub dowolny edytor tekstu) i możliwość spakowania folderu do
  ZIP – na Windows: prawy przycisk myszy → **Kompresuj do pliku ZIP**.

## Kroki

### Część 1: Punkt odniesienia – bez skilla

1. Upewnij się, że żaden skill budżetowy nie jest włączony.
2. Wgraj plik `zestawienie_miesieczne_PODSUMOWANIE.xlsx` i wyślij:

   ```
   Napisz notatkę o odchyleniach budżetowych na podstawie tego zestawienia.
   ```

3. Zachowaj wynik – to Twoje „przed". Zwykle wychodzi poprawna, ale za
   każdym razem inaczej ułożona notatka – inny próg, inna kolejność, inny
   ton.

### Część 2: Zbudowanie skilla

Skill to folder z jednym obowiązkowym plikiem: `SKILL.md`. Na górze pliku
znajduje się krótki opis (sekcja między `---`), po którym Claude
rozpoznaje, kiedy sięgnąć po skill. Reszta to instrukcja pisana zwykłym
językiem.

4. Utwórz na pulpicie folder o nazwie `notatka-odchylenia-budzetowe`.
5. W folderze utwórz plik tekstowy `SKILL.md` i wklej poniższą treść
   (możesz ją potem dowolnie zmieniać – to Twój skill):

   ```markdown
   ---
   name: notatka-odchylenia-budzetowe
   description: Przygotowuje notatkę o odchyleniach budżetowych (plan vs
     wykonanie) na podstawie zestawienia wydziałów, w jednym z dwóch
     stałych formatów – krótkim wewnętrznym lub rozszerzonym dla banku/
     rady miasta. Używaj, gdy użytkownik dostarcza zestawienie planu i
     wykonania budżetu i prosi o notatkę, podsumowanie odchyleń lub
     wyjaśnienie przekroczeń.
   ---

   # Notatka o odchyleniach budżetowych

   ## Kontekst

   Dane wejściowe to zestawienie wydziałów z kolumnami: dział, kwota
   planowana, kwota wykonana, okres. Zadanie: policzyć odchylenie
   (wykonanie minus plan) i przygotować notatkę – domyślnie w formacie
   wewnętrznym, chyba że użytkownik wskaże inaczej (np. „dla banku",
   „dla rady miasta").

   ## Próg istotności

   Odchylenie jest **istotne** i trafia do notatki, gdy przekracza
   **5% planu LUB 20 000 zł** (co jest większe w danym przypadku).
   Mniejsze odchylenia pomiń – nie zaśmiecaj notatki szumem.

   ## Zasady wspólne

   - Kwoty zawsze w PLN, z separatorem tysięcy (np. „112 000 zł"), nigdy
     w zapisie naukowym ani z nadmiarową liczbą miejsc po przecinku.
   - Odchylenia sortuj malejąco według wartości bezwzględnej (największe
     najpierw) – tak łatwiej dostrzec priorytety.
   - Nigdy nie podawaj nazwisk konkretnych pracowników ani kierowników
     wydziałów – notatka dotyczy liczb, nie osób.
   - Jeśli nie znasz faktycznej przyczyny odchylenia (a zwykle nie znasz –
     dane wejściowe jej nie zawierają), napisz to wprost: „przyczyna do
     potwierdzenia z wydziałem" zamiast zgadywać.

   ## Format A – notatka wewnętrzna (domyślna)

   Dla przełożonej/kierownika wydziału. Struktura:

   1. Jedno zdanie nagłówka: okres i liczba wydziałów z istotnym
      odchyleniem.
   2. Lista punktowana istotnych odchyleń, max 6 pozycji: dział, kwota
      odchylenia, procent, „przyczyna do potwierdzenia" jeśli nieznana.
   3. Bez wstępu ani zakończenia – ma być czytelna w 15 sekund.

   ## Format B – notatka dla interesariuszy (bank / rada miasta)

   Pełne zdania, w duchu DataPOV (punkt widzenia + stawka):

   1. **Kontekst** – jedno-dwa zdania o ogólnej kondycji budżetu w danym
      okresie.
   2. **Kluczowe odchylenia** – dla każdego istotnego odchylenia: dział,
      kwota i procent, jedno zdanie możliwego kontekstu (lub „przyczyna
      do potwierdzenia").
   3. **Konsekwencje / ryzyko** – jedno zdanie o tym, co odchylenia
      oznaczają dla całości budżetu (np. czy się kompensują, czy
      kumulują ryzyko przekroczenia planu rocznego).
   4. **Rekomendacja** – jedno zdanie: co warto zrobić dalej (np.
      „warto potwierdzić przyczynę z trzema największymi wydziałami
      przed wysyłką do rady miasta").

   ## Na końcu każdej notatki

   Dopisz jednym zdaniem, którego formatu użyto (A czy B) i dlaczego –
   żeby użytkownik mógł to łatwo zweryfikować.
   ```

6. Zapisz plik. **Uwaga na rozszerzenie:** plik musi nazywać się
   `SKILL.md`, a nie `SKILL.md.txt` – jeśli zapisujesz z Notatnika,
   w oknie zapisu wybierz „Wszystkie pliki" i wpisz nazwę z `.md`.
7. Spakuj **cały folder** `notatka-odchylenia-budzetowe` do ZIP (prawy
   przycisk → **Kompresuj do pliku ZIP**).
8. W Claude przejdź do **Customize → Skills → „+" → „Upload a skill"**
   i wgraj plik ZIP. Włącz skill przełącznikiem na liście.

### Część 3: Test i porównanie

9. Wyślij **to samo polecenie** co w kroku 2 i porównaj z wersją „przed".
   Notatka powinna mieć max 6 pozycji, sortowanie malejąco, kwoty w PLN i
   nigdzie nie zgadywać przyczyny odchylenia.
10. Poproś wprost o drugi format:

    ```
    Przygotuj tę samą notatkę w wersji dla banku.
    ```

    Sprawdź, czy pojawia się kontekst, konsekwencje i rekomendacja –
    elementy, których nie było w formacie wewnętrznym.
11. Sprawdź granice skilla – poproś o coś spoza jego opisu:

    ```
    Napisz notatkę o remoncie chodnika na ulicy Ozimskiej.
    ```

    Skill nie powinien się uruchomić, bo opis (`description`) mówi tylko
    o odchyleniach budżetowych na podstawie zestawienia plan/wykonanie.

### Wariant dla chętnych: skill-creator

Zamiast pisać `SKILL.md` ręcznie, możesz zainstalować skill
**skill-creator** z oficjalnego repozytorium Anthropic
([github.com/anthropics/skills](https://github.com/anthropics/skills))
i poprosić Claude: *„Zbuduj mi skill do notatek o odchyleniach
budżetowych, w wersji wewnętrznej i dla banku"* – Claude przeprowadzi Cię
przez pytania i sam przygotuje plik do pobrania. Warto jednak raz zrobić
to ręcznie, żeby wiedzieć, co jest w środku.

## Na co zwrócić uwagę

- **Sekcja `description` to najważniejsze zdania całego skilla.** To po
  niej Claude decyduje, czy skill pasuje do zadania. Zbyt ogólny opis
  („pomaga z budżetem") sprawi, że skill będzie się włączał za często;
  zbyt wąski – że wcale.
- **Skill to instrukcja, nie magia.** Wszystko, co umie, sam(a) w niego
  wpisałeś/aś – łącznie z progiem istotności (5%/20 000 zł). Jeśli próg
  nie pasuje do Waszej praktyki, zmień go w `SKILL.md`, spakuj i wgraj
  ponownie – to normalny cykl pracy nad skillem.
- **Claude nie zna prawdziwej przyczyny odchylenia** – zna tylko liczby z
  zestawienia. Skill celowo każe pisać „przyczyna do potwierdzenia",
  zamiast zmyślać wyjaśnienie, które brzmi wiarygodnie, ale nim nie jest
  (to samo zjawisko halucynacji, o którym była mowa w Bloku A).
- Ten sam mechanizm – stały próg istotności, stały format, dwa warianty
  odbiorcy – przyda się przy każdym cyklicznym raporcie, nie tylko przy
  odchyleniach budżetowych: prognozach, sprawozdaniach, zestawieniach dla
  rady miasta.
- Jeśli skill się nie uruchamia, sprawdź kolejno: czy wykonywanie kodu
  jest włączone w **Ustawieniach → Capabilities**, czy skill jest
  włączony przełącznikiem i czy plik nazywa się dokładnie `SKILL.md`.

## Notatki własne

- Czym różniła się notatka „przed" i „po" wgraniu skilla?
- Czy próg istotności (5% lub 20 000 zł) pasuje do Waszej praktyki, czy
  wolałbyś/wolałabyś inny próg?
- Do jakiego innego cyklicznego raportu w swojej pracy zbudowałbyś/
  zbudowałabyś podobny skill?
