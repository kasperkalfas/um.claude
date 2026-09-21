# Zadanie 6: Wtyczki (plugins) – skille, konektory, komendy i subagenci w jednym pakiecie

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu, Dzień 1,
wstęp do **Bloku D: Claude Code – pierwszy kontakt**).

**Cel:** otworzyć katalog wtyczek w Cowork, rozebrać jedną wtyczkę
finansową na cztery elementy i zapisać pomysł na wtyczkę Wydziału.
**Poziom:** podstawowy
**Czas:** ok. 8 minut
**Wymaga:** Claude Cowork (aplikacja desktopowa). Niczego nie instalujemy.

## W trzech zdaniach

**Wtyczka (plugin) = skille + konektory + komendy `/` + subagenci**,
spakowane pod jedną konkretną robotę. Zamiast w każdej rozmowie
tłumaczyć, kim jesteście i jak wygląda Wasz proces, wpisujecie jedną
komendę, np. `/zamknij-miesiac`. Nic nowego pod spodem – to pakiet
rzeczy, które już znacie.

| Element | Co to jest | Gdzie już to widzieliście |
|---|---|---|
| **Skill** | wiedza i sposób pracy („jak pisać notatkę o odchyleniach") | [zad. 7–8 z Bloku C](../claude-zadania/07-skill-notatka-budzetowa.md) |
| **Konektor (MCP)** | dostęp do danych: dysk, poczta, kalendarz | [zadanie 5](05-mcp-czyli-jak-claude-siega-po-dane.md) |
| **Komenda `/`** | jedna komenda = cały opisany przepływ pracy | [`/zamknij-miesiac`](../claude-code-cli/10-claude-md-i-wlasna-komenda.md) |
| **Subagent** | „pracownik" z **własnym oknem kontekstu**; agent główny dostaje tylko wynik | nowość |

Subagenci to powód, dla którego wtyczki radzą sobie z zadaniami, które
w jednym czacie by „nie weszły": jeden czyta pliki, drugi liczy, trzeci
sprawdza – a główna rozmowa się nie zapycha.

## Kroki

1. **Otwórzcie katalog.** Cowork → pasek po lewej → **Customize** →
   **Browse plugins**. Przejrzyjcie kategorie (produktywność, sprzedaż,
   prawo, dane i finanse, HR…). **Nie klikajcie Install.**
2. **Wybierzcie jedną wtyczkę finansową** (np. z analizą odchyleń –
   to Wasz Proces 2) i otwórzcie jej opis.
3. **Rozbierzcie ją na cztery elementy.** Wpiszcie w „Notatkach":

   | Element | Co ma ta wtyczka |
   |---|---|
   | Skille | |
   | Konektory (do czego chce się podłączyć) | |
   | Komendy `/` | |
   | Subagenci (tak / nie) | |

   **Sprawdź:** które konektory wymagałyby pisemnej zgody Urzędu/PNT,
   zanim ktokolwiek je podepnie?

4. **Rozmowa (3 min):** wtyczka „Proces 1 + 2" dla Waszego wydziału – co
   byłoby skillem, co konektorem, jak nazwalibyście komendę, co robiliby
   subagenci? (W zadaniu 10 zbudujecie ją naprawdę.)

## Na co zwrócić uwagę

- **Komenda `/` to streszczenie tego, co robicie jako człowiek** – raz
  opisane, uruchamiane jednym słowem.
- **Każda wtyczka zajmuje okno kontekstu.** Wtyczka „HR" w rozmowie
  o budżecie to czysty koszt. Instalujcie to, czego używacie.
- **Subagenci ≠ bez nadzoru.** W Claude Code każda zmiana pliku nadal
  wymaga zgody. Za zestawienie odpowiadacie Wy.
- **Konektory we wtyczce = zasady z zadania 5.** Na szkoleniu oglądamy
  katalog, nie podpinamy systemów.

## Notatki własne

- Jaką wtyczkę z katalogu sprawdzicie po szkoleniu (na danych
  fikcyjnych)? Co ma robić?
- Jak nazywałaby się główna komenda `/` wtyczki Waszego wydziału?
