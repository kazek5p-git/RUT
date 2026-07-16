# RUT - dokumentacja

RUT to przenośny program dla Windows do obsługi radiotelefonów używanych z OpenGD77 oraz kilku narzędzi pomocniczych do kanałów, udźwiękowienia i aktualizacji.

Ten folder jest dokumentacją offline. Można go czytać w Notatniku, Visual Studio Code, przeglądarce GitHub albo dowolnym edytorze tekstu. Pliki są napisane tak, żeby dobrze działały z NVDA: krótkie rozdziały, zwykłe nagłówki i bez skomplikowanych tabel.

## Od czego zacząć

1. Przeczytaj [01-szybki-start.md](01-szybki-start.md), jeśli chcesz tylko uruchomić program.
2. Przeczytaj [03-obslugiwane-radia.md](03-obslugiwane-radia.md), jeśli nie wiesz który profil radia wybrać.
3. Przed pierwszym flashowaniem RT3S przeczytaj [04-backup-i-bezpieczenstwo.md](04-backup-i-bezpieczenstwo.md).
4. Jeśli chcesz wgrywać OpenGD77 lub DMR, przejdź do [05-opengd77-flash-dmr.md](05-opengd77-flash-dmr.md).
5. Jeśli chcesz dodać przemienniki DMR i własne DMR ID, przejdź do [06-kanaly-dmr.md](06-kanaly-dmr.md).
6. Jeśli chcesz wgrać pakiet głosowy, przejdź do [07-udzwiekowienie.md](07-udzwiekowienie.md).
7. Jeśli coś nie działa, sprawdź [08-rozwiazywanie-problemow.md](08-rozwiazywanie-problemow.md).
8. Jeśli chcesz wykonać konkretny typowy przebieg krok po kroku, przejdź do [11-scenariusze.md](11-scenariusze.md).

## Spis dokumentów

- [01-szybki-start.md](01-szybki-start.md) - instalacja, uruchomienie i pierwsze kroki.
- [02-interfejs-i-skroty.md](02-interfejs-i-skroty.md) - opis kontrolek, skrótów klawiaturowych i dostępności.
- [03-obslugiwane-radia.md](03-obslugiwane-radia.md) - profile radia i zakres obsługi.
- [04-backup-i-bezpieczenstwo.md](04-backup-i-bezpieczenstwo.md) - backup codepluga, RT3S, kalibracja i zasady bezpieczeństwa.
- [05-opengd77-flash-dmr.md](05-opengd77-flash-dmr.md) - firmware OpenGD77, DFU, DMR codec i RT3S.
- [06-kanaly-dmr.md](06-kanaly-dmr.md) - import przemienników, DMR ID, dopisywanie kanałów i duplikaty.
- [07-udzwiekowienie.md](07-udzwiekowienie.md) - pakiety głosowe VPR i tryb normalny radia.
- [08-rozwiazywanie-problemow.md](08-rozwiazywanie-problemow.md) - DFU, COM, sterowniki, OpenGD77 CPS i typowe błędy.
- [09-aktualizacje-i-release.md](09-aktualizacje-i-release.md) - autoaktualizacja RUT, GitHub release i manifest.
- [10-struktura-plikow.md](10-struktura-plikow.md) - gdzie RUT zapisuje pliki, logi, backupy i paczki.
- [11-scenariusze.md](11-scenariusze.md) - gotowe przebiegi dla RT3S, DMR + flash, promptów, CPS i diagnostyki.

## Najważniejsze zasady

- Firmware wgrywa się w trybie DFU.
- Kanały, udźwiękowienie i backup codepluga OpenGD77 działają w trybie normalnym przez port COM.
- Przed pierwszym flashowaniem RT3S z fabrycznego firmware trzeba zachować fabryczną kalibrację i oryginalny codeplug oficjalnym CPS producenta.
- RUT nie powinien podmieniać Twoich kanałów bez potrzeby. Import DMR jest robiony jako dopisanie, a duplikaty są usuwane tylko tam, gdzie są faktycznie powtórzone.
- DMR ID wpisane w polu programu jest używane przy budowaniu kanałów OpenGD77.
- Przed zapisem kanałów i promptów RUT próbuje zrobić automatyczny backup codepluga OpenGD77. Jeśli backup nie wyjdzie, program pyta, czy kontynuować.
- W zakładce `Program` jest paczka diagnostyczna i cofanie programu do kopii sprzed aktualizacji.
- W zakładce `Kanały` jest walidacja paczek CSV dla OpenGD77 CPS, żeby szybciej wykryć błędy typu `line 2 is not valid`.

## Linki

- Najnowszy release RUT: https://github.com/kazek5p-git/RUT/releases/latest
- Stały link do EXE: https://github.com/kazek5p-git/RUT/releases/latest/download/RUT.exe
- Stały link do ZIP: https://github.com/kazek5p-git/RUT/releases/latest/download/RUT.zip
- Manifest aktualizacji: https://github.com/kazek5p-git/RUT/releases/latest/download/latest.json
- OpenGD77: https://www.opengd77.com/
