# Szybki start

Ten rozdział opisuje najkrótszą bezpieczną drogę od pobrania RUT do pierwszego użycia.

## Wymagania

- Windows 10 albo Windows 11.
- Konto użytkownika z możliwością uruchamiania PowerShella.
- Kabel USB do radia.
- Dla funkcji OpenGD77 CPS: zainstalowany OpenGD77 CPS, jeśli chcesz używać operacji wymagających pliku `DefaultOpenGD77.g77`.
- Dla funkcji DMR + flash: od wersji `2026.05.18.9` RUT ma wbudowany loader EXE i nie wymaga instalowania Pythona ani `pyusb`. Python jest tylko awaryjnym fallbackiem deweloperskim.

## Instalacja z jednego pliku EXE

1. Pobierz `RUT.exe` z najnowszego release:
   https://github.com/kazek5p-git/RUT/releases/latest/download/RUT.exe
2. Uruchom `RUT.exe`.
3. Program sam rozpakowuje swoją paczkę do `%LOCALAPPDATA%\RUT\onefile\<wersja>` i startuje właściwe GUI.
4. To jest najwygodniejszy wariant dla osoby, która nie chce rozpakowywać ZIP-a ręcznie.

## Instalacja z ZIP

1. Pobierz `RUT.zip` z najnowszego release:
   https://github.com/kazek5p-git/RUT/releases/latest/download/RUT.zip
2. Rozpakuj ZIP do własnego folderu, na przykład `<folder RUT>`.
3. Uruchom `start_RUT.vbs`.
4. Je?li program zamyka si? od razu, uruchom `start_RUT_debug.cmd` i sprawd? pliki `.txt` w folderze `logs`.
4. Jeśli Windows albo program antywirusowy zapyta o zaufanie do pliku, potwierdź tylko wtedy, gdy ZIP pochodzi z powyższego release GitHub.

## Pierwsze uruchomienie

Po starcie RUT pokazuje główne okno z natywnymi kontrolkami Windows i zakładkami. Kursor czytnika ekranu trafia na pasek zakładek. Najważniejsze pola:

- `Model radia` - wybór profilu radia.
- `DMR ID` - numer DMR używany przy generowaniu kanałów DMR.
- `Timeout DFU` - ile sekund RUT czeka na radio w trybie DFU.
- `Log` - szczegóły działania i błędów.

## Pierwsza czynność dla RT3S

Jeśli masz Retevis RT3S i radio ma jeszcze fabryczny firmware Retevis/TYT, najpierw zrób backup w oficjalnym CPS producenta. RUT ma przycisk `Backup radia`, ale ten przycisk odczytuje codeplug OpenGD77 wtedy, gdy radio już pracuje na OpenGD77 w normalnym trybie COM. Fabryczną kalibrację RT3S trzeba zachować CPS-em producenta.

## Pierwsza czynność dla radia już z OpenGD77

1. Włącz radio normalnie.
2. Podłącz USB.
3. W RUT wybierz profil radia.
4. Kliknij `Backup radia`.
5. Zachowaj utworzony folder z `backups\radio`.

## Aktualizacja samego RUT

Program sprawdza manifest aktualizacji przy starcie, jeśli `auto_check_on_start` w `program_update_config.json` jest ustawione na `true`. Możesz też kliknąć `Aktualizuj program` ręcznie.
