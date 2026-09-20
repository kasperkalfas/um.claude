# Zadanie 2: Prezentacja z jednego zdania – plan, zgoda, slajdy „rodzą się" na Waszych oczach

Ćwiczenie do szkolenia „Wykorzystanie systemu AI Claude we współpracy z
Excel, PowerPoint oraz automatyzacja zadań" (Urząd Miejski w Opolu,
**Dzień 2**, ścieżka „Claude w PowerPoincie"; kontynuacja
[zadania 1](01-claude-w-powerpoincie-instalacja.md)).

**Cel:** zbudować 5–6 slajdów jednym poleceniem wprost w PowerPoincie:
odpowiedzieć na pytania Claude o odbiorcę, długość i styl, zatwierdzić
plan, obejrzeć, jak slajdy powstają jeden po drugim, i jak Claude sam
sprawdza swoją pracę – a po drodze świadomie wybrać **tryb zgód** na
zmiany w pliku.
**Poziom:** podstawowy
**Czas:** ok. 15 minut (generowanie 3–5 min)
**Wymaga:** dodatek Claude w PowerPoincie (zadanie 1), **nowa, pusta
prezentacja**, model Opus.

## Problem, który to rozwiązuje

„Zrób mi 5 slajdów o X na jutro" – to zadanie, które w Wydziale zabiera
popołudnie: szkielet, tytuły, treść, ikony, wyrównanie. W Dniu 1 Cowork
robił to „obok" (gotowy plik z folderu). Tu Claude robi to **w otwartym
pliku**: pyta, planuje, wstawia slajd po slajdzie, a Wy patrzycie i w
każdej chwili możecie przerwać. Różnica w praktyce: wynik jest od razu w
Waszym szablonie i edytowalny jak każdy slajd.

## Materiały

- Nowa, pusta prezentacja (Plik → Nowy; jeśli macie pusty szablon
  Urzędu – może być, to wygląd, nie dane).
- Temat na pierwszy raz – **ogólny, bez danych Urzędu**, żeby zobaczyć
  mechanikę. Proponowany: *„Budżet obywatelski w mieście – jak działa i
  co daje mieszkańcom"*. Zamienniki: *„Jak bezpiecznie korzystać z AI w
  urzędzie – 5 zasad dla pracowników"*, *„Klasyfikacja budżetowa dla
  nie-księgowych"*.
- Do części 2: pięć punktów „dla naczelnika" z zadania 2 z Excela
  (`../claude-w-excelu/02-pierwsze-wnioski-z-danych.md`) – skopiowane
  jako tekst.

## Kroki

1. **Tryb zgód – zanim cokolwiek wpiszecie.** Na dole panelu jest
   przełącznik: **pytaj przed każdą zmianą** (*ask before edits*) albo
   **akceptuj wszystkie zmiany** (*accept all edits*). Na pustej
   prezentacji nie ma czego stracić – możecie wybrać „akceptuj". Przy
   **istniejącej** prezentacji: zawsze „pytaj" + kopia pliku. To ta
   sama decyzja co w Claude Code w Dniu 1 (zadanie 10: „zgoda przed
   zmianą") – tylko w innym oknie.
2. **Jedno zdanie.** W panelu (albo głosem: `Win + H` włącza dyktowanie
   Windows): *„Stwórz prezentację o budżecie obywatelskim w mieście –
   jak działa i co daje mieszkańcom."*
3. **Pytania Claude.** Zanim zacznie, zapyta o **odbiorcę** (np.
   mieszkańcy / radni / pracownicy urzędu), **długość** (krótka 5–6 /
   średnia / szczegółowa) i **styl** (jasny i nowoczesny / ciemny i
   mocny). Wybierzcie: **radni**, **krótka**, styl dowolny. Zwróćcie
   uwagę, że pierwsze pytanie brzmi „dla kogo" – to samo pytanie, od
   którego w Dniu 3 zacznie DataPOV.
4. **Plan do zatwierdzenia.** Claude wypisze 5–6 tytułów slajdów (np.
   tytułowy → co to jest → jak przebiega → co daje mieszkańcom →
   wyzwania → podsumowanie) i zapyta o zgodę. **Przeczytajcie plan** –
   to najtańszy moment na zmianę: *„Zamień slajd 5 na 'Rola radnych w
   procesie'"* kosztuje jedno zdanie; ta sama zmiana po wygenerowaniu –
   kilka minut i sporo tokenów. Potem: *„Zatwierdzam."*
5. **Patrzcie, nie klikajcie.** Slajdy pojawiają się jeden po drugim,
   z treścią i ikonami. W trakcie Claude może poprosić o zgodę na
   konkretną operację (np. usunięcie pustego slajdu) – z opcjami
   *pozwól raz / zawsze pozwalaj / pozwól bez pytania*. Na pustym pliku
   – *pozwól raz*. Nie dotykajcie prezentacji, dopóki panel nie napisze,
   że skończył – równoległe edycje kończą się nadpisaniem Waszych
   zmian.
6. **Samokontrola.** Przed „gotowe" Claude **sprawdza własne slajdy**:
   nakładanie się tekstu, wyrównanie tytułów, brakujące ikony – i część
   poprawia sam (zobaczycie komunikaty w rodzaju „poprawiam położenie
   ikon na slajdzie 4"). To ta sama pętla, którą widzieliście w Cowork
   przy dashboardzie i `.pptx` w Dniu 1.
7. **Odbiór.** Przejrzyjcie slajdy w widoku sortowania (*Widok →
   Sortowanie slajdów*). Zapiszcie w „Notatkach": co jest dobre, co
   wymaga ręki (typowo: niewyśrodkowany tytuł, brak ikony na jednym
   slajdzie, za dużo tekstu na jednym). Kliknijcie w dowolny element –
   to zwykłe pole tekstowe PowerPointa. Poprawcie **jedną rzecz ręcznie**
   i **jedną przez Claude** (*„Na slajdzie 3 skróć tekst do 3 punktów po
   maks. 8 słów."*). Które było szybsze?
8. **Część 2 – z Waszych danych (fikcyjnych).** Nowa prezentacja.
   Wklejcie pięć punktów z zadania 2 z Excela i napiszcie: *„Zrób z tych
   pięciu punktów prezentację dla naczelnika wydziału kadr: 6 slajdów,
   każdy z jedną liczbą w tytule, styl jasny."* Porównajcie z częścią 1:
   tu Claude nie wymyśla treści – układa **Waszą**. Sprawdźcie, czy
   wszystkie liczby na slajdach są identyczne z tym, co wkleiliście.

## Na co zwrócić uwagę

- **Tryb zgód to decyzja, nie wygoda.** „Akceptuj wszystko" na pustym
  pliku – w porządku. Na prezentacji dla Rady po trzech dniach pracy –
  nigdy bez kopii. Claude edytuje **Wasz otwarty plik**, nie jego kopię.
- **Plan przed generowaniem to najważniejszy moment.** Zmiana układu
  po zatwierdzeniu planu to zmiana jednego zdania; po wygenerowaniu –
  przebudowa slajdów. Czytajcie plan tak, jak czytalibyście spis treści
  pisma przed jego napisaniem.
- **Treść „z głowy" Claude wymaga sprawdzenia.** Część 1 (budżet
  obywatelski) jest napisana z wiedzy ogólnej modelu: poprawna co do
  zasady, ale bez znajomości uchwały Rady Miasta Opola. Fakty, terminy,
  kwoty, podstawy prawne – **zawsze z Waszych źródeł**. Część 2 pokazuje
  właściwy kierunek: Wy dajecie treść, Claude daje formę.
- **Slajdy są edytowalne, nie „wypalone".** Każde pole tekstowe,
  ikona i kształt to zwykły obiekt PowerPointa. Drobne poprawki
  szybciej ręcznie; zmiany „na wszystkich slajdach" – szybciej przez
  Claude.
- **Krótka prezentacja to nie jedyna opcja.** Po ćwiczeniu spróbujcie
  „średniej" (ok. 12 slajdów) na tym samym temacie – zobaczycie, jak
  Claude rozbudowuje strukturę, i ile więcej tokenów to kosztuje.
- **Dane bez zmian.** Część 1 – temat ogólny, część 2 – dane fikcyjne.
  Prezentacja o realnym budżecie Opola z realnymi kwotami to dane
  Zamawiającego: tylko za pisemną zgodą (Dzień 1, Blok B).

## Notatki własne

- Jaki plan zaproponował Claude i co w nim zmieniliście przed
  zatwierdzeniem?
- Co po wygenerowaniu wymagało ręki: ile rzeczy poprawiliście ręcznie,
  ile przez Claude?
- Czy w części 2 wszystkie liczby na slajdach zgadzały się z wklejonym
  tekstem?
