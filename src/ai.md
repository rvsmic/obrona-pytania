# AI
[`back to README.md`](../README.md)

## 30. Modele reprezentacji wiedzy.

### Podział 1:

* deklaratywne
  * wiedza  z danej dziedziny jest zbiorem specyficznych faktów
  * korzystanie z wiedzy — stosowanie do tego zbioru ogólnych procedur manipulacji faktami
  * wyraźne oddzielenie wiedzy z danej dziedziny od sposobu wykorzystania tej wiedzy w procesie wnioskowania
  * np.: reprezentacja logiczna
* proceduralne
  * przeważającą część wiedzy o świecie stanowią informacje o procesach i działaniach
  * "Wiedzieć" jest równoważne z "wiedzieć jak": znajomość danego pojęcia sprowadza się głównie do umiejętności manipulacji tym pojęciem
  * wiedza zawarta jest w procedurach (podprogramach), które wiedzą jak należy się zachować w określonej sytuacji

### Podział 2

* reprezentacje logiczne (rachunek zdań, rachunek predykatów, rachunek klauzul)
  * fakty zapisywane są w postaci formuł
  * wnioskowanie opiera się na uniwersalnych metodach dowodzenia twierdzeń np. rezolucji
* za pomocą reguł — reguły są to zdania postaci "jeśli ..., to ...", gdzie "..." to zdania logiczne, a "jeśli" i "to" to odpowiednio konkluzja i przesłanka reguły, (równoważne/podzbiorem reprezentacje logiczne??)
* za pomocą ram — stanowią połączenie metod deklaratywnych i proceduralnych; rama składa się ze szczelin (slots) opatrzonych nazwami, których zadaniem jest przechowywanie pewnej cząstki wiedzy o obiekcie reprezentowanym przez ramę (ze szczeliną mogą być związane również procedury);
* za pomocą sieci semantycznych — etykietowany graf skierowany, w którym wierzchołki reprezentują obiekty, pojęcia, wartości itd., natomiast krawędzie wyrażają relacje między wierzchołkami;
* stwierdzenia — kreprezentacje typu (obiekt, atrybut, wartość), w których pojedynczy fakt
zapisywany jest w postaci podanej trójki, a bazę wiedzy stanowi zbiór takich trójek
* ...

### Ontologia

Ontologia — dział filozofii odpowiadającym na pytania dotyczące struktury rzeczywistości

Ontologia wyższa:

* definiuje ogólne ramy dla koncepcji dotyczących reprezentacji świata
* definiuje i klasyfikuje w sposób hierarchiczny obiekty i zdarzenia występujące w świecie

![Ontologia wyższa](/src/img/ai/ontologia_wyzsza.png)

Reprezentacja wiedzy i wnioskowania dla kategorii:

* sieci semantyczne
  * umożliwiają wizualizację bazy wiedzy;
  * zawierają efektywne algorytmy wnioskowania o własnościach elementów na podstawie ich przynależności do kategorii
  * ogólną postacią sieci semantycznych są ramy
* logika opisowa
  * używa języka formalnego do budowania i łączenia definicji kategorii;
  * dostarcza efektywnych algorytmów do wyznaczania relacji zawierania pomiędzy kategoriami
  * formalizacja sieci semantycznych
  * zadania
    * Subsumpcja — sprawdzanie czy dana kategoria jest podzbiorem innej kategorii poprzez porównanie ich definicji
    * Klasyfikacja: sprawdzanie czy dany obiekt należy do kategorii.
    * Badanie zgodności: czy kryteria przynależności do kategorii są logiczne spełnialne.

## 31. Mechanizmy wnioskowań.


Wnioskowanie może być przeprowadzone

* bez hipotezy — generowanie nowych faktów tak długo, aż zostaną odpalone wszystkie możliwe reguły; Pytanie „Co wynika z X?”
* z hipotezą - weryfikacja (udowodnienie) konkretnej hipotezy na podstawie faktów zawartych w bazie wiedzy; Pytanie „Czy jest prawdą, że Y?

### Rodzaje

* wnioskowanie w przód (progresywne) — wnioskowanie od faktów do wniosków
  * wnioskowania z hipotezą lub bez
  * Pierwszym krokiem do opisu mechanizmu wnioskowania w przód jest zdefiniowanie założeń oraz celu wnioskowania.
  * Założenia  
    * System ma zdefiniowaną bazę wiedzy, czyli zbiór reguł oraz, ewentualnie, zadeklarowane fakty
    * System ma zdefiniowaną bazę wiedzy, czyli zbiór reguł oraz, ewentualnie, zadeklarowane fakty
  * Cel wnioskowania: znalezienie wszystkich możliwych do osiągnięcia wniosków.
* wnioskowanie w tył/wstecz (regresywne) — wnioskowanie od wniosków do faktów
* tylko wnioskowania z hipotezą.
  * cel: sprawdzenie, czy jeden, konkretny fakt (hipoteza) jest prawdziwy.
* mieszane — rodzaj wnioskowania przełączany w zależności od reguły

### Systemy ekspertowe

**Systemy ekspertowe** (eksperckie, z bazą wiedzy) — programy wspomagające korzystanie z wiedzy i ułatwiające podejmowanie decyzji; może być uważany za model ekspertyzy złożony z bazy wiedzy i procedury wnioskowania logicznego.

Cechy systemy ekspertowych:

* są wąsko wyspecjalizowane,
* mogą wspomagać lub nawet zastępować ekspertów w danej dziedzinie,
* mogą dostarczać rad, zaleceń i diagnoz dotyczących problemów z określonej dziedziny

![System ekspercki](/src/img/ai/system_ekspercki.png)
## 32. Metody uczenia maszynowego.

**Uczenie maszynowe** —  obszar sztucznej inteligencji poświęcony algorytmom, które poprawiają się automatycznie poprzez doświadczenie, czyli ekspozycję na dane. Algorytmy uczenia maszynowego budują model matematyczny na podstawie przykładowych danych, zwanych zbiorem uczącym, w celu prognozowania lub podejmowania decyzji bez bycia zaprogramowanym explicite przez człowieka do tego celu.

Metody maszynowego uczenia się

* uczenie nadzorowane (supervised learning) — zakłada obecność ludzkiego nadzoru nad tworzeniem funkcji odwzorowującej wejście systemu na jego wyjście
  * Nadzór polega na stworzeniu zestawu danych uczących się
    * wejściowy obiekt uczący się np. wektor
    * pożądana przez nadzorcę (nauczyciela) odpowiedź (np. jakaś konkretna wartość liczbowa)
* uczenie nienadzorowane (unsupervised learning)
  * jego zadaniem odkrywanie w zbiorze danych wzorców bez wcześniej istniejących etykiet i przy minimalnej ingerencji człowieka
  * zakłada brak oczekiwanego wyjścia w danych uczących
  * umożliwia modelowanie gęstości prawdopodobieństwa danych wejściowych
  * metody
    * analiza składowych głównych (PCA) — wykorzystuje się do zmniejszanie wymiarowości danych poprzez odkrywanie i odrzucanie cech które niosą ze sobą najmniej informacji
    * analiza skupień (clustering)
      * grupowanie lub segmentowanie zestawów danych ze wspólnymi atrybutami w celu ekstrapolacji występujących w nich zależności
      * identyfikuje podobieństwa w danych
      * pozwala na grupowanie danych, które nie zostały oznaczone, sklasyfikowane ani skategoryzowane
      * może być wykorzystana aby wykryć nietypowe dane
* uczenie przez wzmacnianie (reinforcement learning)
  * jego zadaniem jest interakcja ze środowiskiem za pomocą polityki na podstawie zebranych przez nią informacji
  * brak danych uczących, jes za to środowisko, z którego model będzie zbierał dane automatycznie
  * model uczy się na podstawie nagród, celem zmaksymalizowanie nagrody
  * większość algorytmów uczenia przez wzmacnianie polega na przygotowaniu polityki, zebraniu za jej pomocą danych o środowisku do bufora, wytrenowaniu jej na ich podstawie i powtarzania tego procesu do osiągnięcia zamierzonego skutku
  ![uczenie przez wzmacnianie](/src/img/ai/reinf_learning.png)
  Schemat przedstawiający uczenie przez wzmacnianie. Agent zwraca akcje na podstawie obserwacji, środowisko zwraca obserwacje i nagrody na podstawie akcji, bufor kolekcjonuje akcje, obserwacje i nagrody, agent uczy się na podstawie danych w buforze.

  Uczenie przez wzmacnianie najczęściej składa się z dwóch etapów: wstępnego zbierania danych oraz pętli uczenia. Pętla uczenia z kolei składa się ze zbierania danych oraz uczenia agenta na ich podstawie
  * elementy
    * agent —  element, który wchodzi w interakcję ze środowiskiem
    * środowisko — otoczenie, w którym agent się uczy (zadanie lub symulacja, z którym agent wchodzi w interakcję)
      * Cechy środowiska
        * stan środowiska — opisuje on stan środowiska w danym momencie
        * krok — najczęściej funkcja, która na podstawie podanej akcji aktualizuje stan środowiska i zwraca nagrodę oraz obserwację
        * epizod — zbiór kroków, po którym resetowany jest stan środowiska
        * nagroda — zmienna zwracana przez środowisko po wykonaniu kroku, która obrazuje jak korzystny był dany krok
        * obserwacja —  skalar, wektor lub macierz zwracana przez krok, mająca opisać obecny stan środowiska
      * powszechnie 2 środowiska — do trenowania i do testowania
    *bufor — to kontener danych przechowujący informacje zebrane przez agenta podczas uczenia. Informacji tych używa się do późniejszego wytrenowania agenta. Bufor jest używany tylko w niektórych algorytmach uczenia przez wzmacnianie
* uczenie częściowo nadzorowane (semi-supervised)
  * dane wejściowe zarówno oznaczone (zawierające odpowiadające im dane wyjściowe, konkretne przykłady), jak i nieoznaczone (wymagające przyporządkowania do danych wyjściowych, znalezienia odpowiedzi)
  * wykorzystywany, gdy organizacja dysponuje zbyt dużą ilością danych lub gdy informacje są na tyle zróżnicowane, że nie sposób przyporządkować odpowiedzi do każdej z nich
  * system sam proponuje odpowiedzi i jest w stanie stworzyć ogólne wzorce.

## 33. Budowa sieci neuronowych.

**Sieć neuronowa** – system przeznaczony do przetwarzania informacji, którego budowa i zasada działania są w pewnym stopniu wzorowane na funkcjonowaniu fragmentów rzeczywistego (biologicznego) systemu nerwowego.

Budowa sieci neuronowej:
* **warstwa wejściowa** — warstwa, która przyjmuje dane wejściowe
* **warstwy ukryte** — warstwy, które przetwarzają dane wejściowe
* **warstwa wyjściowa** — warstwa, która zwraca wynik
  ![sieć neuronowa](/src/img/ai/nn.png)
  
Cechy sieci neuronowych:
* na strukturę składają się neurony połączone ze sobą synapsami. Z synapsami związane są wagi, których interpretacja zależy od modelu.

![sieć neuronowa 2](/src/img/ai/nn2.png)

![sieć neuronowa 3](/src/img/ai/nn3.png)

![sieć neuronowa 4](/src/img/ai/nn4.png)

![sieć neuronowa 5](/src/img/ai/nn5.png)

**Propagacja wsteczna** — metoda uczenia nadzorowanego wielowarstwowych sieci neuronowych. Polega na propagacji błędu popełnionego przez sieć w trakcie uczenia się wstecz, od warstwy wyjściowej do warstwy wejściowej. Wagi połączeń są aktualizowane w kierunku przeciwnym do propagacji sygnału. Tempo modyfikacji wag określone jest natomiast za pomocą współczynnika uczenia (learning rate).
