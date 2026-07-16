RUT - uruchamianie GUI

Wersje release nie wymagają instalacji Pythona do funkcji DMR + flash, jeśli w paczce jest wbudowany `OpenGD77_STM32_FW_Loader.exe`.
Interfejs używa natywnych kontrolek Windows Forms i ma poprawki pod czytnik ekranu NVDA: zakładki, status, ostatni komunikat, skróty klawiaturowe i komunikat startowy.
Launcher GUI obsługuje Windows PowerShell 5 (`powershell.exe`) oraz PowerShell 7+ (`pwsh.exe`).
Program rotuje logi automatycznie: domyślnie 30 dni i maksymalnie 120 plików.

1. Najprościej
   - Pobierz i uruchom `RUT.exe` z:
     https://github.com/kazek5p-git/RUT/releases/latest/download/RUT.exe
   - Język interfejsu domyślnie: Auto, czyli język systemu Windows z fallbackiem do EN.
   - Dostępne języki: Polski, English, Deutsch, Francais, Espanol, Cestina.
   - Okno jest podzielone na zakładki: Radio, Kanały, Firmware i głos, Status i log, Program.
   - Po starcie fokus czytnika ekranu trafia na pasek zakładek.
   - Modele w GUI: TYT UV390 Plus 10W, Retevis RT3S bez GPS, Retevis RT3S GPS, Quansheng UV-K5/UV-K6, Baofeng/PMR.
   - RT3S/RT3S GPS używa firmware OpenGD77 z rodziny MDUV380 i flashowania DFU przez funkcję DMR + flash.
   - Przycisk `Backup radia` zapisuje backup codepluga OpenGD77 `.g77` do folderu `<folder RUT>\backups\radio`.
   - Przed zapisem kanałów i promptów RUT próbuje zrobić automatyczny backup codepluga OpenGD77.
   - Przycisk `Sprawdź paczkę CSV` pomaga wykryć błędy importu OpenGD77 CPS, na przykład `line 2 is not valid in channels`.
   - Przycisk `Paczka diagnostyczna` tworzy ZIP z logami i informacjami potrzebnymi do diagnozy.
   - Przycisk `Cofnij aktualizację` przywraca kopię programu utworzoną przed aktualizacją RUT.
   - Przycisk `Napraw sterownik DFU` ręcznie uruchamia kreator naprawy WinUSB.
   - Część komunikatów technicznych może być wyświetlana po angielsku.
   - Skróty: Alt+S Sprawdź, Alt+T Start, Alt+A Aktualizuj program, Alt+Y Sprawdź paczkę CSV, Alt+J Napraw sterownik DFU, Alt+G Paczka diagnostyczna, Alt+O Cofnij aktualizację, Alt+L Log, Alt+D Timeout, Alt+F4 Zamknij, F1 Pomoc.
   - Tab i Shift+Tab przechodzą po kontrolkach.
   - Alt+F4 i przycisk X pytają o potwierdzenie zamknięcia.
   - W trakcie aktualizacji zamknięcie programu jest blokowane.
   - Aktualizator programu pobiera manifest z:
     https://github.com/kazek5p-git/RUT/releases/latest/download/latest.json
   - Auto-check aktualizacji programu przy starcie jest włączony, jeśli `auto_check_on_start=true` w `program_update_config.json`.
   - Token uploadu logów: zmienna środowiskowa `RUT_LOG_UPLOAD_TOKEN` albo plik `<folder RUT>\secrets\log_upload_token.txt`.
   - Pełna dokumentacja offline: `<folder RUT>\docs\README.md`.
   - Jeśli program zamyka się od razu, uruchom `start_RUT_debug.cmd`. Okno zostanie otwarte, a diagnostyka zapisze się w plikach `.txt` w folderze `logs`.
   - Jeśli podejrzewasz brak składników, uruchom `start_RUT_diagnose.cmd`. Wynik zapisze się jako `logs\RUT_components_YYYYMMDD_HHMMSS.txt`.
   - Najważniejsze pliki diagnostyczne po starcie: `logs\RUT_last_start.txt`, `logs\RUT_launcher_YYYYMMDD_HHMMSS.txt`, `logs\RUT_powershell_YYYYMMDD_HHMMSS.txt` oraz `logs\RUT_last_log.txt`.
   - Główny log programu: `<folder RUT>\logs\RUT_YYYYMMDD_HHMMSS.txt`.

2. Wersja z ZIP
   - Skrypt GUI: `<folder RUT>\RUT.ps1`
   - Launcher bez konsoli: `<folder RUT>\start_RUT.vbs`
   - Backend CLI: `<folder RUT>\dist\OpenGD77_UV390_BackendCLI.exe`

3. Aliasy zgodności
   - `<folder RUT>\start_OpenGD77_UV390_A11y.vbs`
   - `<folder RUT>\start_radio_updater_and_tools.vbs`

4. Narzędzia sterownika DFU
   - Skrypty zgodności zostały w root, z tymi samymi nazwami co wcześniej.
   - Rzeczywiste narzędzia i skrypty są w: `<folder RUT>\tools\driver`
