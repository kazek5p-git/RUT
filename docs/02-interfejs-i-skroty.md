# Interfejs i skróty

RUT używa natywnych kontrolek Windows Forms. Dzięki temu program jest czytelny dla NVDA i innych czytników ekranu.

## Zakładki

Główne okno jest podzielone na pięć zakładek:

- `Radio` - profil radia, timeout DFU, język, DMR ID, sprawdzanie wersji, start aktualizacji i backup radia.
- `Kanały` - import kanałów z pliku, import przemienników z internetu i zapis kanałów do radia.
- `Firmware i głos` - wybór portu COM OpenGD77, wgrywanie pakietu głosowego oraz funkcja `DMR + flash`.
- `Status i log` - bieżący status, ostatni komunikat i pełny log pracy.
- `Program` - aktualizacja RUT, paczka diagnostyczna, cofanie aktualizacji, zamknięcie programu i skróty.

Po uruchomieniu fokus trafia na pasek zakładek. RUT używa własnego dostępnego kontrolera zakładek, żeby NVDA widział tylko 5 zakładek i czytał nazwę z numerem, na przykład `Kanały. Zakładka 2 z 5`.

## Główne kontrolki

- `Tylko sprawdź wersję` - dla profili obsługiwanych przez backend, sprawdza wersję bez flashowania.
- `Po braku DFU spróbuj automatycznej instalacji sterownika WinUSB` - pomaga przy problemach ze sterownikiem DFU.
- `Model radia` - wybiera profil i zmienia dostępne funkcje.
- `Timeout DFU` - czas oczekiwania na radio w trybie DFU.
- `DMR ID` - numer używany w importowanych kanałach DMR.
- `Język interfejsu` - tryb automatyczny albo ręczny wybór języka.
- `Port COM OpenGD77` - port radia w trybie normalnym. Domyślnie zostaw `Automatycznie`: RUT sprawdzi wykryte porty i wybierze taki, który odpowie jak OpenGD77. Ręczny wybór lub wpisanie `COM5` wymusza konkretny port dla udźwiękowienia, kanałów i backupu OpenGD77.
- `Log` - najważniejsze miejsce diagnostyczne. Jeśli coś nie działa, najpierw przeczytaj ostatnie linie logu.
- `Sprawdź paczkę CSV` - sprawdza folder CSV przed importem do OpenGD77 CPS i wykrywa typowe błędy separatorów, brakujących kolumn i pustych wartości.

## Przyciski

- `Sprawdź wersję` - sprawdza dostępność aktualizacji firmware tam, gdzie dany profil to obsługuje.
- `Start aktualizacji` - uruchamia główną akcję aktualizacji dla wybranego profilu.
- `Aktualizuj program` - aktualizuje sam RUT z manifestu GitHub.
- `Kanały z pliku` - importuje kanały z lokalnego pliku.
- `Przemienniki z internetu` - pobiera listę przemienników, między innymi SP-DMR.
- `Kanały + wgraj` - dopisuje kanały do aktualnego codepluga i zapisuje je do radia OpenGD77.
- `Odśwież porty COM` - ponownie skanuje porty COM widoczne w Windows.
- `Udźwiękowienie` - wybiera i wgrywa pakiet głosowy `.vpr`.
- `DMR + flash` - scala kodek DMR z firmware OpenGD77 i wgrywa wynik przez DFU.
- `Napraw sterownik DFU` - ręcznie uruchamia kreator naprawy WinUSB dla radia w DFU, bez czekania na błąd flashowania.
- `Backup radia` - robi backup codepluga OpenGD77 `.g77` w trybie normalnym przez COM.
- `Cofnij aktualizację` - przywraca ostatnią kopię programu utworzoną przed aktualizacją RUT.
- `Paczka diagnostyczna` - tworzy ZIP z logami, konfiguracją bez sekretów, listą portów COM i listą ważnych plików programu.
- `Zamknij` - zamyka program. W czasie operacji zamknięcie jest blokowane.

## Skróty klawiaturowe

- `Alt+S` - Sprawdź wersję.
- `Alt+T` - Start aktualizacji.
- `Alt+A` - Aktualizuj program.
- `Alt+K` - Kanały z pliku.
- `Alt+U` - Przemienniki z internetu.
- `Alt+W` - Kanały + wgraj.
- `Alt+V` - Udźwiękowienie.
- `Alt+M` - DMR + flash.
- `Alt+J` - Napraw sterownik DFU.
- `Alt+B` - Backup radia.
- `Alt+Y` - Sprawdź paczkę CSV.
- `Alt+O` - Cofnij aktualizację programu.
- `Alt+G` - Paczka diagnostyczna.
- `Alt+R` - przejdź na zakładkę `Radio` i ustaw fokus na model radia.
- `Alt+P` - przejdź na zakładkę `Firmware i głos` i ustaw fokus na wybór portu COM OpenGD77.
- `Alt+L` - przejdź na zakładkę `Status i log` i ustaw fokus na log.
- `Alt+D` - przejdź na zakładkę `Radio` i ustaw fokus na timeout DFU.
- `F1` - krótka pomoc w programie.
- `Alt+F4` - zamknięcie programu z potwierdzeniem.

## Tryb normalny i DFU

To rozróżnienie jest krytyczne:

- Tryb normalny: radio jest włączone zwyczajnie. Windows widzi port COM. Używaj go do kanałów, udźwiękowienia i backupu codepluga.
- Tryb DFU: ekran radia zwykle jest czarny, radio czeka na firmware. Używaj go do flashowania firmware.

Jeżeli RUT czeka na DFU, a radio jest w trybie normalnym, operacja nie ruszy. Jeżeli RUT szuka portu COM, a radio jest w DFU, też nie ruszy.
