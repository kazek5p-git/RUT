# Historia zmian dokumentacji

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
- RUT dekoduje teraz tresc latest.json jako UTF-8 przed ConvertFrom-Json.

## 2026.05.17.7

- Naprawiono b??d startu: funkcje pomocnicze profili OpenGD77 by?y omy?kowo zagnie?d?one w `Refresh-RadioProfilesCombo` przed blokiem `param`.
- Objaw b??du: program zamyka? si? natychmiast, a log zawiera? `The term 'param' is not recognized` przy `Refresh-RadioProfilesCombo`.

## 2026.05.17.6

- Dodano `start_RUT_diagnose.cmd` do sprawdzania brakuj?cych sk?adnik?w.
- Dodano `tools\diagnostics\Test-RUT-Components.ps1`.
- Diagnostyka zapisuje wynik do `logs\RUT_components_*.txt` i rozr??nia `OK`, `WARN` oraz `FAIL`.

## 2026.05.17.5

- Dodano diagnostyczne logi startu jako zwyk?e pliki `.txt`.
- Launcher `start_RUT.vbs` tworzy `logs\RUT_last_start.txt`, `logs\RUT_launcher_*.txt` i `logs\RUT_powershell_*.txt`.
- Dodano `start_RUT_debug.cmd`, kt?ry zostawia okno konsoli i zapisuje log tekstowy, gdy program zamyka si? od razu.
- G??wny log RUT ma teraz rozszerzenie `.txt`, a `logs\RUT_last_log.txt` wskazuje ostatni g??wny log.

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
