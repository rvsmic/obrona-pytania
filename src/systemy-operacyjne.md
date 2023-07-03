# Systemy operacyjne

[`back to README.md`](../README.md)

## 23. Wielowarstwowa organizacja systemów komputerowych.

> Według wykładu profesora Łojewskiego, [wy2 2020/2021](https://drive.google.com/drive/folders/1l-LHcaOcwQoiGkw8m59UWU9ySmLEs_vf)

![warstwy](img/systemy-operacyjne/warstwy-systemu.png)

1. Sprzęt — procesor, pamięć, urządzenia wejścia/wyjścia
2. Jądro systemu — obsługuje sprzęt, ma w sobie sterowniki, które umożliwiają komunikację z urządzeniami, komunikuje się ze sprzętem w sposób bezpośredni
3. API — interfejs programowania aplikacji, umożliwia komunikację z jądrem systemu operacyjnego za pomocą funkcji jądra, w tym **powłoce** (shell)
4. Programy narzędziowe (systemowe) — w tym powłoka, są pierwszymi programami, które są uruchamiane po starcie systemu i umożliwiają komunikację z użytkownikiem (tutaj też jest interpreter poleceń, chyba)
5. Programy użytkowe — oprogramowanie, które jest używane przez użytkownika: gry, edytory, przeglądarki, itp.

Na przykładzie systemu Android:

* Linux Kernel Layer – warstwa jądra systemu operacyjnego oparta na Linuxie
* Native Libraries Layer – natywne biblioteki systemu Android
* Application Framework Layer – warstwa, z którą bezpośrednio komunikują się aplikacje min. zarządzanie oknami, zasobami itp.
* Application Layer – warstwa aplikacji, z którą w interakcję wchodzą użytkownicy, aby np. wykonać połączenie telefoniczne

**Najogólniej to system jest podzielony na jądro oraz programy systemowe (interpreter poleceń, powłoka, itp.).** Programy użytkowe są uruchamiane przez użytkownika, a programy systemowe są uruchamiane przez jądro systemu operacyjnego.

> Według wikipedii [system komputerowy](https://www.wikiwand.com/pl/System_komputerowy) i [system operacyjny](https://www.wikiwand.com/pl/System_operacyjny)

Na początek dwa obrazki z wikipedii:

![logiczne warstwy](https://upload.wikimedia.org/wikipedia/commons/1/18/Operating_system_placement-pl.svg)

Tutaj mamy podział na warstwy logiczne, które są zależne od siebie. System operacyjny pośredniczy między sprzętem a aplikacjami, które są używane przez użytkownika.

![Schemat](https://upload.wikimedia.org/wikipedia/commons/3/3e/System_operacyjny_schemat_ogolny.svg)

Tutaj mamy schemat, gdzie jądro zawiera w sobie sterowniki, które umożliwiają komunikację z urządzeniami. Jądro jest częścią systemu operacyjnego, a system operacyjny jest częścią systemu komputerowego. Powłoka umożliwia użytkownikowi komunikację z jądrem.

Wikipedia wyszczególnia 5 warstw systemu komputerowego:

1. Sprzęt — procesor, pamięć, urządzenia wejścia/wyjścia, sa to podstawowe zasoby systemu komputerowego
2. Oprogramowanie systemowe — kontroluje i koordynuje sprzęt, 
3. Oprogramowanie narzędziowe — interfejsy zapewniające dostęp do zasobów systemu
4. Oprogramowanie użytkowe — oprogramowanie, które jest używane przez użytkownika: gry, edytory, przeglądarki, itp.
5. Użytkownik — człowiek, który używa systemu komputerowego, ale również inny system czy maszyna

## 24. System operacyjny – charakterystyka, zadania, klasyfikacja.
System operacyjny — program działający jako pośrednik między użytkownikiem a sprzętem komputerowym; zarządza zasobami systemu komputerowego; tworzy wygodne dla użytkownika środowisko do wykonywania programów.

* Charakterystyka
  * struktura
    * jądro — zbiór modułów, które ukrywają szczegóły sprzętowej realizacji systemu komputerowego, udostępniając pewien zestaw usług, wykorzystywanych między innymi do implementacji programów systemowych
    * powłoka — program komunikujący użytkownika z systemem operacyjnym
    * system plików — sposób ustrukturyzowanego zapisu danych na nośniku.
  * efektywność zarządzania zasobami
  * wygodny interfejs użytkownika
* Zadania
  * definiowanie interfejsu użytkownika — zbiór poleceń lub system okienkowy, menu
  * udostępnianie systemu plików — organizuje i ułatwia dostęp do informacji np. w postaci hierarchicznego systemu plików 
  * udostępnianie środowiska do wykonywania programów
    * dostarcza struktury do wykonywania programu, zachowywania i odtwarzania stanu przetwarzania (procesy i przełączanie kontekstu)
    * komunikacja między procesami (kolejki, strumienie, pamięć współdzielona)
    * mechanizmy synchronizacji procesorów (np. semafory)
  * zarządzanie zasobami
  * planowanie i przydział czasu procesora dla zadań
  * kontrola i przydział pamięci operacyjnej dla uruchomionych zadań
  * sterowanie urządzeniami wejścia-wyjścia — moduły sterujące
  * obsługa podstawowej klasy błędów
* Klasyfikacja
  * pod względem komunikacji z użytkownikiem
    * tekstowe — pierwsze wersje DOSu, Unix
    * graficzne 
  * pod względem architektury
    * monolityczne — jednozadaniowe systemy posiadające najprostszą strukturę
    * warstwowe — osiadające hierarchiczną strukturę poleceń systemowych, możliwa wielozadaniowość
    * klient/serwer — rozbudowana struktura, nadzorują podrzędne systemy na komputerach w sieci
    * równoległe
    * rozproszone
  * pod względem planowania i przydziału czasu procesora poszczególnym zadaniom
    * czasu rzeczywistego (RTOS)
    * czasowo niedeterministyczne
  * pod względem sposobu realizacji przełączania zadań
    * z wywłaszczaniem zadań
    * bez wywłaszczania
  * pod względem ilości zadań (programów), które mogą wykonać
    * jednozadaniowe (jednoprogramowe)
    * wielozadaniowe (wieloprogramowe)
  * pod względem środowiska użytego do implementacji systemu
    * sprzętowe — sprzętowo programowe rozwiązania integrowane z wybraną architekturą procesora; sprzętowa część systemu przyśpiesza wybrany zakres czynności wykonywanych przez system (przykładowo przełączania zadań i zachowywanie ich kontekstu)
    * programowe
  * inny
    * otwarte — można uruchomić na dowolnej maszynie wskazanego rodzaju i w określonym stopniu modyfikować
    * wbudowane — systemy operacyjne dla urządzeń wbudowanych
  * Zazwyczaj jako otwarte systemy operacyjne spotyka się systemy w pełni programowe, czasowo niedeterministyczne stosujące wywłaszczenie przy przełączaniu zadań. Wbudowane systemy operacyjne są najczęściej czasowo deterministyczne, zazwyczaj nie stosują wywłaszczenia zadań, bywa, że są realizowane również w sprzęcie.

## 25. Procesy i wątki – charakterystyka i problemy.
* Proces — egzemplarz wykonywanego programu
  * każdy proces ma swój unikatowy numer (PID)
  * aby współbieżnie wykonać pewne fragmenty programu program może utworzyć określoną ilość wątków
  * każdy proces posiada proces nadrzędny (rodzica) i może posiadać procesy podrzędne (dzieci) — drzewo procesów
  * każdy proces ma odrębne zasoby
    * własną przestrzeń adresową
    * listę otwartych plików, urządzeń
    * czas procesora
    * pamięć
  * proces składa się z
    * kodu programu
    * licznika rozkazów
    * stosu programu
    * sekcji danych
  * wykonanie procesu musi przebiegać sekwencyjnie;może przyjmować kilka stanów:
    * aktualnie wykonywany
    * czekający na udostępnienie zasobów
    * uśpiony
    * przeznaczony do zniszczenia
    * proces zombie — wpis w tablicy procesów opisujący program, którego wykonanie w systemie operacyjnym zostało zakończone, ale którego zamknięcie nie zostało jeszcze obsłużone przez proces rodzica
    * właśnie tworzony itd.
  * tworzenie procesów
    * uruchomienie programu za pomocą powłoki systemowej, proces wywołujący wykonuje polecenie fork lub jego pochodną
    * System operacyjny tworzy przestrzeń adresową dla procesu oraz strukturę opisującą nowy proces
      * wypełnia strukturę opisującą proces,
      * kopiuje do przestrzeni adresowej procesu dane i kod, zawarte w pliku wykonywalnym,
      * mapuje współdzielone zasoby systemowe w przestrzeń adresową procesu,
      * ustawia stan procesu na działający,
      * dołącza nowy proces do kolejki procesów oczekujących na procesor (ustala jego priorytet),
      * zwraca sterowanie powłoce systemowej.

  * kończenie procesów
    * Proces wykonuje ostatnią instrukcję – zwraca do systemu operacyjnego kod zakończenia. Jeśli proces zakończył się poprawnie, zwraca wartość 0, w przeciwnym wypadku zwraca wartość kodu błędu.
    * Jeśli ok, to stan procesu zmienia się na gotowy do zniszczenia i rozpoczyna zwalnianie wszystkich zasobów, które w czasie działania procesu zostały temu procesowi przydzielone.
    * System operacyjny po kolei kończy wszystkie procesy potomne w stosunku do procesu macierzystego.
    * System operacyjny zwalnia przestrzeń adresową procesu. Jest to dosłowna śmierć procesu.
    * System operacyjny usuwa proces z kolejki procesów gotowych do uruchomienia i szereguje zadania. Jest to ostatnia czynność wykonywana na rzecz procesu.
    * Procesor zostaje przydzielony innemu procesowi.

* Wątek (thread) — część programu wykonywana współbieżnie w obrębie jednego procesu
  * w jednym procesie może istnieć wiele wątków
  * wątki współdzielą prawie wszystkie zasoby procesu z wyjątkiem czasu procesora, który jest przydzielany każdemu wątkowi osobno dzięki temu
    * Wątki wymagają mniej zasobów do działania i też mniejszy jest czas ich tworzenia.
    * Dzięki współdzieleniu przestrzeni adresowej (pamięci) wątki jednego zadania mogą się między sobą komunikować w bardzo łatwy sposób, niewymagający pomocy ze strony systemu operacyjnego.
  * W systemach wieloprocesorowych, a także w systemach z wywłaszczaniem, wątki mogą być wykonywane równocześnie (współbieżnie)
* Problemy
  * wątki wykonywane równocześnie współdzielą pamięć adresową — równoczesny dostęp do wspólnych danych może powodować utratę spójności danych i w konsekwencji błędne działanie programu — do zapobiegania temu służą mechanizmy synchronizacji ( semafory, muteksy, sekcje krytyczne)



## 26. Zarządzanie pamięcią operacyjną w systemie operacyjnym.
<!-- 
Pamięć operacyjna — pamięć komputerowa adresowana i dostępna bezpośrednio przez procesor, a nie za pośrednictwem urządzeń wejścia-wyjścia. Większość procesorów wymaga by w pamięci operacyjnej były umieszczone rozkazy procesora (program) dostępne bezpośrednio dla jego jednostek wykonawczych, stąd pamięć operacyjna jest każdą pamięcią, która może być zmapowana w przestrzeń adresową procesora. -->

## 27. Organizacja systemu plików i pamięci zewnętrznej. 

> Według jakiś prezek z neta
> <https://kcir.pwr.edu.pl/~witold/opsys/os_fsys_s.pdf>
> <http://edu.pjwstk.edu.pl/wyklady/sop/scb/wyklad9/>
> <https://www.wikiwand.com/pl/System_plik%C3%B3w>

Systam plików to metoda przechowywania, zarządznia i dostępu do plików. Przchowują one również infomacje o tych plikach. Systemy plików stosuje się na roznych mośnikach danych, takich jak dyski, pendrive'y, karty pamięci, itp. Nowoczene aplikacie uzywają sysrtemu plików, a nie bezpośrednio dysku.
Systamy plików są zależne od systemu operacyjnego, a nie od sprzętu.

Z wikipedii:

> Z formalnego punktu widzenia system plików to reguły umieszczania na nośniku abstrakcyjnych danych oraz informacji umożliwiających przechowywanie tych danych, łatwy i szybki dostęp do informacji o danych oraz do tych danych, manipulowania nimi, a także sposobach usuwania ich.

### Organizacja systemu plików

* Logiczna — rekordy o stałej lub zmiennej długości, rekordy są grupowane w pliki, pliki są grupowane w katalogi
* Fizyczna — zbiór bloków dyskowych. Zjawisko fragmentacji powoduje, że plik może być rozproszony na wielu blokach dyskowych

### Operajce na plikach

* tworzenie
* kasoowanie
* odczyt
* zapis

### Atrybuty plików

mogą to być:

* nazwa
* hasło
* typ
* twórca
* właściciel
* uprawnienia
* czas utworzenia
* flagi
  * tekstowy/binary
  * archiwum
  * ukrycia
* rozmiar
* ...
* flagi uniksowe:
  * r — odczyt
  * w — zapis
  * x — wykonanie
  * specjalne:
    * s — setuid
    * t — sticky bit
    *  ...

### Katalogi

Katalog służy do grupowania plików i innych katalogów. Katalogi mogą być zagnieżdżone. Katalogi mogą być puste. Katalogi mogą być ukryte. 

Czasami katalogi przyjmują strukturę:

* drzewa jedenopozionowego
* drzewa wielopozionowego
* grafu acyklicznego
* grafu spójnego
  
### Struktura logiczna/przydziału miejsca na dysku

* ciągły — plik zajmuje ciągły obszar dysku, jest zły bo trzeba znać rozmiar pliku, a jeśli plik jest za duży to nie można go zapisać
* listowy FAT — bloki tworzące plik są rozproszone na dysku, a w pliku jest lista bloków, które należą do pliku. Jest to dobre rozwiązanie, ale trzeba znać rozmiar listy, a jeśli lista jest za duża to nie można jej zapisać. Prostrza impelemntacja zakłada liste jednokierunkową, gdzie koniec jedenego fragmentu wskazuje na początek następnego fragmentu.
* wiele ciągłych obszarów — plik jest podzielony na wiele ciągłych obszarów, które są rozproszone na dysku. W pliku jest lista obszarów, które należą do pliku. **NTFS** używa tego rozwiązania.
* indeksowy — plik jest podzielony na wiele ciągłych obszarów, które są rozproszone na dysku. Bloki są  numerowane i zebrane do jedengo bloku, tzw, bloku indeksowanego. W bloku indeksowanym jest lista numerów bloków, które należą do pliku.

### Nośniki danych

Nośniki danych posiadają strukturę blokową (bloki są najmniejszymi jednostkami, które mogą być odczytywane i zapisywane (w całości)). W dyskach wiekość jednego bloku jest wielokrotnością wielkości sektora.

System operacyjny łączy bloki w klastry
