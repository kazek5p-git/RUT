# Obsługiwane radia

RUT ma profile radia. Profil decyduje o tym, które funkcje są aktywne i jaki firmware lub narzędzie jest używane.

## TYT UV390 Plus 10W (OpenGD77)

Zakres obsługi:

- sprawdzanie wersji przez backend RUT,
- aktualizacja firmware przez DFU,
- import i zapis kanałów OpenGD77,
- udźwiękowienie `.vpr`,
- backup codepluga OpenGD77 `.g77`,
- DMR + flash z plikiem kodeka.

Używany plik firmware w paczce:

- `dist\firmware_extracted\OpenMDUV380_10W_PLUS.bin`

## Retevis RT3S bez GPS (OpenGD77)

Zakres obsługi:

- DMR + flash przez helper OpenGD77 i DFU,
- import i zapis kanałów po przejściu na OpenGD77,
- udźwiękowienie po przejściu na OpenGD77,
- backup codepluga OpenGD77 `.g77` po przejściu na OpenGD77,
- ostrzeżenie o backupie kalibracji przed flashowaniem.

Używany plik firmware w paczce:

- `dist\firmware_extracted\OpenMDUV380.bin`

## Retevis RT3S GPS (OpenGD77)

Zakres obsługi jest taki sam jak dla RT3S bez GPS. Profil jest osobny, żeby użytkownik mógł świadomie wybrać swój wariant radia, ale obecnie oba profile RT3S używają pliku `OpenMDUV380.bin` z rodziny MDUV380.

## Quansheng UV-K5 / UV-K6

Zakres obsługi:

- sprawdzanie release firmware z GitHub,
- flashowanie firmware Quansheng przez narzędzia pobierane z GitHub.

Ten profil nie jest profilem OpenGD77. Funkcje kanałów OpenGD77, udźwiękowienia OpenGD77 i DMR + flash nie dotyczą Quanshenga.

## Baofeng i PMR

Te profile są traktowane jako pomocnicze dla list kanałów i organizacji pracy. Automatyczne flashowanie nie jest w nich gotowe.

## Co oznacza komunikat, że funkcja jest tylko dla UV390/OpenGD77

W wielu miejscach historyczne komunikaty mówią o UV390, bo RUT zaczynał jako narzędzie dla UV390. W praktyce funkcje OpenGD77 dotyczą profili z `Kind = opengd77`, czyli UV390 i RT3S po przejściu na OpenGD77, o ile radio jest widoczne w wymaganym trybie.