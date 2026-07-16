# Rozwiązywanie problemów

Ten rozdział zbiera najczęstsze awarie i konkretne działania.

## RUT czeka na DFU i nic się nie dzieje

Sprawdź:

1. Czy radio jest naprawdę w DFU, a nie włączone normalnie.
2. Czy kabel USB przesyła dane, a nie tylko ładuje.
3. Czy Windows wydał dźwięk podłączenia urządzenia.
4. Czy w Menedżerze urządzeń widać urządzenie DFU.
5. Czy zaznaczona jest opcja automatycznej instalacji WinUSB.

Jeśli sterownik jest zły, użyj Zadig i ustaw WinUSB dla urządzenia DFU.

## Komputer piknął, ale RUT nadal nie widzi DFU

Piknięcie oznacza tylko, że Windows wykrył urządzenie. RUT potrzebuje jeszcze poprawnego sterownika i właściwego identyfikatora urządzenia. Sprawdź Menedżer urządzeń. Jeżeli urządzenie jest w złej kategorii albo ma ostrzeżenie, napraw sterownik.

## Flash kończy się błędem po wykryciu DFU

Możliwe przyczyny:

- zły sterownik DFU,
- zajęte urządzenie USB,
- niezgodny plik firmware,
- brak wbudowanego loadera `OpenGD77_STM32_FW_Loader.exe` albo, w starszych wersjach, brak Pythona lub `pyusb`,
- przerwanie połączenia USB.

Działania:

1. Odłącz USB.
2. Wyłącz radio albo wyjmij i włóż baterię, jeśli radio nie reaguje.
3. Wejdź ponownie w DFU.
4. Podłącz USB.
5. Spróbuj flashowania jeszcze raz.

## RUT nie widzi portu COM

Dotyczy kanałów, backupu i udźwiękowienia. Te funkcje wymagają trybu normalnego.

Sprawdź:

1. Radio ma być normalnie włączone, nie w DFU.
2. Zamknij OpenGD77 CPS.
3. Zamknij inne programy radiowe i terminale COM.
4. Odłącz i podłącz USB.
5. Sprawdź Menedżer urządzeń i numer portu COM.

## Brak DefaultOpenGD77.g77

Niektóre operacje codepluga potrzebują bazowego pliku z instalacji OpenGD77 CPS:

- `C:\Program Files (x86)\OpenGD77CPS\DefaultOpenGD77.g77`
- `C:\Program Files\OpenGD77CPS\DefaultOpenGD77.g77`

Jeśli go nie ma, zainstaluj OpenGD77 CPS albo napraw instalację CPS.

## OpenGD77 CPS przeszkadza w operacji

CPS może trzymać port COM. Jeśli RUT zgłasza, że port jest zajęty, zamknij CPS i spróbuj ponownie. RUT czasem uruchamia CPS automatycznie do operacji importu/eksportu, ale przy bezpośrednim odczycie COM CPS powinien być zamknięty.

## Radio pokazuje tylko ekran startowy OpenGD77

Jeśli radio uruchamia się, ale funkcje nie działają:

1. Spróbuj wejść w tryb normalny i wgrać poprawne udźwiękowienie.
2. Jeżeli firmware jest uszkodzony, wejdź w DFU i wgraj firmware ponownie.
3. Jeżeli to RT3S po pierwszym flashowaniu, upewnij się, że używasz profilu RT3S i pliku `OpenMDUV380.bin`.

## Gdzie są logi

RUT zapisuje logi w:

`logs\RUT_YYYYMMDD_HHMMSS.txt`

W zakładce `Program` można kliknąć `Paczka diagnostyczna`. RUT utworzy ZIP w:

`diagnostics\packages`

Paczka zawiera logi, konfigurację bez sekretów, listę portów COM, informacje o sterowniku DFU i spis ważnych plików programu. To jest najwygodniejszy plik do wysłania komuś, kto ma pomóc w diagnozie.

W razie problemu najważniejsze są:

- ostatnie linie logu w oknie programu,
- najnowszy plik w folderze `logs`,
- komunikat błędu z okna dialogowego.

## Co wysłać komuś do diagnozy

Najlepiej wysłać:

- paczkę ZIP z przycisku `Paczka diagnostyczna`,
- model radia,
- czy radio było w DFU czy w trybie normalnym,
- ostatnie 20-40 linii logu,
- nazwę operacji, którą uruchomiono,
- informację, czy Windows widzi DFU albo COM,
- wersję RUT z manifestu lub release.

## OpenGD77 CPS: line 2 is not valid in channels

Ten błąd zwykle oznacza, że CPS dostał plik CSV z niezgodnym separatorem, brakującą kolumną, uszkodzonym nagłówkiem albo niepoprawną wartością już w pierwszym wierszu danych.

W RUT użyj przycisku `Sprawdź paczkę CSV` w zakładce `Kanały` i wskaż folder z plikami importu. Jeśli walidator pokaże błąd, popraw wskazany plik albo wygeneruj paczkę ponownie najnowszym RUT-em.

Jeśli paczka była tworzona ręcznie, używaj kodowania UTF-8 bez BOM albo zwykłego ANSI z polskimi znakami zgodnego z systemem, ale nie mieszaj separatorów `;` i `,` w jednej paczce.
## Program zamyka się od razu po uruchomieniu

Najpierw uruchom:

`start_RUT_debug.cmd`

Ten plik zostawia widoczne okno i zapisuje diagnostykę do zwykłych plików tekstowych `.txt` w folderze `logs`. Po takim uruchomieniu wyślij albo sprawdź:

- `logs\RUT_last_start.txt` - krótka informacja, które pliki są z ostatniego startu.
- `logs\RUT_launcher_YYYYMMDD_HHMMSS.txt` - log launchera VBS.
- `logs\RUT_powershell_YYYYMMDD_HHMMSS.txt` - błędy z PowerShella, jeśli `RUT.ps1` nie wystartował.
- `logs\RUT_last_log.txt` - wskazuje główny log RUT, jeśli skrypt zdążył wystartować.
- `logs\RUT_YYYYMMDD_HHMMSS.txt` - główny log programu.

Najczęstsze przyczyny natychmiastowego zamknięcia:

- ZIP nie został rozpakowany, tylko program uruchomiono ze środka archiwum.
- Windows zablokował pliki pobrane z internetu.
- Antywirus albo polityka firmowa blokuje `.vbs` lub PowerShell.
- Brakuje PowerShella albo jest uszkodzony.
- Brakuje pliku `RUT.ps1`, bo paczka została rozpakowana niepełnie.
- Skrypt zatrzymał się na błędzie składni albo brakującym komponencie .NET/Windows Forms.

## Podejrzenie brakujących składników

Uruchom:

`start_RUT_diagnose.cmd`

Ten plik nie uruchamia GUI. Sprawdza składniki potrzebne do startu i wybrane składniki opcjonalne. Wynik zapisuje do:

`logs\RUT_components_YYYYMMDD_HHMMSS.txt`

W logu zobaczysz pozycje `OK`, `WARN` i `FAIL`. Najważniejsze dla samego startu są:

- `powershell.exe`,
- `System.Windows.Forms`,
- `System.Drawing`,
- `RUT.ps1`,
- `program_update_config.json`,
- rozpakowane foldery `docs`, `assets`, `dist` i `tools`.

Pozycje opcjonalne, takie jak Python, OpenGD77 CPS i plik kodeka DMR, mogą mieć `WARN`. Od wersji `2026.05.18.9` Python nie jest wymagany do `DMR + flash`, jeśli działa wbudowany `OpenGD77_STM32_FW_Loader.exe`.

## Nie znaleziono skryptu naprawy sterownika

Jeżeli pojawia się błąd podobny do:

`Nie znaleziono skryptu naprawy sterownika: ...\tools\driver\elevate_install_winusb_dfu.ps1`

to używana paczka RUT jest niepełna albo zbyt stara. Pobierz najnowszy jedno-plikowy `RUT.exe` z GitHuba i uruchom go ponownie. Od wersji `2026.05.18.6` folder `tools\driver` jest częścią paczki release, a diagnostyka sprawdza jego obecność.

## Okno PowerShell naprawy sterownika jest puste albo znika

W wersjach starszych niż `2026.05.18.7` skrypt naprawy DFU mógł zamknąć okno zbyt szybko i nie uruchamiał Zadiga jako widocznego fallbacku. Pobierz najnowszy `RUT.exe` i spróbuj ponownie.

Od wersji `2026.05.18.7` okno naprawy:

- pokazuje kolejne kroki w konsoli,
- zapisuje log do `logs\driver_install_YYYYMMDD_HHMMSS.txt`,
- sprawdza DFU `USB\VID_0483&PID_DF11` oraz `USB\VID_1FC9&PID_0094`,
- próbuje `pnputil`, wymuszenia przez Windowsowe `newdev.dll` i pakietowego instalatora libwdi,
- jeśli automatyka nie wystarczy, otwiera `zadig-2.9.exe`.

W wersji `2026.05.18.8` RUT przed Zadigiem próbuje jeszcze wymusić sterownik przez systemowe `UpdateDriverForPlugAndPlayDevices`, więc w wielu przypadkach użytkownik nie musi nic klikać ręcznie.

W Zadig wybierz `Options > List All Devices`, potem urządzenie DFU/STM32/OpenGD77/Retevis, ustaw sterownik `WinUSB` i kliknij `Install Driver` albo `Replace Driver`. Po zamknięciu Zadiga skrypt sprawdzi sterownik jeszcze raz.

## Błąd: Nie znaleziono Pythona z biblioteka pyusb

Ten błąd dotyczy wersji starszych niż `2026.05.18.9` albo niepełnej paczki bez `tools\opengd77_dmr\OpenGD77_STM32_FW_Loader.exe`. Pobierz najnowszy jedno-plikowy `RUT.exe`. Aktualny RUT używa wbudowanego loadera EXE i nie wymaga instalowania Pythona.
