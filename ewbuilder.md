# EW-Builder
Tworzenie obiektów i pozyskiwanie atrybutów z elementów warstw programu EW-Mapa.

### Tworzenie obiektów liniowych
Możliwość tworzenia obiektów liniowych poprzez łączenie sąsiadujących elementów liniowych. Atrybuty dla obiektu pozyskiwane są na podstawie treści etykiety znajdującej się w pobliżu elementów. Segmentacja obiektu następuje w chwili zmiany treści etykiety, w punkcie styku więcej niż dwóch linii oraz opcjonalnie w chwili zmiany operatu elementu liniowego. Dla obiektu przypisywany jest operat tworzących go segmentów.

Utworzone obiekty liniowe będą posiadały atrybuty pozyskane z treści etykiet - nie jest jednak możliwe w pełni poprawne ustalenie części atrybutów (np. funkcji przewodu). Po naniesieniu poprawek, wynikających z analizy operatów, istnieje możliwość przeprowadzenia dodatkowych operacji, takich jak redukcja nadmiernej segmentacji, generacji etykiet, segmentacja obiektów i innych w ramach możliwości programu [EW-Database](ewdatabase.md).

W przypadku sieci napowietrznych, które zostały naniesione za pomocą symboli, istnieje możliwość utworzenia elementów liniowych poprzez dopasowanie par symboli spełniających kryteria dopuszczalnej odległości oraz dopuszczalnej różnicy kąta obrotu. Istnieje także możliwość utworzenia listy niedopasowanych symboli.

Podczas tworzenia obiektów liniowych można ustalić, czy zmiana operatu segmentu powoduje segmentacje obiektu oraz czy operat etykiety musi być taki sam, jak operat linii. Dodatkowo istnieje możliwość zadania maksymalnej odległości etykiety od elementu liniowego oraz maksymalnej różnicy pomiędzy kątem obrotu etykiety, a kotangensem współczynnika kierunkowego linii.

### Tworzenie obiektów punktowych
Możliwość tworzenia obiektów punktowych znajdujących się na warstwach, wraz z wyszukiwaniem etykiet dla tworzonych obiektów i pozyskiwania na ich podstawie atrybutów opisowych. Utworzone obiekty posiadają operat zgodny z operatem symbolu, z którego się składają.

Podczas tworzenia obiektów punktowych można ustalić, czy operat etykiety musi być taki sam, jak operat linii. Dodatkowo istnieje możliwość zadania maksymalnej odległości etykiety od symbolu obiektu.

W przypadku, gdy na warstwach nie występuje symbol obiektu (bardzo częsty przypadek dla rzędnych wysokościowych), istnieje możliwość wygenerowania symbolu obiektu w punkcie wstawienia najbliższego obiektu punktowego lub w punkcie załamania najbliższego obiektu złożonego z linii. Maksymalna odległość opisu od punktu wstawienia wygenerowanego symbolu może zostać ustalona - jest ona liczona od punktu wstawienia opisu do punktu wstawienia wygenerowanego symbolu. W przypadku, gdy dopasowanie współrzędnych symbolu jest niemożliwe, istnieje możliwość wygenerowania symbolu w miejscu punktu wstawienia opisu.

### Tworzenie obiektów powierzchniowych
Możliwość utworzenia obiektów powierzchniowych na poprzez połączenie sąsiadujących elementów liniowych, które stanowią zamkniętą powierzchnie oraz pozyskania obiektów z segmentów będących okręgami. Podczas tworzenia obiektów możliwe jest także dopasowanie istniejących etykiet oraz pozyskanie z nich atrybutów obiektów.

Podczas tworzenia obiektów powierzchniowych można ustalić, czy zmiana operatu segmentu powoduje segmentacje obiektu oraz czy operat etykiety musi być taki sam, jak operat linii. Dodatkowo istnieje możliwość zadania maksymalnej odległości etykiety od elementu liniowego.

### Wymagania dotyczące warstw
Poprawne utworzenie obiektów wymaga, aby wszystkie segmenty i opisy znajdowały się na odpowiednich warstwach. Istnieje jednak możliwość pozyskania etykiet dla obiektów w przypadku gdy te znajdują się na różnych warstwach ze względu na rodzaj obiektu (np. opisy sieci kanalizacji deszczowej znajdują się na warstwie z opisem kanalizacji sanitarnej).

Konwersja warstw do nowego standardu jest możliwa przy użyciu narzędzi dostarczanych wraz z programem EW-Mapa. Utworzone narzędzie umożliwia także wspomaganie procesu tworzenia pliku schematu konwersji warstw. Schemat konwersji powinien uwzględniać i korygować ewentualne błędy kartowania (symbole na warstwach opisowych itd.).

W przypadku, gdy na warstwach znajdą się niepoprawne elementy, proces tworzenia obiektów może być niekompletny lub niepoprawny.

Aby poprawnie pozyskać informacje dotyczące sposobu pozyskania danych należy podzielić dane występujące na warstwach. W tym celu należy wykonać osobny eksport dla każdego źródła pozyskania danych. Ustalenie źródła pozyskania danych może odbyć się także na drodze analizy treści etykiet obiektów.

### Dodatkowe operacje
Utworzenie obiektów jest pierwszym krokiem podczas tworzenia opracowania bazy danych. Zwykle konieczna jest także analiza operatów, w wyniku której pozyskiwane są brakujące atrybuty i korygowane ewentualne błędy. Często zdarza się, że operator podczas kartowania wprowadza dane na złych warstwach, czy też stosuje niepoprawny symbol dla obiektu. Część z tych błędów może zostać wychwycona - część jednak wymaga analizy danych źródłowych.

Po wykonaniu analizy operatów baza danych wymaga wielu operacji takich jak usunięcie nadmiernej segmentacji, utworzenie relacji pomiędzy obiektami, przypisanie poprawnych dat pomiaru itd.. Możliwości te oferuje narzędzie [EW-Database](ewdatabase.md).

### Sygnalizowanie błędów
Duża część ewentualnych błędów może zostać wychwycona i przekazana w formie list. Poprawa tych błędów wymaga analizy operatów - ich automatyczna naprawa może nie być trafna, co powodowało by poważnie konsekwencje. Listy dotyczą zarówno obiektów z podejrzeniem wystąpienia błędu, jak i miejsc w opracowaniu, w których istnieje prawdopodobieństwo błędu (np. fragment sieci gazowej skartowany jako sieć wysokiego ciśnienia opisany w etykiecie jako sieć niskiego ciśnienia).
