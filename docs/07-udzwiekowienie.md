# Udźwiękowienie i pakiety VPR

RUT potrafi wgrywać pakiety głosowe OpenGD77 `.vpr` do radia w trybie normalnym.

## Kiedy używać tej funkcji

Użyj przycisku `Udźwiękowienie`, gdy chcesz wgrać albo zmienić pakiet głosowy OpenGD77.

Radio musi być:

- włączone normalnie,
- podłączone przez USB,
- widoczne jako port COM,
- nie może być w DFU.

## Źródła pakietów

RUT może użyć:

- lokalnego pliku `.vpr`,
- katalogu pakietów głosowych OpenGD77 z internetu,
- lokalnych plików roboczych, jeśli były wcześniej tworzone.

Dla pakietów UV380-like RUT preferuje pliki zgodne z rodziną UV380/UV390/RT3S.

## Wybór portu COM

Na zakładce `Firmware i głos` jest pole `Port COM OpenGD77`.

- `Automatycznie` - zalecane ustawienie domyślne. RUT sprawdza kolejno wykryte porty COM i wybiera ten, który odpowie jak radio OpenGD77.
- `COMx` - wybierz port z listy albo wpisz go ręcznie, na przykład `COM5`, tylko gdy wiesz, który port należy do radia albo automatyka nie znajduje radia.
- `Odśwież porty COM` - odświeża listę po podłączeniu albo przepięciu radia.

Ten wybór dotyczy trybu normalnego OpenGD77: udźwiękowienia, zapisu kanałów i backupu codepluga. Nie dotyczy DFU, bo firmware wgrywa się innym mechanizmem USB.

Od wersji `2026.05.19.3` RUT przy wgrywaniu promptów używa ścieżki OpenGD77 Direct: najpierw odczytuje `RadioInfo`, a dla RT3S/UV380/UV390 zapisuje prompt pod adresem `0xAF400` tak jak OpenGD77 CPS.

Jeżeli auto wykryje kilka portów, błędne porty typu Bluetooth albo Intel AMT są traktowane jako mniej prawdopodobne. Jeśli pierwszy port nie odpowie, RUT próbuje następne porty zamiast kończyć operację od razu.

## Weryfikacja pliku

Przed wgraniem RUT sprawdza, czy plik wygląda jak poprawny pakiet głosowy. Jeśli plik jest uszkodzony albo niezgodny, operacja zostanie przerwana.

Przed właściwym zapisem RUT próbuje też zrobić automatyczny backup aktualnego codepluga OpenGD77. Jeśli backup się nie uda, program pokaże ostrzeżenie i pozwoli przerwać operację przed zapisem promptu.

## Co zrobić, gdy radio przestanie mówić

1. Nie panikuj i nie flashuj od razu firmware, jeśli problem dotyczy tylko głosu.
2. Włącz radio normalnie.
3. Podłącz USB.
4. W RUT kliknij `Udźwiękowienie`.
5. Wybierz znany poprawny plik `.vpr`.
6. Poczekaj na komunikat powodzenia.
7. Odłącz i uruchom radio ponownie.

Jeśli radio nie jest widoczne w trybie normalnym, sprawdź port COM i sterowniki.

## Typowe błędy

- `Nie znaleziono portu COM` - radio nie jest w trybie normalnym albo sterownik COM nie działa. Sprawdź pole `Port COM OpenGD77`, odśwież listę portów albo wpisz port ręcznie, na przykład `COM5`.
- `Port COM jest zajęty` - zamknij OpenGD77 CPS i inne programy radiowe.
- `Brak odpowiedzi radia` - odłącz USB, podłącz ponownie, uruchom radio normalnie i spróbuj jeszcze raz.
- `Plik pakietu mowy jest nieprawidłowy` - wybierz inny `.vpr`.

## Gdzie są pobrane pakiety

RUT używa folderu:

`downloads\voice_prompts`

Pakiety oficjalne trafiają zwykle do:

`downloads\voice_prompts\official`
