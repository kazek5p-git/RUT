# Struktura plików RUT

Ten rozdział opisuje najważniejsze foldery i pliki w instalacji RUT.

## Jednoplikowy EXE

- `RUT.exe` z release GitHub jest samorozpakowującym wariantem programu.
- Po uruchomieniu rozpakowuje bieżącą wersję do `%LOCALAPPDATA%\RUT\onefile\<wersja>`.
- W rozpakowanym folderze są te same pliki, które zawiera `RUT.zip`, w tym `RUT.ps1`, backend, firmware, narzędzia DMR i dokumentacja.
- Zmienna środowiskowa `RUT_ONEFILE_EXTRACT_DIR` może awaryjnie wskazać inny katalog rozpakowania.

## Pliki startowe

- `start_RUT.vbs` - najprostszy launcher bez widocznej konsoli.
- `start_RUT_debug.cmd` - launcher diagnostyczny, zostawia okno i zapisuje pliki `.txt` w `logs`.
- `start_RUT_diagnose.cmd` - sprawdza brakuj?ce sk?adniki i zapisuje `logs\RUT_components_*.txt`.
- `RUT.ps1` - główny program GUI.
- `radio_updater_and_tools.ps1` - alias zgodności uruchamiający RUT.
- `OpenGD77_UV390_A11y.ps1` - alias zgodności uruchamiający RUT.

## Konfiguracja

- `program_update_config.json` - wersja lokalna, manifest aktualizacji, język, profil radia, DMR ID i ustawienia uploadu logów.
- `install_id.txt` - lokalny identyfikator instalacji.
- `secrets\README.txt` - opis miejsca na lokalne sekrety. Prawdziwe tokeny nie powinny trafiać do release ZIP.

## Dokumentacja

- `README_GUI_RUN.txt` - krótka instrukcja uruchomienia.
- `README_PROGRAM_UPDATE.txt` - starsza notatka o aktualizacji programu.
- `docs\README.md` - główny indeks dokumentacji.
- `docs\*.md` - rozdziały dokumentacji offline.

## Firmware i narzędzia

- `dist\OpenGD77_UV390_BackendCLI.exe` - backend UV390.
- `dist\firmware_extracted\OpenMDUV380_10W_PLUS.bin` - firmware dla UV390 Plus 10W.
- `dist\firmware_extracted\OpenMDUV380.bin` - firmware dla RT3S/MDUV380.
- `tools\opengd77_dmr\Run_OpenGD77_DMR_Flash.ps1` - helper DMR + flash.
- `tools\opengd77_dmr\opengd77_stm32_firmware_loader.py` - loader OpenGD77 STM32.
- `tools\opengd77_dmr\libusb-1.0.dll` - biblioteka USB dla helpera.

## Dane robocze

- `downloads\channel_lists` - pobrane i wygenerowane listy kanałów.
- `downloads\voice_prompts` - pobrane pakiety głosowe.
- `backups\radio` - backupy codepluga OpenGD77 i instrukcje backupu RT3S.
- `logs` - logi pracy RUT.
- `diagnostics` - pliki diagnostyczne, jeśli dana funkcja je tworzy.

## Release

- `dist\program_updater_release\<wersja>` - lokalnie zbudowany release.
- `dist\program_updater_release\<wersja>\RUT.zip` - paczka do publikacji i autoaktualizacji.
- `dist\program_updater_release\<wersja>\RUT.exe` - jednoplikowy samorozpakowujący wariant programu.
- `dist\program_updater_release\<wersja>\latest.json` - manifest aktualizacji.

## Czego nie kasować pochopnie

Nie kasuj bez potrzeby:

- `backups`,
- `downloads`,
- `logs`,
- `secrets`,
- `program_update_config.json`.

Przy aktualizacji programu najlepiej nadpisywać pliki programu, ale zachować dane robocze i backupy.
## Narzędzia sterownika DFU

Release zawiera folder `tools\driver`. Są tam skrypty i pliki INF używane przez opcję automatycznej naprawy sterownika WinUSB dla DFU. Ten folder musi być obecny także po rozpakowaniu jedno-plikowego `RUT.exe` do `%LOCALAPPDATA%\RUT\onefile\<wersja>`.
