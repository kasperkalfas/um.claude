# Zadanie 3: Wtyczka Claude in Chrome – instalacja i uprawnienia

> **Materiał wprowadzający**, ciąg dalszy [zadania 1](01-czym-jest-cowork.md).

**Cel:** zainstalować wtyczkę **Claude in Chrome**, świadomie ustawić
uprawnienia i przetestować ją na publicznej stronie.
**Poziom:** podstawowy
**Czas:** ok. 15 minut

## Co to jest – i dlaczego wymaga ostrożności

Wtyczka działa **w Twojej prawdziwej przeglądarce Chrome** – na Twoich
kartach, z Twoimi zalogowanymi kontami. Claude może klikać, wypełniać
formularze i czytać strony w Twoim imieniu.

Wbudowana przeglądarka Cowork (zadanie 1) jest osobna i izolowana –
niższe ryzyko. Wtyczka Chrome ma dostęp do wszystkiego, na czym jesteś
zalogowany/a – **wyższe ryzyko**. Wymaga planu płatnego; Team Urzędu jest
objęty.

**Trzy zasady:**

1. Testuj w **osobnym profilu Chrome**, w którym nie jesteś zalogowany/a
   do niczego służbowego.
2. Zaczynaj od trybu **Manual** – Claude pyta przed każdą akcją.
3. Nie ustawiaj „Default for all sites" na automatyczną zgodę na
   komputerze służbowym. Działanie na systemach Urzędu = pisemna zgoda
   Zamawiającego, jak przy każdej integracji.

## Kroki

1. **Sprawdź plan.** Ustawienia → Plan (Pro/Max/Team/Enterprise).
2. **Utwórz osobny profil Chrome** do testów (ikona profilu w prawym
   górnym rogu Chrome → Dodaj) – bez logowania do kont służbowych.
3. **Zainstaluj.** W tym profilu wejdź na [claude.ai/chrome](https://claude.ai/chrome)
   → **Add to Chrome** → zaloguj się kontem Claude → zaakceptuj
   uprawnienia. Przypnij ikonę (puzzle → pineska przy „Claude").
4. **Ustaw uprawnienia.** Ustawienia wtyczki → **Site permissions** →
   sprawdź **„Default for all sites"**. Jeśli jest na najszerszej opcji –
   zawęź (pytaj / osobna zgoda dla każdej strony).
5. **Ustaw tryb Manual** w rozwijanym menu przy oknie czatu wtyczki.
6. **Przetestuj na neutralnej stronie.** Otwórz polską Wikipedię i wpisz
   we wtyczce:

   ```
   Przeczytaj otwartą stronę i streść ją w 3 zdaniach.
   ```

7. **Obserwuj pytania.** Przed każdą akcją Claude pyta o zgodę – kliknij
   „Zezwól" albo „Odrzuć" świadomie.

**Sprawdź:**

- [ ] przełącznik **„Enable Claude in Chrome"** jest włączony
- [ ] „Default for all sites" **nie** jest na automatycznej zgodzie
- [ ] tryb = Manual
- [ ] w teście Claude zapytał o zgodę, zanim cokolwiek zrobił

## Ściągawka: tryby i twarde granice

| Tryb | Co się dzieje |
|---|---|
| **Manual** (start) | pyta przed każdą akcją |
| **Auto** | działa sam, blokuje to, co uzna za ryzykowne, pyta tylko wtedy |
| **Skip** | o nic nie pyta – tylko gdy w 100 % ufasz zadaniu i stronie |

Niezależnie od trybu Claude **zawsze pyta** przed pobraniem pliku,
wpisaniem wrażliwych danych i autoryzacją (OAuth). **Nigdy nie zrobi:**
zakupów i płatności, zakładania kont, wpisywania danych karty/dokumentów,
trwałego usuwania, transakcji giełdowych.

## Na co zwrócić uwagę

- **Site permissions** są wspólne dla wtyczki i wbudowanej przeglądarki
  Cowork – zmiana w jednym miejscu działa na oba.
- Jeśli nie widzisz wtyczki na swoim koncie – jest wdrażana stopniowo,
  to nie błąd.

## Notatki własne

- Jak masz ustawione „Default for all sites" – świadomie czy domyślnie?
- Jakie publiczne, nieistotne zadanie przetestujesz jako pierwsze?
