# Historia zmian dokumentacji

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
