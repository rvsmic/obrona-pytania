# Systemy operacyjne
[`back to README.md`](../README.md)
## 23. Wielowarstwowa organizacja systemów komputerowych.
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
## 27. Organizacja systemu plików i pamięci zewnętrznej. 
