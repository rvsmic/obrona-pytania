# AI
[`back to README.md`](../README.md)
## 30. Modele reprezentacji wiedzy.
## 31. Mechanizmy wnioskowań.
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
## 33. Budowa sieci neuronowych. 
