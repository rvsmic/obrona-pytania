# Systemy operacyjne

[`back to README.md`](../README.md)

## 23. Wielowarstwowa organizacja systemów komputerowych.

## 24. System operacyjny – charakterystyka, zadania, klasyfikacja

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

## 25. Procesy i wątki – charakterystyka i problemy

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

## 26. Zarządzanie pamięcią operacyjną w systemie operacyjnym

Pamięć operacyjna — kluczowy zasób systemu komputerowego dla wykonywania programów. Zarządzanie pamięcią jest jednak dość skomplikowane, ponieważ
jej poszczególne części są w tym samym czasie wykorzystywane przez wiele procesów oraz
przez jądro systemu operacyjnego.

Podstawowe zadania, realizowane w ramach zarządzania pamięcią operacyjną obejmują
przydział pamięci i jej odzyskiwanie, ochronę, udostępnianie w celu współdzielenia,
transformację adresów oraz transfer danych. Zadania te podzielone są między układy
sprzętowe na poziomie architektury komputera, a system operacyjny.

### Pamięć wirtualna

Technika programowa i sprzętową pozwawalająca na sztuczne zwiększenie pamięci RAM.

Pamięć wirtualna gospodaruje pamięcią operacujną RAM, pozwalając na przydzielenie pamięci dla wielu procesów, zwalnianie jej i powtórne przydzielanie, w ilości większej niż rzeczywista ilość pamięci fizycznej zainstalowanej w komputerze poprzez przeniesienie danych z ostatnio nie używanej pamięci do pamięci masowej (np. twardego dysku); w sytuacji gdy procesor odwołuje się do danych z pamięci przeniesionej na dysk przesuwa się te dane do pamięci w wolne miejsce, a gdy brak wolnej pamięci - zwalnia się ją przez wyżej opisane przerzucenie jej na dysk.

### Sposoby zarządzania pamięcią operacyjną w systemie

#### Segmentacja

Jedna z metod ochrony pamięci, używana przy wielozadaniowości. Każdy proces otrzymuje swój własny obszar pamięci, realizowany poprzez rejestry segmentowe.

Segmentacja pamięci polega na podzieleniu przez procesor pamięci fizycznej na ciągłe
bloki nazywane segmentami, które opisane są przez deskryptory (8 bajtowy rekord).
![deskryptor](/src/img/systemy_operacyjne/deskryptor.png)

* B — adres bazowy segmentu, czyli fizyczny adres początku segmentu w pamięci operacyjnej,
* L — długość segmentu,
* G — sposób interpretacji limitu segmentu (0 — w bajtach, 1 — w 4KB stronach),
* DPL — poziom uprzywilejowania (0 — najwyższy, 3 — najniższy),
* P — bit obecności (używany w pamięci wirtualnej),
* AV — nie używany,
* A — mówi czy deskryptor jest używany.

Deskryptory segmentów przechowywane są w tablicy deskryptorów segmentów

* globalnej — GDT (Global Descriptor Table) — jest tylko jedna, opisuje segmenty widoczne dla wszystkich procesów
* lokalnej — LDT (Local Descriptor Table) — jest ich wiele, opisują preywatne segmenty procesów.

![Mechanizm segmanetacji](/src/img/systemy_operacyjne/mech_segm.png)

Adres logiczny składa się selektora segmentu SE i przesunięcia D.

* Funkcje selektora segmentu pełni jeden z rejestrów segmentowych:
  * dla kodu rejestr CS,
  * dla danych  resejst DS, ES,
  * dla stosu SS.
* Selektor zawiera:
  * indeks deskryptora — położenie segmentu znajdującego się w tablicy deskryptorów,
  * TI — określa o którą tablicę chodzi (0 — GDT, 1 — LDT)
  * RPL - żądany poziom uprzywilejowania – określa poziom uprzywilejowania procesu
![Selektor segmentu](/src/img/systemy_operacyjne/selektor.png)

* Adres liniowy — suma pobieranego z pola adresowego rozkazu przesunięcia D i adresu początku segmentu B pobieranego z deskryptora. Adres liniowy może być poddany przetwarzaniu przez mechanizm stronicowania.
* Komparator sprawdza czy przesunięcie D nie wykracza poza długość segmentu L zapisanego w deskryptorze. Gdy tak się zdarzy generowany jest wyjątek EXC który powoduje wywołanie systemu operacyjnego. System operacyjny podejmuje decyzję, co zrobić z naruszającym przydzielony segment procesem.

##### Zalety i wady segmentacji

* Zalety:
  * Skuteczna, prosta relokacja kodu i danych – nieważne jest, gdzie w pamięci fizycznej znajduje się segment, program może odwoływać się do kolejnych słów pamięci w ramach segmentu, licząc od zera do końca segmentuość implementacji,
  * dobra ochrona — ze względu na strukturę ligicznej przestrzeni adresowej,
  * łatwe współdzielenie kodu i danych,
  * brak wewnętrzej fragmentacji, 
  * wyższy stopień wieloprogramowości.
* Wady
  * komplikacja modelu programowego (dwuelementowy adres),
  * problematyczna i niewydajna dynamiczna alokacja,
  * praktycznie nierealizowalna pamięć wirtualna,
  * duże ograniczenia rozmiarów segmentów – zmuszało to do dzielenia kodu programów oraz bloków danych w sposób nienaturalny, utrudniając tworzenie wielkich struktur danych (te ograniczenie zostało później zniesione, ale dzielenie programu na logiczne części jest dalej skomplikowane)
  
#### Stronicowanie

Jeden ze sposobów rozwiązania problemu zewnętrznej fragmentacji,
polegający na dopuszczeniu nieciągłości rozmieszczenia logicznej przestrzeni adresowej
procesu w pamięci fizycznej. Jest to podział pamięci na mniejsze obszary o ustalonej lub
zmiennej wielkości i przydzielanie tym blokom adresów fizycznych lub logicznych.

Cechy:

* pamięć fizyczna dzielona jest na bloki o jednakowej wielkości zwane ramkami (frame),
* pamięć fizyczna dzielona jest na bloki o jednakowej wielkości zwane stronami,
* rozmiary stron i ramek równe,
* przy wykonywaniu procesu, strony z pamięci pomocniczej wprowadzane są w odpowiednie ramki pamięci operacyjnej.

W celu odróżnienia stron z obrazem procesu od stron pamięci fizycznej, strony fizyczne nazywa się ramkami (ang. frames). Pamięć procesu tworzą kolejne strony, natomiast ramki mogą być porozrzucane gdziekolwiek w pamięci. Ich fizyczna lokalizacja zawarta jest w tablicy stron.

![Schemat stronnicowania](/src/img/systemy_operacyjne/stronnicowanie.png)

##### Tablica stron

Składa się z 32 bitowych słów, każde opisuje pojedynczą stronę.
Opis strony zawiera:

* adres fizyczny strony,
* atrubuty strony: bit obecności, dostępu, możliwość zapisu, przywileje zapisu, czy był zapis
![Zawartość deskryptora strony](/src/img/systemy_operacyjne/deskryp_strony.png)

W architekturze IA-32 dwa schematy stronnicowania:

* jednopoziomowe (strona ma 4MB)
* wielopoziomowe (strona ma 4KB)

#### Segmentacja ze stronicowaniem

Segmentacja ze stronicowaniem — połączenie technik segmentacji
i stronicowania.

* Z punktu widzenia procesu, pamięć logiczna składa się z szeregu segmentów, które są rozmieszczone w pamięci fizycznej w spójny sposób. Są one dzielone na strony i każda strona może być pamiętana w dowolnej ramce. Tak więc adres logiczny składa się z numeru segmentu i adresu w obrębie segmentu. Na podstawie numeru segmentu można wyznaczyć tablicę stron określającą rozmieszczenie stron tworzących segment.
* Podobnie jak w przypadku stronicowania, możemy mieć do czynienia ze stronicowaniem wielopoziomowym, jak również z podręczną tablicą stron
* Dzięki połączeniu technik segmentacji i stronicowania
  * można przydzielać procesom wiele segmentów, czy współdzielić segmenty unikająć fragmentacji zewnętrznej.

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
