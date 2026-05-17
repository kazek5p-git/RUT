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
- brak Pythona lub `pyusb` w ścieżce DMR + flash,
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

`logs\RUT_YYYYMMDD_HHMMSS.log`

W razie problemu najważniejsze są:

- ostatnie linie logu w oknie programu,
- najnowszy plik w folderze `logs`,
- komunikat błędu z okna dialogowego.

## Co wysłać komuś do diagnozy

Najlepiej wysłać:

- model radia,
- czy radio było w DFU czy w trybie normalnym,
- ostatnie 20-40 linii logu,
- nazwę operacji, którą uruchomiono,
- informację, czy Windows widzi DFU albo COM,
- wersję RUT z manifestu lub release.