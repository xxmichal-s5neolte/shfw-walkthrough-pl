# Szybki przewodnik konfiguracji SHFW

SHFW to niestandardowy firmware (custom firmware) dostępny do wgrania za pomocą aplikacji Scooterhacking Utility. Konfiguracja może być trudna dla nowych użytkowników. Ten przewodnik ma na celu zapewnienie szybkiego i łatwego sposobu na zastosowanie najważniejszych podstaw. Zrozumienie tego wszystkiego może być przytłaczające, ale przyjdzie jako efekt uboczny twoich własnych testów i przemyśleń — tego nie jesteśmy w stanie zrobić za ciebie.

Dołącz do dyskusji na [Telegramie](https://t.me/scooterhackingchat) i [Discordzie](https://scooterhack.in/discord).

### Instalacja

Aby zainstalować SHFW, wykonaj następujące kroki:

1. Pobierz naszą oficjalną aplikację [Utility](https://utility-beta.cfw.sh/), alternatywnie, aby uzyskać wsparcie dla szerokiej gamy urządzeń, w tym iOS, sprawdź [Lunę](https://luna.cfw.sh/).

2. Obsługiwane modele hulajnóg:

      - **Ninebot G30, G30L**: Możesz wgrać ten firmware, jeśli wersja DRV wynosi 1.7.3 lub niżej. Jeśli twój DRV to 1.7.3, musisz wybrać „Attempt Downgrade" przed wgraniem SHFW. Dla wersji DRV powyżej 1.7.3 potrzebny jest ST-Link. Więcej informacji [tutaj](https://joeybabcock.me/wiki/STLink_Ninebot_Max_ESC).

      - **Ninebot G2, F2, F2 Plus, F2 Pro**: Każdy model regionalny jest kompatybilny, wymaga odblokowania przez ST-Link.

      - **Ninebot ESx**: Każda wersja jest obsługiwana.

      - **Seria Exx**: [Nie E2, E2 Plus, E2 Pro. Tylko starsze E22, E45 itp.] Możesz wgrać SHFW, jeśli wersja DRV jest poniżej 2.7.0. W przeciwnym razie musisz użyć ST-Linka.

      - **Ninebot seria F**: [Starsze SHFW 0.3.6] Możesz wgrać ten firmware, jeśli wersja DRV jest poniżej 5.7.0. W przeciwnym razie musisz użyć ST-Linka. W internecie dostępne są przewodniki tego procesu. Aplikacja będzie prosić o aktualizacje, nawet jeśli ich nie ma — bądź tego świadomy. Wymaga wgrania za pomocą aktualnej wersji Utility, a następnie konfiguracji za pomocą [Utility 2.5](https://utility.cfw.sh/distrib/ScooterHackingUtility-2.5.apk). Nie włączaj wzmocnienia hamulca.

      - **Ninebot seria D**: [Obecnie nie działa] Istnieje eksperymentalne wsparcie dla serii D przy użyciu firmware serii F. Nie wiadomo, od jakiej wersji DRV wymagany jest ST-Link. Instrukcje powinny być identyczne jak dla serii F.

   - **Hulajnogi Xiaomi**: Jeśli wersja BLE wynosi 1.5.5 lub wyżej, musisz dokonać downgrade'u dashboardu przez ST-Link. [Przewodnik po downgrade ST-Link](https://lekrsu.github.io/shfw-walkthrough/stlinking/xiaomi-ble). Spróbuj downgrade'u DRV przez naszą aplikację (ScooterHacking Utility), jeśli wgranie SHFW nie powiedzie się z obsługiwaną wersją BLE.

    [Reflasher](https://www.scooterhacking.org/forum/viewtopic.php?t=676), [Webflasher](https://flash.bastelpichi.de/) i [ScooterFlasher](https://github.com/scooterteam/scooterflasher) to programy używane do ST-Linkowania — wybierz dowolny, jeśli jest potrzebny.

    | Model | Kompatybilne BLE | Kompatybilne DRV |
    |:--|:--|:--|
    |  | *ST-Link jeśli niekompatybilne* | *ST-Link jeśli niekompatybilne* |
    | Ninebot G30 | Wszystkie | [Do 1.7.3](https://joeybabcock.me/wiki/STLink_Ninebot_Max_ESC) |
    | Ninebot G2 | Wszystkie | ST-Link |
    | Ninebot F2, F2 Plus, F2 Pro | Wszystkie | ST-Link |
    | Xiaomi Essential, 1s, Pro 2, 3 | Poniżej 1.5.5 | Wszystkie |
    | Ninebot EsX | Wszystkie | Wszystkie |
    | Seria Ex | Wszystkie | Poniżej 2.7.0 |
    | Ninebot E2, E2D, E2 Pro | N/D | N/D |
    | Ninebot seria F | Wszystkie | Poniżej 5.7.0 |
    | Ninebot seria D | Wszystkie | Eksperymentalne (firmware serii F, nieznane) |

3. Procedura flashowania:

   - Otwórz aplikację Utility, połącz się z hulajnogą.
   - Naciśnij „Install/update SHFW" i wybierz wersję o najwyższym numerze, jeśli jest kilka do wyboru. Następnie naciśnij flash. Jeśli się nie uda, a powyższa tabela wskazuje obsługiwaną wersję, spróbuj opcji „attempt drv downgrade" przed SHFW.
      - Jeśli masz nowszy silnik Gen 3 G30, wybierz opcję nowego silnika w zakładce konfiguracji silnika. Jest to automatyczne z oryginalnym numerem seryjnym. Jeśli nie wiesz, który masz, porównaj numer seryjny silnika z poniższą tabelą:

      | Numer seryjny silnika (SN) | Generacja | Modele |
      |--------------------------|----------------------|--------------------------------------|
      | Zaczyna się od 6 | Pierwsza generacja | Większość starszych modeli |
      | Zaczyna się od 9 | Druga generacja | G30Ps, niektóre modele G30Lx |
      | Zawiera PCAH | Trzecia generacja | G30P |
      | Zawiera PAAH | Trzecia generacja | G30E |
      | Zawiera PADH/PADJ | Trzecia generacja | G30D |


### Użytkowanie

Pamiętaj, że poniższe informacje są przeznaczone do praktycznego zastosowania, ale należy z nich korzystać ostrożnie. Pamiętaj, że osłabianie pola magnetycznego (field weakening) z natury nie jest wydajne.

#### Funkcje kalkulatora szczytowego poboru prądu

- **Obliczanie prądu momentu obrotowego**: Użytkownicy mogą wprowadzić swoje ampery momentu obrotowego (Iq), aby dokładnie obliczyć składową momentu obrotowego.
- **Obliczanie osłabiania pola**: Wprowadzając początkowy strumień w A, zmienny strumień w mAh, aktualną maksymalną prędkość w km/h i prędkość startu w km/h, kalkulator wyznacza składową strumienia (Id), uwzględniając efekty osłabiania pola.
- **Szczytowy pobór prądu**: Na podstawie parametrów wejściowych kalkulator oblicza szczytowy pobór prądu (I_total), dostarczając istotnych informacji o maksymalnym zapotrzebowaniu elektrycznym systemu.

Aby dostosować te limity fazowe, sprawdź suwaki Iq i Id w sekcji „Field Weakening".

[**Wypróbuj kalkulator szczytowego poboru prądu**](https://lekrsu.github.io/shfw-walkthrough/logic/index.html) — przyjazne dla użytkownika narzędzie zaprojektowane dla jasności i wydajności w obliczaniu parametrów elektrycznych. Pamiętaj, że jest to wartość szczytowa, nie pokazuje rzeczywistego poboru z baterii, ale pomaga to zwizualizować. Krzywe Sport, Drive i Eco w Utility pokazują docelowy prąd baterii, ale nie jest to ogranicznik — przy niskich prędkościach może być tymczasowo pobierany wyższy prąd.

#### Ninebot G30

Aby osiągnąć maksymalną prędkość dla Ninebot G30, zastosuj następującą konfigurację:

   - Włącz „expert view" w prawym górnym rogu.

1. Ustaw krzywą sport DPC auto na 25A, 0.5 kwadratowa
   - Skonfiguruj pozostałe tryby według uznania — niższy prąd niż sport oznacza mniejsze przyspieszenie.
   - Zostaw limit prędkości wyłączony / 0.
   - Wzmocnienie przyspieszenia (Acceleration boost): 50%.
   - Wzmocnienie hamulca (Brake boost): 0-50%, przetestuj.
   - Nadmodulacja (Overmodulation) włączona dla sport/drive — efektywny wzrost prędkości o 10%.

Możesz ustawić eco i drive na niższe wartości, np. 10A eco, 25A drive. Drive zużyje mniej prądu, ponieważ nie włączymy osłabiania pola.

2. Przejdź do zakładki osłabiania pola (field weakening) i włącz je dla trybu sport:

   ### Normalne użytkowanie:
   - Skonfiguruj następująco:
     - Prędkość: 20 km/h
     - Początkowy (Initial current): 0A
     - Zmienny (Variable current): 1200

   ### Wyższa wydajność, mniejsze osłabianie pola:
   - Skonfiguruj następująco:
     - Prędkość: 20 km/h
     - Początkowy (Initial current): 0A
     - Zmienny (Variable current): 600

4. Domyślny rozmiar opony dla modeli Max to 10", ale ustaw 9.4" na G30, aby prędkość na wyświetlaczu odpowiadała prędkości GPS.

5. W ustawieniach silnika (Motor Settings) wybierz 20 lub 24 kHz.

#### Ninebot G2, F2

Aby osiągnąć maksymalną prędkość dla G2 i F2, zastosuj następującą konfigurację:

   - Włącz „expert view" w prawym górnym rogu.

1. Ustaw krzywą sport DPC auto na 25A, 0.5 kwadratowa
   - Skonfiguruj pozostałe tryby według uznania — niższy prąd niż sport oznacza mniejsze przyspieszenie.
   - Zostaw limit prędkości wyłączony / 0.
   - Wzmocnienie przyspieszenia (Acceleration boost): 100%. Jeśli hulajnoga się wyłącza, zmniejsz ten procent.
   - Brake overshoot na 45A — zmniejsza ryzyko nadprądu przy aktywacji hamulca.

Możesz ustawić eco i drive na niższe wartości, np. 10A eco, 25A drive. Drive zużyje mniej prądu, ponieważ nie włączymy osłabiania pola.

2. Przejdź do zakładki osłabiania pola (field weakening) i włącz je dla trybu sport:

   ### Normalne użytkowanie:
   - Skonfiguruj następująco:
     - Prędkość: 20 km/h
     - Początkowy (Initial current): 0A
     - Zmienny (Variable current): 1200

   ### Wyższa wydajność, mniejsze osłabianie pola:
   - Skonfiguruj następująco:
     - Prędkość: 20 km/h
     - Początkowy (Initial current): 0A
     - Zmienny (Variable current): 600

#### Xiaomi Pro 2

Konfiguracja dla tego modelu zależy od numeru seryjnego baterii i wersji firmware:

Włącz „expert view" w prawym górnym rogu.

### Numer seryjny baterii zaczynający się od `4XFG` *ORAZ* wersja firmware BMS z 3 cyframi (np. 1.4.1) zamiast 4:
   1. Tryb sport, DPC, krzywa auto 30A, pół-kwadratowa (0.5):
      - Wzmocnienie przyspieszenia ustawione na 100%.
      - Wzmocnienie hamulca ustawione na 100%.
      - Nadmodulacja włączona dla sport/drive.

### Numer seryjny baterii zaczynający się od `BFFG` *LUB* wersja firmware BMS z 4 cyframi (np. 1.1.0.2) zamiast 3:
   1. Tryb sport, DPC, krzywa auto 20A, pół-kwadratowa (0.5):
      - Wzmocnienie przyspieszenia ustawione na 80%.
      - Wzmocnienie hamulca ustawione na 100%.
      - Nadmodulacja włączona dla sport/drive.

Możesz ustawić eco i drive na niższe wartości, np. 10A eco, 20A drive. Drive zużyje mniej prądu, ponieważ nie włączymy osłabiania pola.

2. Przejdź do zakładki osłabiania pola i:
   - Włącz osłabianie pola dla trybu sport.
   - Skonfiguruj następująco: 20 km/h, 0A, 1500.

4. W ustawieniach silnika (Motor Settings) wybierz 20 kHz.

#### Xiaomi Mi 3

Dla tego modelu użyj następującej konfiguracji:
Włącz „expert view" w prawym górnym rogu.

1. Tryb sport, DPC, krzywa auto 20A, pół-kwadratowa (0.5):
    - Wzmocnienie przyspieszenia ustawione na 90%. Jeśli pojazd się wyłącza, zmniejsz wartość.
    - Wzmocnienie hamulca ustawione na 100%.
    - Nadmodulacja włączona dla sport/drive.

Możesz ustawić eco i drive na niższe wartości, np. 10A eco, 20A drive. Drive zużyje mniej prądu, ponieważ nie włączymy osłabiania pola.

2. Przejdź do zakładki osłabiania pola i:
   - Włącz osłabianie pola dla trybu sport.
   - Skonfiguruj następująco: 20 km/h, 0A, 1500.

4. W ustawieniach silnika (Motor Settings) wybierz 20 kHz.

#### Xiaomi Essential, Lite, 1S

Dla Xiaomi Essential i 1S użyj następującej konfiguracji:

   - Włącz „expert view" w prawym górnym rogu.

1. Tryb sport, DPC, 18A, w pełni kwadratowa (1.0).
   - Wzmocnienie przyspieszenia ustawione na 50%.
   - Hamulec ustawiony na 30A, płaski (0.0) — jeśli hamulec wydaje się słaby, powoli zwiększaj ustawienie wzmocnienia hamulca.
   - Nadmodulacja włączona dla sport/drive.

Możesz ustawić eco i drive na niższe wartości, np. 10A eco, 18A drive. Drive zużyje mniej prądu, ponieważ nie włączymy osłabiania pola.

2. Przejdź do zakładki osłabiania pola i:

   - Włącz osłabianie pola dla trybu sport.
   - Skonfiguruj następująco: 15 km/h, 0A, 1500.

4. W ustawieniach silnika (Motor Settings) wybierz 20.

#### Ninebot EsX, Ex

Dla Ninebot EsX, Ex użyj następującej konfiguracji:

   - Włącz „expert view" w prawym górnym rogu.

1. Tryb sport, DPC, 18A, w pełni kwadratowa (1.0).
   - Wzmocnienie przyspieszenia: 50%.
   - Hamulec: 55A, płaski (0.0).
   - Nadmodulacja włączona dla sport/drive.

Możesz ustawić eco i drive na niższe wartości, np. 10A eco, 18A drive. Drive zużyje mniej prądu, ponieważ nie włączymy osłabiania pola.

2. Przejdź do zakładki osłabiania pola i:
   - Włącz osłabianie pola dla trybu sport.
   - Skonfiguruj następująco: 15 km/h, 0A, 1500.

4. W ustawieniach silnika (Motor Settings) wybierz 20 kHz.

## Wyjaśnienie sterowania PI i wzmocnienia przyspieszenia

### Sterowanie PI do konwersji czasu napięcia

System sterowania PI przekształca ampery w czas napięcia. Proces ten skaluje czas napięcia od 0 do 31128, gdzie 31128 reprezentuje 100%. Skalowanie dotyczy obu składowych prądu. Jeśli łączny czas przekracza 31128, wartości są odpowiednio zmniejszane.

### Pomiar napięcia i kompensacja

System mierzy jedynie czas napięcia, używając 100% cyklu pracy przy maksymalnej potencjalnej prędkości. Ta metoda pozwala systemowi działać spójnie przy różnych napięciach bez konieczności dostosowywania firmware. Cykl PWM (modulacja szerokości impulsu) jest utrzymywany na wysokim poziomie w sposób ciągły, działając podobnie do silnika prądu stałego.

### Szczegóły implementacji

- **Liczniki 16-bitowe**: System używa liczników 16-bitowych do implementacji PWM. Liczniki zatrzymują się 4 cykle przed końcem częstotliwości.
- **Limit cyklu pracy**: Cykl pracy jest ograniczony do 95%, ponieważ osiągnięcie 100% jest teoretycznie możliwe, ale niepraktyczne.
- **Znaczenie napięcia**: Napięcie nie jest bezpośrednio istotne dla sterowania. Zamiast tego zarządzanie dotyczy czasu trwania fazy. Na przykład:
  - Faza A może być wysoka przez 10 ms
  - Faza B może być wysoka przez 5 ms
  - Faza C może być wysoka przez krótszy czas

Jednak ważne jest, aby wiedzieć, że rzeczywiste czasy faz są znacznie krótsze niż te przykłady.

### Wzmocnienie przyspieszenia (Acceleration Boost)

Funkcja wzmocnienia przyspieszenia pozwala na lepszą reakcję silnika poprzez tymczasowe zwiększenie docelowego prądu podczas przyspieszania. Jest to kontrolowane za pomocą suwaka 0-100%, który reguluje intensywność wzmocnienia.

Po ustawieniu suwaka system żąda wyższego prądu na krótki czas, efektywnie podwajając docelowy prąd, gdy suwak jest ustawiony na 100%. Na przykład ustawienie suwaka na 50% zwiększa żądany prąd do 150% wartości docelowej. To tymczasowe wzmocnienie umożliwia silnikowi osiągnięcie szybszego przyspieszenia bez trwałego podnoszenia limitu prądu.

Jednak ta technika powoduje zwiększone zużycie energii elektrycznej, ponieważ system pobiera dodatkową moc podczas fazy przyspieszania. Energia potrzebna do tego wzmocnienia pochodzi z baterii, co prowadzi do wyższego całkowitego zużycia energii.

### Obliczenia i logika osłabiania pola

#### Czym jest osłabianie pola?

Osłabianie pola (field weakening) to technika powszechnie stosowana w 3-fazowych silnikach elektrycznych, aby osiągnąć wyższe prędkości w pojazdach elektrycznych, takich jak hulajnogi. Pozwala silnikowi na pracę powyżej jego znamionowego napięcia i obrotów, co może skutkować zwiększoną prędkością maksymalną. Jednak wdrożenie osłabiania pola wiąże się z kompromisami, w tym zwiększonym zużyciem baterii, wyższą temperaturą silnika i potencjalnymi dodatkowymi kosztami.

#### Obliczanie strumienia osłabiania pola

Wzór na obliczanie strumienia osłabiania pola jest następujący:

strumień osłabiania pola = początkowy + ("aktualna prędkość" - "prędkość startu osłabiania pola") * (zmienny / 1000)

- `początkowy`: wartość początkowa strumienia osłabiania pola.
- `"aktualna prędkość"`: aktualna prędkość hulajnogi.
- `"prędkość startu osłabiania pola"`: prędkość, przy której powinno się rozpocząć osłabianie pola.
- `zmienny`: parametr wpływający na tempo wzrostu strumienia.

Poniżej wykres prądu strumienia stosowanego przy różnych prędkościach, porównujący 2 konfiguracje:
- 7A prąd początkowy, 24 km/h prędkość startu, 1500 mA/km/h prąd zmienny
- 0A prąd początkowy, 24 km/h prędkość startu, 1500 mA/km/h prąd zmienny

Podsumowując wykres: początkowy dodaje osłabianie pola przy prędkości startu osłabiania, z dodatkowym prądem na km/h zgodnie z ustawionym prądem zmiennym. Prąd początkowy może być użyty do przekroczenia progu potrzebnego do osiągnięcia wyższego prądu osłabiania przez zmienną. Zbyt duże osłabianie pola spowoduje jedynie nagrzewanie i potencjalne uszkodzenia, podczas gdy zbyt małe ograniczy prędkość. Optymalne dla wydajności silnika i baterii jest jednak nieużywanie osłabiania pola w ogóle.

### Niestandardowe baterie i emulacja BMS

Po zainstalowaniu niestandardowej baterii w określonych modelach hulajnóg możesz zauważyć, że wyświetlacz nie pokazuje już procentu naładowania baterii. Dzieje się tak, ponieważ oryginalny system zarządzania baterią (BMS) używa kabla komunikacyjnego do dostarczania tych informacji, między innymi. Jako obejście można zastosować emulację BMS. Ta metoda oblicza poziom naładowania baterii wyłącznie na podstawie napięcia systemu — jest to możliwe dzięki liniowej zależności między napięciem a stanem naładowania.

Aby skonfigurować, otwórz aplikację Utility i przejdź do zakładki „Config". Na dole znajdziesz opcję emulacji BMS. W tej sekcji wprowadź dane swojej baterii, w tym liczbę grup szeregowych i całkowitą pojemność. Ważne jest, aby minimalne i maksymalne napięcia grup ogniw były ustawione prawidłowo, najlepiej odpowiadając lub będąc bardziej konserwatywnym niż te określone przez twój BMS. Zakres napięć dla ogniwa Li-Ion zwykle wynosi od 3 do 4.2V, ale twój BMS może mieć określone limity odcięcia ładowania i rozładowywania. Dostosuj te ustawienia zgodnie z limitami BMS lub wybierz wartości domyślne, jeśli nie jesteś pewien.

Uwaga: emulacja BMS jest konieczna tylko wtedy, gdy całkowicie zastąpiłeś oryginalną baterię. Jeśli dodałeś dodatkowy pakiet szeregowo z taką samą lub wyższą pojemnością, lub jeśli masz inną baterię równolegle, emulacja BMS nie jest wymagana. W przypadku konfiguracji z baterią równoległą główna zmiana polega na wyłączeniu trybu ładowania, który można znaleźć w ustawieniach systemu. Ten przewodnik ma na celu ułatwienie płynnego przejścia na niestandardową baterię, zapewniając optymalną wydajność i kompatybilność.

Dane:
- `V_min` = Minimalne napięcie pakietu baterii przy pełnym rozładowaniu.
- `V_max` = Maksymalne napięcie pakietu baterii przy pełnym naładowaniu.
- `V_current` = Aktualne napięcie pakietu baterii.

Wzór na obliczenie procentu baterii (`Bateria_%`):

Bateria_% = ((V_current - V_min) / (V_max - V_min)) * 100

Gdzie:
- `Bateria_%` to stan naładowania pakietu baterii w procentach.
- `V_min` to całkowite napięcie pakietu, gdy wszystkie ogniwa są na minimalnym napięciu.
- `V_max` to całkowite napięcie pakietu, gdy wszystkie ogniwa są na maksymalnym napięciu.
- `V_current` to aktualne całkowite napięcie pakietu baterii.

#### Informacje o modyfikacji ADC (G30 i ESx)

Specjalne podziękowania dla BXLR za dostarczenie cennych informacji na temat logiki R_adc.

[Otwórz kalkulator](https://lekrsu.github.io/shfw-walkthrough/calculator/)

**Uwaga 1**: Upewnij się, że dostosujesz R_adc, ponieważ odgrywa on znaczącą rolę w modyfikacji ADC.
**Uwaga 2**: Możesz również zmierzyć napięcie baterii, a następnie zwiększać napięcie dzielnika, aż odczyt napięcia systemowego będzie odpowiadał wcześniejszemu pomiarowi.
**Uwaga 3**: To ustawienie musisz zmienić dopiero po zmianie rezystorów na ESC.

### Licencja

Ten projekt jest licencjonowany na [Licencji MIT](LICENSE).

Zapoznaj się z plikiem [LICENSE](LICENSE), aby uzyskać szczegółowe warunki.

**Uwaga**: Licencja MIT jest stosowana do tego projektu. Chociaż pozwala na szerokie użytkowanie i modyfikację, nie obejmuje żadnych gwarancji. Współtwórcy i opiekunowie projektu nie ponoszą odpowiedzialności za jakiekolwiek problemy, szkody lub zobowiązania wynikające z użytkowania tego oprogramowania.

### Informacje o autorze

Ten przewodnik został napisany przez **lekrsu**, z którym można się skontaktować na Discordzie pod tagiem `lekrsu` i na Telegramie pod nazwą użytkownika `lekrsu`. Zachęcamy do wysłania pull requesta, jeśli uważasz, że informacje wymagają korekty.
