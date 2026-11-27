# TEMPO

Lekka aplikacja webowa (PWA) w czystym HTML, CSS i JavaScript do mierzenia tempa pracy powtarzalnej z ustawianym progiem docelowym i podglądem bilansu czasu na żywo. Zaprojektowana z myślą o obsłudze jedną ręką na telefonie, działaniu w trybie offline oraz odporności na blokowanie ekranu.

**Podgląd (GitHub Pages):** `https://damianhaq.github.io/tempo/`  
**Aktualna wersja:** `1.3`

## Funkcje

- **Trzy tryby pracy (`Cel | Slow Flow | Etapy`):** szybkie przełączanie między pracą z progiem docelowym, spokojnym trybem bez presji i trybem podziału cyklu na etapy.
- **Zsynchronizowany próg docelowy:** ustawianie celu jako czasu na jedną pozycję (np. `06:00`) albo liczby pozycji na godzinę (np. `10,0/h`) — oba parametry przeliczają się automatycznie.
- **Bilans na żywo (+/-):** bieżąca informacja o zapasie lub stracie czasu względem zadanego progu oraz pasek postępu dla aktualnej pozycji.
- **Tryb Slow Flow:** spokojny tryb pracy bez progu docelowego, bez oceniania kolorami (zielony/czerwony), z licznikiem `MM:SS` bez setnych sekundy oraz uproszczoną siatką statystyk (`Pozycje`, `Czas łączny`) — z pełnym zapisem wszystkich danych i statystyk w historii oraz eksporcie.
- **Tryb etapowy (Etapy):** podział pojedynczego cyklu na 2–8 konfigurowalnych etapów z banerem aktualnego etapu i ścieżką postępu, jednoczesnym podglądem czasu bieżącego etapu oraz całego cyklu, wykresem warstwowym SVG, analizą wąskich gardeł, rozrzutu i wyliczeniem „idealnego cyklu”.
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

## Historia zmian

### v1.3 (27.11.2026)
- **Widok trybu `Etapy` (Wariant A):** neutralny ciemny przycisk z górnym paskiem koloru etapu (bez kolidującej kolorowej ramki), wyraźna nazwa aktualnego etapu, usunięcie zbędnej dolnej linijki akcji podczas pracy oraz baner aktualnego etapu ze stabilną ścieżką kroków (bez zawijania linii po ukończeniu etapu).
- **Uproszczony tryb `Slow Flow`:** ukrycie kafelków `Średnia`, `Mediana`, `Tempo` i `Najlepszy czas` w widoku bieżącej sesji (przy zachowaniu pełnych statystyk w Historii).
- **Poprawki działania i stabilności:** zachowanie legendy i filtra wykresu po zmianie rozmiaru okna (`resize`), blokada przestawiania i usuwania etapów w trakcie aktywnego cyklu, bezpieczne cofanie na granicy cyklu (`Cofnij etap`), poprawne rysowanie etapu `0 ms` w filtrze wykresu, synchronizacja pól przy zamknięciu ustawień klawiszem `Escape` oraz izolacja widoku `Slow Flow` w sesjach mieszanych.

### v1.2 (25.11.2026)
- **Tryb etapowy (`Etapy`):** podział cyklu na 2–8 nazwanych etapów, przełącznik 3 trybów (`Cel | Slow Flow | Etapy`), dwa czasy na głównym przycisku (czas etapu + czas bieżącego cyklu) oraz cofanie po pojedynczych etapach.
- **Rozszerzona analiza:** pasek trendów (`Ost. 5 cykli`, `W progu`, `Idealny cykl` / `Bez najgorszego`), wykres warstwowy SVG z filtrowaniem pojedynczego etapu, tabela `Analiza etapów` (średnia, mediana, min–max, udział %, trend) oraz rozwijane wiersze na liście pomiarów i kolumny etapów w CSV.

### v1.1 (25.11.2026)
- **Tryb `Slow Flow`:** praca bez progu docelowego i bez czerwono-zielonego oceniania, z licznikiem `MM:SS` bez setnych sekundy.
- **Poprawki PWA, wykresu i walidacji:** wygenerowane ikony PNG (`192x192`, `512x512`, `maskable`, `apple-touch-icon`), poprawki Service Workera, responsywny `viewBox` wykresu SVG, walidacja `localStorage`, obsługa przecinka w polu wydajności oraz poprawiony eksport CSV i kopiowanie do schowka.

### v1.0 (22.11.2026)
- Pierwsze wydanie aplikacji **TEMPO**: stoper oparty o `Date.now()`, zsynchronizowany próg docelowy (`MM:SS` / `szt./h`), bilans na żywo `+/-`, blokada podwójnego kliknięcia, podstawowe statystyki, wykres SVG, historia w `localStorage`, eksport CSV oraz wsparcie offline PWA.
