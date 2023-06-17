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
## 26. Zarządzanie pamięcią operacyjną w systemie operacyjnym.
## 27. Organizacja systemu plików i pamięci zewnętrznej. 
