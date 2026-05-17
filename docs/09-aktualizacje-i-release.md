# Aktualizacje i release

RUT ma własny mechanizm aktualizacji programu oraz paczki release na GitHubie.

## Aktualizacja w programie

Przycisk `Aktualizuj program` pobiera manifest:

`https://github.com/kazek5p-git/RUT/releases/latest/download/latest.json`

Manifest zawiera:

- wersję,
- URL paczki ZIP,
- SHA256,
- rozmiar pliku,
- datę wydania.

RUT porównuje wersję lokalną z wersją zdalną i pobiera ZIP, jeśli jest nowszy.

## Auto-check przy starcie

W pliku `program_update_config.json` jest opcja:

`auto_check_on_start`

Jeśli jest ustawiona na `true`, RUT sprawdza aktualizację po starcie.

## Stałe linki GitHub

- Najnowszy ZIP: `https://github.com/kazek5p-git/RUT/releases/latest/download/RUT.zip`
- Manifest: `https://github.com/kazek5p-git/RUT/releases/latest/download/latest.json`
- Strona release: `https://github.com/kazek5p-git/RUT/releases/latest`

## Budowanie release lokalnie

Skrypt budujący:

```powershell
powershell -ExecutionPolicy Bypass -File .\build_program_update_release.ps1 -Version 2026.05.17.4 -BaseUrl https://github.com/kazek5p-git/RUT/releases/latest/download
```

Wyniki trafiają do:

`dist\program_updater_release\<wersja>`

Najważniejsze pliki:

- `RUT.zip`,
- `latest.json`.

## Co powinno wejść do ZIP

ZIP powinien zawierać między innymi:

- `RUT.ps1`,
- launchery `.vbs`,
- `program_update_config.json`,
- `README_GUI_RUN.txt`,
- `docs`,
- `assets`,
- `tools\opengd77_dmr`,
- `dist\firmware_extracted`,
- `dist\OpenGD77_UV390_BackendCLI.exe`,
- `secrets\README.txt`.

ZIP nie powinien zawierać prawdziwych tokenów ani prywatnych sekretów.

## Publikacja na GitHubie

Release publikuje się jako tag, na przykład:

`v2026.05.17.4`

Do release trzeba dołączyć:

- `RUT.zip`,
- `latest.json`.

Po publikacji trzeba sprawdzić, czy link `releases/latest/download/RUT.zip` prowadzi do nowego tagu.