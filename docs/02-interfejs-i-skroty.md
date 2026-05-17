# Interfejs i skróty

RUT używa natywnych kontrolek Windows Forms. Dzięki temu program jest czytelny dla NVDA i innych czytników ekranu.

## Główne kontrolki

- `Tylko sprawdź wersję` - dla profili obsługiwanych przez backend, sprawdza wersję bez flashowania.
- `Po braku DFU spróbuj automatycznej instalacji sterownika WinUSB` - pomaga przy problemach ze sterownikiem DFU.
- `Model radia` - wybiera profil i zmienia dostępne funkcje.
- `Timeout DFU` - czas oczekiwania na radio w trybie DFU.
- `DMR ID` - numer używany w importowanych kanałach DMR.
- `Język interfejsu` - tryb automatyczny albo ręczny wybór języka.
- `Log` - najważniejsze miejsce diagnostyczne. Jeśli coś nie działa, najpierw przeczytaj ostatnie linie logu.

## Przyciski

- `Sprawdź wersję` - sprawdza dostępność aktualizacji firmware tam, gdzie dany profil to obsługuje.
- `Start aktualizacji` - uruchamia główną akcję aktualizacji dla wybranego profilu.
- `Aktualizuj program` - aktualizuje sam RUT z manifestu GitHub.
- `Kanały z pliku` - importuje kanały z lokalnego pliku.
- `Przemienniki z internetu` - pobiera listę przemienników, między innymi SP-DMR.
- `Kanały + wgraj` - dopisuje kanały do aktualnego codepluga i zapisuje je do radia OpenGD77.
- `Udźwiękowienie` - wybiera i wgrywa pakiet głosowy `.vpr`.
- `DMR + flash` - scala kodek DMR z firmware OpenGD77 i wgrywa wynik przez DFU.
- `Backup radia` - robi backup codepluga OpenGD77 `.g77` w trybie normalnym przez COM.
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
- `Alt+B` - Backup radia.
- `Alt+R` - fokus na model radia.
- `Alt+L` - fokus na log.
- `Alt+D` - fokus na timeout DFU.
- `F1` - krótka pomoc w programie.
- `Alt+F4` - zamknięcie programu z potwierdzeniem.

## Tryb normalny i DFU

To rozróżnienie jest krytyczne:

- Tryb normalny: radio jest włączone zwyczajnie. Windows widzi port COM. Używaj go do kanałów, udźwiękowienia i backupu codepluga.
- Tryb DFU: ekran radia zwykle jest czarny, radio czeka na firmware. Używaj go do flashowania firmware.

Jeżeli RUT czeka na DFU, a radio jest w trybie normalnym, operacja nie ruszy. Jeżeli RUT szuka portu COM, a radio jest w DFU, też nie ruszy.