# Podstawowe informacje o programowaniu
[`back to README.md`](../README.md)
## 5. Pozycyjne systemy liczbowe i konwersje pomiędzy nimi.

**Systemy pozycyjne** (systemy liczbowe) – metody zapisywania liczb  w taki sposób, że w zależności od pozycji danej cyfry w ciągu, oznacza ona wielokrotność potęgi pewnej liczby uznawanej za bazę danego systemu (np. $456_{(10)}=4\times 10^2+5\times 10^1 +5\times 10^0$).

### Konwersja z systemu dziesiętnego na system o podstawie $n$

1. Podziel liczbę przez $n$ i pobierz resztę z dzielenia.
2. W $i$-tym kroku zapisz cyfrę na pozycji $i$ od prawej strony.
3. Jeśli liczba jest różna od $0$, wróć do kroku 1.

i|operacja|wynik|aktualna liczba
---|:---:|---:|---:
$0$|$23/2$|$11\ r.\ 1$|$1$
$1$|$11/2$|$5\ r.\ 1$|$11$
$2$|$5/2$|$2\ r.\ 1$|$111$
$3$|$2/2$|$1\ r.\ 0$|$0111$
$4$|$1/2$|$0\ r.\ 1$|$10111$


### Konwersja z systemu o podstawie $n$ na system dziesiętny

Należy zsumować wartości wszystkich cyfr pomnożonych przez $n$ podniesione do potęgi odpowiadającej pozycji cyfry od prawej strony liczonej od 0.

$10111_{(2)}=1\times 2^4+0\times 2^3+1\times 2^2+1\times 2^1+1\times 2^0=16+0+4+2+1=23_{(10)}$

### Konwersja z systemu o podstawie $n$ na system o podstawie $m$

Aby z systemu o podstawie $n$ przekonwertować na system o podstawie $m$ można przekonwertować z systemu o podstawie $n$ na system dziesiętny, a następnie z systemu dziesiętnego na system o podstawie $m$.

## 6. Sposoby cyfrowej reprezentacji liczby całkowitej i rzeczywistej.

### Liczby całkowite

* kod uzupełnień do dwóch (w skrócie U2 lub ZU2) — obecnie najpopularniejszy sposób reprezentacji liczb całkowitych w systemach cyfrowych
* w U2 na $n$ bitach można zapisać liczbę z zakresu $[-2^{n-1},2^{n-1}-1]$
* liczba $-2^{n-1}$ nie ma liczby przeciwnej w $n$-bitowej reprezentacji kodu U2
* gdy $a$ liczbą w U2 to $l_{(10)}=a_{n-1}*-2^{n-1}+\sum_{i=n-2}^0 a_i2^i$
 ![Przykład U2](/src/img/podstawy/calkowita_ex.png)
* zmiana liczby U2 na przeciwną
  * inwersja bitów
  * dodanie 1
### Liczby rzeczywiste

* w sposób zmiennopozycyjny
## 7. Typ, zmienna, obiekt i zarządzanie pamięcią.
...
## 8. Instrukcje sterujące przepływem programu. 

**Instrukcja sterująca** — instrukcja zdefiniowana w składni określonego języka programowania, umożliwiająca wyznaczenie i zmianę kolejności wykonania instrukcji zawartych w kodzie źródłowym.

### Możliwości wyznaczania kolejności wykonywania instrukcji

* wykonanie sekwencyjne
  * bloki, instrukcje blokowe
* wykonanie innej instrukcji niż następna
  * instrukcja skoku, instrukcja opuszczenia, instrukcja powrotu
* wykonanie warunkowe
  * instrukcja warunkowa, instrukcja wyboru
* powtarzanie wykonania instrukcji
  * instrukcja pętli, instrukcja kontynuacji


### Rodzaje instrukcji sterujących

* instrukcje proste
  * skoku
  * opuszczenia
  * kontynuacji
  * powrotu
* instrukcje strukturalne
  * złożone
    * blokowa — jedna z rodzajów instrukcji blokowej
    * grupująca — jedna z rodzajów instrukcji blokowej
    * wiążąca — służy do uproszczeniu zapisu instrukcji odwołań do pól rekordu (struktury) lub pól i metod obiektu
  * warunkowe, rozgałęzienia
    * warunkowa
    * wyboru
  * pętli
    * iteracyjna — określona ilość iteracji
    * repetycyjna (warunkowa) — wykonanie kolejnej iteracji uzależnione jest od pewnego, zdefiniowanego przez programistę warunku
    * ogólna — jawnie zdefiniowany warunek zakończenia pętli, jawne zwiększanie lub zmniejszanie zmiennej sterującej
    * nieskończona
    * inne