# Wstęp do teorii obliczalności
[`back to README.md`](../README.md)
## 44. Definicja funkcji obliczalnej (częściowo rekurencyjnej).
## 45. Maszyna Turinga jako model procesów obliczalnych.
## 46. Zagadnienia nierostrzygalne w kontekście obliczalności.

### Problem nierozstrzygalny

**Problem nierozstrzygalny** – problem, dla którego nie istnieje algorytm, który po skończonej liczbie kroków dałby odpowiedź na pytanie, czy dana instancja problemu ma rozwiązanie.

> Definicja z skryptu dr. Mycki:
>
> *Mówimy, że problem decyzyjny dla zbioru S jest rozstrzygalny jeżeli S jest zbiorem rekurencyjnym. Problem decyzyjny jest nierozstrzygalny jeżeli nie jest rozstrzygalny*

#### Problem stopu

**Problem stopu** – problem, czy dany program zatrzyma się dla dowolnych danych wejściowych.
> *Nie istnieje maszyna Turinga rozstrzygająca w skończonej liczbie kroków, czy dowolna maszyna Turinga zakończy pracę.*

##### Dowód:

Załóżmy, że następujący program rozstrzyga problem stopu:

```
procedura stop(program, dane):
   jeżeli program(dane) zatrzymuje się, to
      zwróć tak,
   w przeciwnym przypadku
      zwróć nie.
```

czyli jeżeli `program` zatrzymuje się dla danych wejściowych, to zwracamy `tak`, w przeciwnym przypadku zwracamy `nie`.

Załóżmy że `stop` jest rozstrzygalny, czyli istnieje maszyna Turinga `M`, która go rozstrzyga.

Teraz rozważmy następujący program:

```
procedura test(program): 
   jeżeli stop(program, program) = tak, to
      zapętl się
```

Pytanie: czy `test(test)` zatrzymuje się?


* Jeżeli `test(test)` nie zatrzymuje się, to `stop(test, test) = nie`, czyli `test(test)` zatrzymuje się.
* Jeżeli `test(test)` zatrzymuje się, to `stop(test, test) = tak`, czyli `test(test)` nie zatrzymuje się.

Przeczy to założeniu, że `stop` jest rozstrzygalny, więc `stop` nie jest rozstrzygalny.

#### Inne problemy nierozstrzygalne

* Nierozstrzygalność Entscheidungsproblem — *Nie istnieje algorytm rozstrzygający w skończonej liczbie kroków, czy dana formuła jest dowodliwa w wybranym systemie aksjomatycznym*
* Istnienie rozwiązania równania diofantycznego
* Problem domina — Czy można pokryć płaszczyznę zestawem kafelków, zachowując kolory na styku

## 47. Definicja i klasy złożoności obliczeniowej – czasowej i pamięciowej

> Zdefiniowane przy algorytmach, dokładnie: [*Złożoność obliczeniowa*](algorytmy.md#złożoność-obliczeniowa)
