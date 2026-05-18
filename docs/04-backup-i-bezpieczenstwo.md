# Backup i bezpieczeństwo

Ten rozdział warto przeczytać przed pierwszym flashowaniem radia, szczególnie RT3S.

## Co RUT potrafi zbackupować automatycznie

Przycisk `Backup radia` odczytuje codeplug OpenGD77 `.g77` z radia w trybie normalnym przez port COM. Backup trafia do folderu:

`<folder RUT>\backups\radio`

W środku powstaje podfolder z nazwą profilu i datą. RUT zapisuje tam:

- plik `.g77` z codeplugiem OpenGD77,
- `README_BACKUP.txt` z opisem backupu,
- informację o porcie COM i danych firmware, jeśli radio je zwróciło,
- SHA256 pliku `.g77`.

## Czego RUT nie potrafi zbackupować automatycznie

RUT nie odczytuje wiarygodnie fabrycznej kalibracji z oryginalnego firmware Retevis/TYT. Dotyczy to przede wszystkim RT3S przed pierwszym przejściem na OpenGD77.

Jeżeli RT3S ma jeszcze fabryczny firmware, zrób backup oficjalnym CPS producenta przed flashowaniem. Zachowaj:

- oryginalny codeplug,
- kalibrację,
- wszystkie pliki eksportu, które CPS pozwala zapisać.

Najlepiej skopiuj te pliki do folderu utworzonego przez `Backup radia`, żeby wszystkie kopie były w jednym miejscu.

## Kiedy kliknąć Backup radia

Kliknij `Backup radia`, gdy:

- radio jest już na OpenGD77,
- radio jest włączone normalnie,
- Windows widzi port COM,
- CPS i inne programy nie trzymają portu COM.

Nie klikaj tego przycisku, gdy radio jest w DFU. W DFU nie ma normalnego portu COM do odczytu codepluga.

## Backup przed flashowaniem RT3S

Dla profili `Retevis RT3S bez GPS` i `Retevis RT3S GPS` RUT pokazuje ostrzeżenie przed flashowaniem. To ostrzeżenie nie blokuje pracy na siłę, ale przypomina o backupie kalibracji.

Zasada praktyczna:

1. Fabryczny RT3S: najpierw backup w CPS producenta.
2. RT3S już na OpenGD77: backup w RUT przyciskiem `Backup radia`.
3. Dopiero potem `DMR + flash` lub inne operacje firmware.

## Gdzie trzymać backupy

Domyślny folder:

`<folder RUT>\backups\radio`

Nie kasuj tego folderu przy aktualizacji programu. Aktualizacja RUT z ZIP-a powinna być robiona tak, żeby nie usuwać folderów `backups`, `downloads`, `logs` i `secrets`.

## Jak sprawdzić, czy backup się udał

Po udanym backupie RUT pokazuje komunikat z:

- folderem backupu,
- ścieżką do `.g77`,
- SHA256.

W logu pojawi się też informacja `Backup radia zapisany`. Plik `.g77` powinien mieć około 128 KB.
