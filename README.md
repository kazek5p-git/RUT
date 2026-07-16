# RUT

RUT - Radio Updater and Tools dla OpenGD77, TYT UV390, Retevis RT3S oraz narzędzi pomocniczych do kanałów, DMR, DFU i udźwiękowienia.

## Najpierw przeczytaj

Pełna dokumentacja offline jest w folderze:

`docs\README.md`

Najważniejsze rozdziały:

- `docs\01-szybki-start.md` - instalacja i pierwsze uruchomienie.
- `docs\03-obslugiwane-radia.md` - wybór profilu radia.
- `docs\04-backup-i-bezpieczenstwo.md` - backup codepluga i RT3S.
- `docs\05-opengd77-flash-dmr.md` - DFU, OpenGD77, RT3S i DMR + flash.
- `docs\06-kanaly-dmr.md` - import przemienników i DMR ID.
- `docs\07-udzwiekowienie.md` - pakiety głosowe VPR.
- `docs\08-rozwiazywanie-problemow.md` - typowe błędy i naprawy.
- `docs\09-aktualizacje-i-release.md` - aktualizacja programu i release GitHub.

## Uruchomienie

Najprościej pobierz i uruchom jednoplikowy wariant:

`RUT.exe`

Jeśli używasz paczki ZIP, uruchom:

`start_RUT.vbs`

Możesz też uruchomić bezpośrednio:

`RUT.ps1`

## Najważniejsze funkcje

- profile dla TYT UV390 Plus 10W, Retevis RT3S bez GPS i Retevis RT3S GPS,
- `DMR + flash`, czyli scalanie kodeka DMR z firmware OpenGD77 i flashowanie przez DFU,
- naprawa sterownika WinUSB dla DFU z awaryjnym Zadigiem,
- backup codepluga OpenGD77 przez COM,
- import przemienników DMR, dopisywanie kanałów i obsługa DMR ID,
- walidacja paczek CSV OpenGD77 CPS przed importem,
- wgrywanie pakietów głosowych `.vpr`,
- paczka diagnostyczna ZIP z logami i informacjami o środowisku,
- aktualizator programu z rollbackiem do kopii sprzed aktualizacji.

## Najnowszy release

- EXE: https://github.com/kazek5p-git/RUT/releases/latest/download/RUT.exe
- ZIP: https://github.com/kazek5p-git/RUT/releases/latest/download/RUT.zip
- Manifest: https://github.com/kazek5p-git/RUT/releases/latest/download/latest.json
- Strona release: https://github.com/kazek5p-git/RUT/releases/latest

## Gdy program zamyka się od razu

Uruchom `start_RUT_debug.cmd`. Program zostawi otwarte okno i zapisze pliki tekstowe w `logs`. Najpierw sprawdź `logs\RUT_last_start.txt`, bo wskazuje konkretne pliki do wysłania.

## Sprawdzenie brakujących składników

Uruchom `start_RUT_diagnose.cmd`. Ten plik nie uruchamia GUI, tylko sprawdza składniki i zapisuje wynik do `logs\RUT_components_*.txt`.

W samym programie można też kliknąć `Paczka diagnostyczna`. RUT utworzy ZIP w `diagnostics\packages`, wygodny do wysłania komuś do analizy.
