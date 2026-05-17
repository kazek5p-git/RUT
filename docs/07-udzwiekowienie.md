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

## Weryfikacja pliku

Przed wgraniem RUT sprawdza, czy plik wygląda jak poprawny pakiet głosowy. Jeśli plik jest uszkodzony albo niezgodny, operacja zostanie przerwana.

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

- `Nie znaleziono portu COM` - radio nie jest w trybie normalnym albo sterownik COM nie działa.
- `Port COM jest zajęty` - zamknij OpenGD77 CPS i inne programy radiowe.
- `Brak odpowiedzi radia` - odłącz USB, podłącz ponownie, uruchom radio normalnie i spróbuj jeszcze raz.
- `Plik pakietu mowy jest nieprawidłowy` - wybierz inny `.vpr`.

## Gdzie są pobrane pakiety

RUT używa folderu:

`downloads\voice_prompts`

Pakiety oficjalne trafiają zwykle do:

`downloads\voice_prompts\official`