# Podstawowe informacje o programowaniu

[`back to README.md`](../README.md)

## 5. Pozycyjne systemy liczbowe i konwersje pomiędzy nimi

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

* Liczba zmiennoprzecinkowa – reprezentacja liczby rzeczywistej zapisanej za pomocą notacji naukowej.
* Konwersja (np. 12.75 do 32 bitowej liczby zmiennoprzecinkowej (1 bit znaku, 8 bitów wykładnika, 23 bity mantysy))
  * konwersja części całkowitej liczby na system binarny (12 -> 1100)
  * konwersja części ułamkowej liczby na system binarny (0.75 -> 0.11)
  * złączenie części całkowitej i ułamkowej (1100.11)
  * przesunięcie przecinka tak aby było 1.XXX (1100.11 = 1.10011 * 2^3)
  * znak = 0 bo liczba dodatnia
  * wykładnik = 3 + 127 = 130 = 10000010 (wykładnik + 127 na binarny)
  * mantysa = 10011000000000000000000 (przed przecinkiem zawsze 1 (pomija się) a reszta to część ułamkowa)

## 7. Typ, zmienna, obiekt i zarządzanie pamięcią

### Typ

**Typ** — definiuje jakie wartości może przyjmować zmienna, jaki rozmiar danych może być przechowywany.

* typ całkowity — np. `int` (4 bajty), `long long` (8 bajtów), `short` (2 bajty) w c++
* typ zmiennoprzecinkowy — np. `float` (4 bajty), `double` (8 bajtów) w c++
* typ znakowy — np. `char` (1 bajt) w c++
* typ tekstowy — np. `string`, `char *` w c++
* typ logiczny — np. `bool` (1 bajt) w c++
* typ wyliczeniowy — np. `enum` w c++
* typ złożony — np.
  * typ strukturalny — np. `struct` w c++
  * typ obiektowy (klasa) — `class` w c++
* typ pusty — np. `void` w c++ ?
* typ wskaźnikowy — np. `int *` w c++
* typ tablicowy — np. `int []` w c++
* typ referencyjny — np. `int &` w c++

### Zmienna

**Zmienna** — nazwany obszar pamięci komputera, który przechowuje wartość określonego typu.

* zmienna globalna — zmienna zdefiniowana w obrębie całego programu
* zmienna lokalna — zmienna zdefiniowana w obrębie bloku
* zmienna stała — zmienna, której wartość nie może być zmieniona po zainicjowaniu

### Obiekt

**Obiekt** — zmienna, która jest instancją klasy. Jest strukturą danych, która zawiera w sobie dane oraz metody, które mogą być wywoływane na tych danych.

### Zarządzanie pamięcią

**Zarządzanie pamięcią** — głównym zadaniem jest dostarczenie możliwości dynamicznego alokowania i zwalniania pamięci komputera.

* dynamiczna alokacja pamięci — na żądanie alokacji, znajdowany jest blok nieużywanej pamięci o określonym rozmiarze. Pamięć pochodzi z dużej puli pamięci zwanej stertą. W procesie alokacji pojawia się problem fragmentacji pamięci związany z występowaniem wielu małych bloków nieużywanej pamięci pomiędzy blokami zajętymi. Występuje wtedy scalenie wolnych bloków pamięci zwane  kompaktyfikacją lub upakowaniem
* sterta (kopiec, stóg, heap) — obszar pamięci implementujący strukturę danych o tej samej nazwie. Jest to obszar pamięci, z którego alokowane są dynamicznie obiekty. W języku C++ alokacja pamięci odbywa się za pomocą operatora `new`, a zwalnianie za pomocą operatora `delete`

* stos (stack) — liniowa struktura danych, w której dane dokładane są na wierzch stosu i z wierzchołka stosu są pobierane (bufor typu LIFO Last In First Out). Stosowany jest przez procesory do chwilowego zapamiętywania rejestrów procesora, do przechowywania zmiennych lokalnych, a także w programowaniu wysokopoziomowym. W C++ przechowuje zmienne lokalne, argumenty wywołania funkcji, wartość zwracana przez funkcję i adres wywołania funkcji (miejsce w kodzie).

## 8. Instrukcje sterujące przepływem programu

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
