# Historia zmian dokumentacji

## 2026.07.16.1

- Dodano automatyczny backup codepluga przed zapisem kanałów i wgrywaniem promptów.
- Dodano przycisk `Paczka diagnostyczna`, który tworzy ZIP z logami, konfiguracją bez sekretów, portami COM i listą ważnych plików.
- Dodano przycisk `Cofnij aktualizację`, oparty o kopię programu tworzoną przed aktualizacją RUT.
- Dodano ręczny przycisk `Napraw sterownik DFU`.
- Dodano walidację paczek CSV OpenGD77 CPS, także w trybie konsolowym `-ValidateCpsDir`.
- Paczki CSV tworzone przez RUT zawierają podstawowe pliki pomocnicze kontaktów i list TG.
- Dodano modularny zestaw narzędzi release w `tools\release`: wspólny moduł kontroli, zbiorczy test release i bezpieczną publikację GitHub bez podmieniania istniejących tagów.
- Dodano rozdział `11-scenariusze.md` z gotowymi przebiegami dla użytkownika i osoby pomagającej zdalnie.

## 2026.05.19.3

- Wgrywanie promptów `.vpr` używa teraz ścieżki OpenGD77 Direct, tej samej klasy komunikacji COM co odczyt codepluga.
- Dla radii STM32, takich jak RT3S/UV380/UV390, RUT wybiera adres promptów `0xAF400` i komendę zapisu `X`, zgodnie z OpenGD77 CPS.
- Szybki test portu COM odczytuje `RadioInfo`, dzięki czemu log pokazuje typ radia, build, bufor USB i plan zapisu.
## 2026.05.18.9

- Dodano wbudowany `OpenGD77_STM32_FW_Loader.exe` dla funkcji `DMR + flash`, zbudowany z loadera OpenGD77 i spakowany z `pyusb`.
- `Run_OpenGD77_DMR_Flash.ps1` najpierw używa wbudowanego EXE, więc użytkownik nie musi instalować Pythona ani `pyusb`.
- Python zostaje tylko jako fallback deweloperski, gdy wbudowany EXE nie istnieje.
- Diagnostyka sprawdza wbudowany loader EXE i nie zgłasza braku Pythona jako problemu, jeśli loader działa.
## 2026.05.18.8

- Dodano automatyczne wymuszanie przypięcia WinUSB przez Windowsowe `newdev.dll` (`UpdateDriverForPlugAndPlayDevices`) przed awaryjnym uruchomieniem Zadiga.
- Naprawa sterownika próbuje teraz kolejno: `wdi-simple` jeśli istnieje, `pnputil`, wymuszenie przez `newdev.dll`, pakietowy instalator libwdi, usunięcie starego STTub30, a dopiero na końcu Zadig.
- Self-test skryptu sterownika sprawdza dostępność API `newdev.dll`.
## 2026.05.18.7

- Przepisano skrypt naprawy sterownika DFU WinUSB: okno PowerShell pokazuje teraz postęp, zapisuje log i nie zamyka się od razu przy błędzie.
- Dodano obsługę identyfikatorów DFU `USB\VID_0483&PID_DF11` oraz `USB\VID_1FC9&PID_0094`.
- Dodano kolejne metody naprawy: `pnputil`, pakietowy instalator libwdi i awaryjne otwarcie `zadig-2.9.exe` z instrukcją wyboru WinUSB.
- Diagnostyka i build release sprawdzają teraz obecność `zadig-2.9.exe` oraz `installer_x64.exe`.

## 2026.05.18.6

- Do paczki release dodano `tools\driver`, czyli skrypt naprawy sterownika DFU WinUSB oraz pliki INF używane przy automatycznej naprawie.
- Skrypt budowania release przerywa pracę, jeśli w paczce brakuje krytycznych plików, w tym `tools\driver\elevate_install_winusb_dfu.ps1`.
- Diagnostyka `start_RUT_diagnose.cmd` sprawdza teraz obecność skryptu naprawy DFU i pliku `usb_device.inf`.

## 2026.05.18.5

- Dodano własny dostępny kontroler zakładek dla RUT. NVDA nie widzi już 10 elementów w natywnym `TabControl` WinForms.
- Dostępne nazwy zakładek zawierają numer, na przykład `Kanały. Zakładka 2 z 5`.
- Poprawkę zweryfikowano w podglądzie mowy NVDA.

## 2026.05.18.4

- Poprawiono dostępność zakładek: RUT nie nadaje już stronom zakładek dodatkowej roli `PageTab`, bo NVDA liczył wtedy 5 natywnych zakładek plus 5 stron, czyli `1 z 10`.
- Numerowanie zakładek zostaje po stronie natywnego kontrolera Windows, dzięki czemu powinno być `1 z 5`.

## 2026.05.18.3

- RUT pobiera manifest aktualizacji z parametrem anty-cache, żeby Windows PowerShell nie używał starego `latest.json`.
- Skrypt release obsługuje osobny `PackageBaseUrl`, dzięki czemu manifest może wskazywać assety z konkretnego taga, a konfiguracja programu nadal sprawdza ruchomy `latest`.

## 2026.05.18.2

- Główne okno RUT podzielono na zakładki: Radio, Kanały, Firmware i głos, Status i log oraz Program.
- Fokus po starcie trafia na pasek zakładek, a nazwy dostępności zawierają numer, na przykład `Radio. Zakładka 1 z 5`.
- Dodano budowanie jednoplikowego `RUT.exe`, który ma w środku paczkę RUT i sam rozpakowuje się do `%LOCALAPPDATA%\RUT\onefile\<wersja>`.
- Manifest release może zawierać pola `onefile_url`, `onefile_sha256` i `onefile_file_size`.

## 2026.05.18.1

- Usunięto zaszytą ścieżkę do kodeka DMR z profilu `C:\Users\Kazek`.
- Kodek DMR jest teraz pakowany w `tools\opengd77_dmr\resources` i RUT szuka go w katalogu programu.
- Diagnostyka komponentów sprawdza kodek DMR w paczce RUT, a nie w prywatnym katalogu Telegrama.
- Usunięto twarde `D:\` z wyboru referencyjnego pliku promptów głosowych.

## 2026.05.17.8

- Naprawiono auto-check aktualizacji programu dla manifestu pobieranego z GitHuba jako bajty application/octet-stream.
- RUT dekoduje teraz treść `latest.json` jako UTF-8 przed `ConvertFrom-Json`.

## 2026.05.17.7

- Naprawiono błąd startu: funkcje pomocnicze profili OpenGD77 były omyłkowo zagnieżdżone w `Refresh-RadioProfilesCombo` przed blokiem `param`.
- Objaw błędu: program zamykał się natychmiast, a log zawierał `The term 'param' is not recognized` przy `Refresh-RadioProfilesCombo`.

## 2026.05.17.6

- Dodano `start_RUT_diagnose.cmd` do sprawdzania brakujących składników.
- Dodano `tools\diagnostics\Test-RUT-Components.ps1`.
- Diagnostyka zapisuje wynik do `logs\RUT_components_*.txt` i rozróżnia `OK`, `WARN` oraz `FAIL`.

## 2026.05.17.5

- Dodano diagnostyczne logi startu jako zwykłe pliki `.txt`.
- Launcher `start_RUT.vbs` tworzy `logs\RUT_last_start.txt`, `logs\RUT_launcher_*.txt` i `logs\RUT_powershell_*.txt`.
- Dodano `start_RUT_debug.cmd`, który zostawia okno konsoli i zapisuje log tekstowy, gdy program zamyka się od razu.
- Główny log RUT ma teraz rozszerzenie `.txt`, a `logs\RUT_last_log.txt` wskazuje ostatni główny log.

## 2026.05.17.4

- Dodano pełną dokumentację offline w folderze `docs`.
- Dodano rozdziały o szybkim starcie, interfejsie, obsługiwanych radiach, backupie, RT3S, DMR, kanałach, udźwiękowieniu, problemach i release.
- Dokumentacja jest pisana pod czytanie NVDA: zwykłe nagłówki, krótkie listy i bez tabel wymagających nawigacji komórkami.

## 2026.05.17.3

- Dodano opcję `Backup radia`.
- Dodano ostrzeżenie backupu przed flashowaniem RT3S.

## 2026.05.17.2

- Dodano profile Retevis RT3S bez GPS i Retevis RT3S GPS.
- Dodano firmware `OpenMDUV380.bin` do paczki.
