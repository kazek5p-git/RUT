# Scenariusze RUT

Ten rozdział jest dla osoby, która chce wykonać gotowy przebieg bez szukania opcji po całej dokumentacji.

## Pierwsze uruchomienie u znajomego

1. Pobierz `RUT.exe` z najnowszego release GitHub.
2. Uruchom `RUT.exe`.
3. Jeśli program zamknie się od razu, uruchom `start_RUT_debug.cmd` z paczki ZIP albo poproś o logi z `%LOCALAPPDATA%\RUT\onefile\<wersja>\logs`.
4. W programie wejdź w zakładkę `Program`.
5. Użyj `Paczka diagnostyczna`, jeśli trzeba wysłać komuś logi.

Nie kopiuj prywatnych ścieżek z komputera Kazka. RUT powinien korzystać z plików spakowanych w folderze programu albo z plików wskazanych przez aktualnego użytkownika.

## RT3S albo RT3S GPS i OpenGD77

1. W zakładce `Radio` wybierz profil `Retevis RT3S bez GPS (OpenGD77)` albo `Retevis RT3S GPS (OpenGD77)`.
2. Przed pierwszym przejściem z firmware fabrycznego zrób backup oficjalnym CPS producenta.
3. Wprowadź radio w DFU.
4. Użyj `Napraw sterownik DFU`, jeżeli RUT widzi DFU, ale sterownik nie jest `WinUSB`.
5. Uruchom `DMR + flash`.

RT3S bez GPS i RT3S GPS używają firmware z rodziny `OpenMDUV380.bin`. Wariant GPS nie zmienia wyboru promptu głosowego: używaj `UV380-like`.

## Flash DMR bez instalowania Pythona

1. Kodek DMR musi być w paczce RUT w `tools\opengd77_dmr\resources`.
2. Loader OpenGD77 STM32 powinien być w `tools\opengd77_dmr\OpenGD77_STM32_FW_Loader.exe`.
3. Użytkownik nie powinien instalować Pythona ani `pyusb` do zwykłego flashowania release.
4. Jeśli log wspomina o braku Pythona, sprawdź, czy paczka zawiera wbudowany loader EXE.

## Wgranie promptu VPR

1. Radio ma być włączone normalnie, nie w DFU.
2. Kabel USB podłącz po włączeniu radia.
3. Zamknij OpenGD77 CPS i inne programy używające portu COM.
4. W RUT wybierz port COM albo zostaw automatyczne szukanie.
5. Wskaż plik `.vpr` pasujący do radia.
6. Uruchom wgrywanie promptu.

Dla RT3S, MD-UV380 i MD-UV390 wybierz VPR `UV380-like`. Dla GD-77, GD-77S, DM-1801/DM-1801A i RD-5R wybierz `monochrome`.

## Import kanałów i DMR ID

1. W zakładce `Kanały` wpisz swoje DMR ID.
2. Pobierz albo wskaż listę przemienników.
3. Wybierz tryb dopisywania, jeśli nie chcesz nadpisywać swoich kanałów.
4. Usuń tylko rzeczywiste duplikaty.
5. Przed zapisem RUT powinien zrobić backup codepluga.

DMR ID powinno trafić do kanałów i ustawień zgodnie z formatem OpenGD77. Jeśli użytkownik importuje przez OpenGD77 CPS, użyj paczki CSV przygotowanej przez RUT.

## Błąd OpenGD77 CPS `line 2 is not valid in channels`

1. Nie zgaduj, który plik jest winny.
2. W RUT użyj `Sprawdź paczkę CSV`.
3. Jeśli pracujesz z konsoli, uruchom:

```powershell
powershell -ExecutionPolicy Bypass -File .\RUT.ps1 -ValidateCpsDir "C:\folder_paczki_csv"
```

4. Popraw wskazany plik i dopiero wtedy importuj w CPS.

## Gdy prompt albo kanały nie wgrywają się przez COM

1. Sprawdź, czy OpenGD77 CPS potrafi czytać radio na tym samym porcie.
2. Zamknij CPS przed użyciem RUT.
3. Odłącz USB, włącz radio normalnie i podłącz USB ponownie.
4. Wybierz port ręcznie, jeśli automatyczne szukanie wybiera zły.
5. Użyj `Paczka diagnostyczna` i wyślij ZIP z logami.

Samo poprawne flashowanie DFU nie dowodzi, że port COM do trybu normalnego działa. DFU i COM używają innych sterowników i innych trybów radia.

## Test przed publikacją release

1. Zwiększ wersję, jeśli zmienia się `RUT.exe`, `RUT.zip` albo `latest.json`.
2. Uruchom:

```powershell
powershell -ExecutionPolicy Bypass -File .\tools\release\Test-RUT-Release.ps1 -Version 2026.07.16.1 -Build -BuildOneFileExe
```

3. Jeśli sprawdzasz także paczkę CSV:

```powershell
powershell -ExecutionPolicy Bypass -File .\tools\release\Test-RUT-Release.ps1 -Version 2026.07.16.1 -Build -BuildOneFileExe -CsvPackage "C:\folder_csv"
```

4. Publikuj nowy tag, nie podmieniaj assetów starego taga:

```powershell
powershell -ExecutionPolicy Bypass -File .\tools\release\Publish-RUT-GitHubRelease.ps1 -Version 2026.07.16.1
```

Skrypt publikacji odmawia pracy, jeśli release o takim tagu już istnieje.
