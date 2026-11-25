# TEMPO

Lekka aplikacja webowa (PWA) w czystym HTML, CSS i JavaScript do mierzenia tempa pracy powtarzalnej z ustawianym progiem docelowym i podglądem bilansu czasu na żywo. Zaprojektowana z myślą o obsłudze jedną ręką na telefonie, działaniu w trybie offline oraz odporności na blokowanie ekranu.

**Podgląd (GitHub Pages):** `https://damianhaq.github.io/tempo/`

## Funkcje

- **Zsynchronizowany próg docelowy:** ustawianie celu jako czasu na jedną pozycję (np. `06:00`) albo liczby pozycji na godzinę (np. `10,0/h`) — oba parametry przeliczają się automatycznie.
- **Bilans na żywo (+/-):** bieżąca informacja o zapasie lub stracie czasu względem zadanego progu oraz pasek postępu dla aktualnej pozycji.
- **Tryb Slow Flow:** spokojny tryb pracy bez progu docelowego, bez oceniania kolorami (zielony/czerwony) i z licznikiem `MM:SS` bez setnych sekundy — z pełnym zapisem wszystkich statystyk i historii.
- **Tryb etapowy (Etapy):** podział pojedynczego cyklu na 2–8 konfigurowalnych etapów z jednoczesnym podglądem czasu bieżącego etapu oraz całego cyklu, wykresem warstwowym SVG, analizą wąskich gardeł, rozrzutu i wyliczeniem „idealnego cyklu”.
- **Przycisk pod kciuk z zabezpieczeniem:** duży obszar kliknięcia, krótka wibracja i opcjonalna blokada 1,5 s chroniąca przed przypadkowym podwójnym tapnięciem.
- **Szybka korekta pomiarów:** usuwanie pojedynczych błędnych wpisów z listy oraz cofanie ostatniej pozycji z przywróceniem jej czasu do bieżącego okrążenia.
- **Statystyki i wykres:** średnia, mediana, tempo na godzinę, najkrótszy i najdłuższy czas oraz podgląd przebiegu sesji na wykresie SVG.
- **Odporność na minimalizację i blokadę ekranu:** czas wyliczany jest na podstawie znaczników zegara systemowego (`Date.now()`), dzięki czemu odliczanie nie gubi sekund w tle ani po wygaszeniu ekranu.
- **Zapis w przeglądarce i eksport:** pełna trwałość aktywnej sesji, ustawień oraz historii w `localStorage`, kopiowanie listy w formacie tekstowym oraz eksport do pliku CSV.
- **Tryb offline (PWA):** instalacja na ekranie głównym telefonu i uruchamianie bez dostępu do sieci dzięki Service Workerowi.

## Struktura projektu

```text
.
├── index.html             # Główny plik aplikacji (HTML, CSS i JS w jednym pliku)
├── manifest.json          # Konfiguracja PWA (ikony, kolory, tryb pełnoekranowy)
├── sw.js                  # Service Worker obsługujący pamięć podręczną i tryb offline
├── icon.svg               # Minimalistyczna ikona wektorowa aplikacji
├── icon-192.png           # Ikona PWA (192x192)
├── icon-512.png           # Ikona PWA (512x512)
├── icon-maskable-512.png  # Ikona maskowalna PWA (512x512)
├── apple-touch-icon.png   # Ikona dla ekranu głównego iOS (180x180)
└── README.md              # Dokumentacja projektu
```
