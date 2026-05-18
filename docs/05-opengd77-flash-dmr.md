# OpenGD77, DFU i DMR + flash

Ten rozdział opisuje operacje firmware dla UV390 i RT3S.

## Tryb DFU

Firmware wgrywa się w trybie DFU. Typowa procedura dla radia z rodziny UV380/UV390/RT3S:

1. Wyłącz radio.
2. Przytrzymaj odpowiednią kombinację przycisków dla trybu aktualizacji. W RUT dla UV390 opis jest: `PTT + S1`, potem włącz radio.
3. Ekran zwykle zostaje czarny.
4. Podłącz USB.
5. Windows powinien wykryć urządzenie DFU.

Jeżeli komputer piknie po podłączeniu, to znaczy, że Windows coś wykrył. Nie znaczy to jeszcze, że sterownik DFU jest poprawny.

## Sterownik WinUSB

Do DFU potrzebny jest poprawny sterownik, zwykle WinUSB. RUT ma opcję:

`Po braku DFU spróbuj automatycznej instalacji sterownika WinUSB`

RUT próbuje naprawić sterownik automatycznie przez `pnputil`, `newdev.dll` i pakietowy instalator libwdi. Jeśli automatyka nie wystarczy, otworzy pakietowy `zadig-2.9.exe` jako fallback. W Zadig wybierz urządzenie DFU/STM32/OpenGD77/Retevis i ustaw `WinUSB`. Szczegóły są w [08-rozwiazywanie-problemow.md](08-rozwiazywanie-problemow.md).

## UV390 Plus 10W

Profil `TYT UV390 Plus 10W (OpenGD77)` używa backendu:

`dist\OpenGD77_UV390_BackendCLI.exe`

Ten profil zachowuje dotychczasowe działanie RUT dla UV390 Plus 10W.

Firmware w paczce:

`dist\firmware_extracted\OpenMDUV380_10W_PLUS.bin`

## RT3S bez GPS i RT3S GPS

Profile RT3S używają ścieżki `DMR + flash`, nie starego backendu UV390. RUT wybiera:

`dist\firmware_extracted\OpenMDUV380.bin`

oraz model loadera:

`MD-UV380`

Oba profile RT3S mają ostrzeżenie o backupie przed flashowaniem.

## DMR + flash

Funkcja `DMR + flash` robi trzy rzeczy:

1. Bierze otwarte firmware OpenGD77 z paczki RUT.
2. Bierze plik z kodekiem DMR.
3. Scala je i wgrywa wynik przez DFU.

Plik kodeka DMR jest częścią paczki RUT i powinien znajdować się tutaj:

`tools\opengd77_dmr\resources\MD9600-CSV(2571V5)-V26.45.bin`

Nie używaj ścieżek z komputera osoby, która budowała paczkę. Awaryjnie można wskazać własny plik przez zmienną środowiskową `RUT_DMR_CODEC_PATH`, ale standardowy release nie powinien tego wymagać.

Helper sprawdza SHA256 pliku kodeka. Jeżeli plik jest inny, operacja zostanie przerwana.

## Wbudowany loader OpenGD77

Od wersji `2026.05.18.9` ścieżka `DMR + flash` używa wbudowanego pliku:

`tools\opengd77_dmr\OpenGD77_STM32_FW_Loader.exe`

Ten plik jest zbudowany z loadera OpenGD77 i ma spakowane zależności Pythona, w tym `pyusb`. Użytkownik nie musi instalować Pythona ani wykonywać `pip install pyusb`.

Helper:

`tools\opengd77_dmr\Run_OpenGD77_DMR_Flash.ps1`

najpierw uruchamia wbudowany EXE. Dopiero jeśli tego pliku nie ma, próbuje awaryjnie znaleźć lokalny `python.exe` albo `py.exe` z biblioteką `pyusb`.

## Nie przerywaj flashowania

W czasie flashowania:

- nie odłączaj USB,
- nie wyjmuj baterii,
- nie zamykaj RUT,
- nie usypiaj komputera.

Jeżeli flashowanie przerwie się na etapie DFU, zwykle można ponownie wejść w DFU i spróbować jeszcze raz. Szczegóły awaryjne są w rozdziale problemów.
