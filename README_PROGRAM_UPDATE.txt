Aktualizator programu RUT
==========================================

1) Konfiguracja klienta
- Plik: program_update_config.json
- Pola:
  - app_version: lokalna wersja programu
  - manifest_url: URL do latest.json
  - auto_check_on_start: true/false, automatyczne sprawdzanie aktualizacji przy starcie
  - ui_language: auto/pl/en/de/fr/es/cs (auto = język systemu Windows)
  - radio_profile_id: domyślny profil radia
  - dmr_id: lokalnie zapamiętany DMR ID użytkownika
  - open_gd77_com_port: ręcznie wybrany port COM OpenGD77 albo puste dla trybu automatycznego
  - log_upload_enabled: true/false, automatyczna wysyłka logów diagnostycznych
  - log_upload_url: URL endpointu odbioru logów
  - log_upload_token_source: skąd token; domyślnie env RUT_LOG_UPLOAD_TOKEN albo plik secrets\log_upload_token.txt

2) Build paczki update lokalnie
- Polecenie:
  powershell -ExecutionPolicy Bypass -File .\build_program_update_release.ps1 -Version 2026.07.16.1 -BaseUrl https://github.com/kazek5p-git/RUT/releases/latest/download -PackageBaseUrl https://github.com/kazek5p-git/RUT/releases/download/v2026.07.16.1 -BuildOneFileExe

- Wyniki:
  - EXE: dist\program_updater_release\<version>\RUT.exe
  - ZIP: dist\program_updater_release\<version>\RUT.zip
  - Manifest: dist\program_updater_release\<version>\latest.json

3) Publikacja na GitHubie
- Release powinien mieć tag w formacie:
  v2026.07.16.1

- Do release dołącz:
  - RUT.exe
  - RUT.zip
  - latest.json

- Stałe linki po publikacji:
  - https://github.com/kazek5p-git/RUT/releases/latest/download/RUT.exe
  - https://github.com/kazek5p-git/RUT/releases/latest/download/RUT.zip
  - https://github.com/kazek5p-git/RUT/releases/latest/download/latest.json

4) Użycie w aplikacji
- W GUI: przycisk "Aktualizuj program" (Alt+A)
- Auto-check przy starcie jest włączony, gdy auto_check_on_start=true
- Przed aktualizacją RUT tworzy kopię rollback w backups\program_update_rollbacks
- Aplikacja:
  - pobiera manifest,
  - porównuje wersje,
  - pobiera ZIP,
  - weryfikuje SHA256,
  - uruchamia helper podmiany plików,
  - zamyka i uruchamia się ponownie.
