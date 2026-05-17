# Historia zmian dokumentacji

## 2026.05.17.7

- Naprawiono b??d startu: funkcje pomocnicze profili OpenGD77 by?y omy?kowo zagnie?d?one w `Refresh-RadioProfilesCombo` przed blokiem `param`.
- Objaw b??du: program zamyka? si? natychmiast, a log zawiera? `The term 'param' is not recognized` przy `Refresh-RadioProfilesCombo`.

## 2026.05.17.6

- Dodano `start_RUT_diagnose.cmd` do sprawdzania brakuj?cych sk?adnik?w.
- Dodano `tools\diagnostics\Test-RUT-Components.ps1`.
- Diagnostyka zapisuje wynik do `logs\RUT_components_*.txt` i rozr??nia `OK`, `WARN` oraz `FAIL`.

## 2026.05.17.5

- Dodano diagnostyczne logi startu jako zwyk?e pliki `.txt`.
- Launcher `start_RUT.vbs` tworzy `logs\RUT_last_start.txt`, `logs\RUT_launcher_*.txt` i `logs\RUT_powershell_*.txt`.
- Dodano `start_RUT_debug.cmd`, kt?ry zostawia okno konsoli i zapisuje log tekstowy, gdy program zamyka si? od razu.
- G??wny log RUT ma teraz rozszerzenie `.txt`, a `logs\RUT_last_log.txt` wskazuje ostatni g??wny log.

## 2026.05.17.4

- Dodano pełną dokumentację offline w folderze `docs`.
- Dodano rozdziały o szybkim starcie, interfejsie, obsługiwanych radiach, backupie, RT3S, DMR, kanałach, udźwiękowieniu, problemach i release.
- Dokumentacja jest pisana pod czytanie NVDA: zwykłe nagłówki, krótkie listy i bez tabel wymagających nawigacji komórkami.

## 2026.05.17.3

- Dodano opcję `Backup radia`.
- Dodano ostrzeżenie backupu przed flashowaniem RT3S.

## 2026.05.17.2

- Dodano profile Retevis RT3S bez GPS i Retevis RT3S GPS.
- Dodano firmware `OpenMDUV380.bin` do paczki.