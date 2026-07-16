# Kanały DMR i przemienniki

RUT potrafi importować kanały i przemienniki, budować pliki CSV zgodne z OpenGD77 CPS oraz dopisywać kanały do aktualnego codepluga radia OpenGD77.

## DMR ID

Pole `DMR ID` w głównym oknie ma znaczenie przy generowaniu kanałów OpenGD77. Jeśli wpiszesz tam numer, RUT będzie go wpisywał w odpowiednie pola importowanych kanałów DMR.

DMR ID może zawierać tylko cyfry. Jeżeli wpiszesz inne znaki, RUT wyczyści pole.

## Import z internetu

Przycisk `Przemienniki z internetu` pobiera listy przemienników z obsługiwanych źródeł. Dla SP-DMR używany jest adres:

`http://www.sp-dmr.pl/przemienniki-sp-dmr/`

RUT normalizuje dane i zapisuje wynik w folderze:

`downloads\channel_lists`

## Import z pliku

Przycisk `Kanały z pliku` pozwala wybrać lokalny plik z kanałami. RUT próbuje znormalizować dane do formatu OpenGD77.

## Kanały + wgraj

Przycisk `Kanały + wgraj` wykonuje pełny przepływ:

1. Importuje kanały z wybranego źródła.
2. Buduje pakiet CSV zgodny z OpenGD77 CPS.
3. Robi bezpieczny odczyt obecnego codepluga z radia.
4. Dopisuje nowe kanały do istniejących.
5. Usuwa faktyczne duplikaty, jeśli wystąpią.
6. Buduje nowy plik `.g77`.
7. Wgrywa go do radia i robi odczyt weryfikacyjny.

Radio musi być w trybie normalnym, nie w DFU.

## Sprawdź paczkę CSV

Przycisk `Sprawdź paczkę CSV` waliduje folder eksportu/importu OpenGD77 CPS przed próbą wgrania go w CPS. RUT sprawdza między innymi:

- czy istnieją `Channels.csv` i `Zones.csv`,
- czy pliki mają spójny separator `;` albo `,`,
- czy każdy wiersz ma tyle pól co nagłówek,
- czy kanały mają nazwy,
- czy strefy nie wskazują pustych kanałów.

To pomaga przy błędach OpenGD77 CPS typu `line 2 is not valid in channels`.

Ten sam test można uruchomić z konsoli:

```powershell
powershell.exe -ExecutionPolicy Bypass -File .\RUT.ps1 -ValidateCpsDir "C:\folder_csv"
```

Paczki CSV tworzone przez RUT zawierają teraz także pomocnicze pliki `Contacts.csv`, `TG_Lists.csv`, `Channels.csv` i `Zones.csv`, żeby OpenGD77 CPS dostał komplet podstawowych danych.

## Czy RUT usuwa moje kanały

Założenie RUT jest takie, żeby dopisywać kanały, a nie podmieniać cały codeplug. Program usuwa stare wpisy tylko wtedy, gdy wykryje rzeczywiste powtórzenie potrzebne do oszczędzenia miejsca i uniknięcia duplikatu.

## Foldery wynikowe

Najważniejsze foldery:

- `downloads\channel_lists` - importy i wygenerowane CSV.
- `downloads\channel_lists\OpenGD77_DIRECT_BASE_*` - odczyt bazowego codepluga przed zapisem.
- `downloads\channel_lists\OpenGD77_CPS_AUTO_*` - paczki CSV dla OpenGD77 CPS.

## Gdy zapis kanałów nie działa

Najczęstsze przyczyny:

- radio jest w DFU zamiast w trybie normalnym,
- port COM jest zajęty przez CPS,
- Windows nie widzi portu COM radia,
- brakuje `DefaultOpenGD77.g77` z instalacji OpenGD77 CPS,
- radio nie pracuje na OpenGD77.

Rozwiązania są opisane w [08-rozwiazywanie-problemow.md](08-rozwiazywanie-problemow.md).
