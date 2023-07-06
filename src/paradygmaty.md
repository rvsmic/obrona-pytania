# Paradygmaty programowania
[`back to README.md`](../README.md)
## 48. Główne paradygmaty programowania – charakterystyka i przykłady

**Paradygmat** — przyjęty sposób widzenia rzeczywistości w danej dziedzinie, doktrynie

**Paradygmat programowania** — wzorzec, teoria, metodologia; na początku determinowany przez architekturę komputera, później przez kompilator

### Podstawowy podział

* imperatywny
  * ściśle opary na architekturze von Neumanna
  * zmiana stanu programu wraz z kolejnymi krokami
  * struktury kontrolne programu określają kolejność wywołań instrukcji
  * programy przypominają instrukcję obsługi, czyli musimy znać metodę osiągnięcia celu (algorytm prowadzący od danych do wyniku)
    * strukturalny
      * bazuje na strukturze kodu (bloki)
      * brak instrukcji skoku `goto`
      * kod jest czystszy i łatwiejszy do analizy
      * program wykonywany po kolei (za wyjątkiem pętli)
    * proceduralny — odmiana strukturalnego
      * część kodu zestawiana w podprogramy (procedury, funkcje)
      * podprogramy mogą być wywoływane wielokrotnie z głównego programu lub innych podprogramów
    * obiektowy
      * definiuje się metody działania na klasach danych, nie pojedynczych instancjach
      * przynależność do klasy, a więc właściwości, obiekt dziedziczy hierarchicznie
* deklaratywny
  * wzorowany na językach naturalnych i ludzkich procesach myślowych
  * nieliniowość wykonania, komenda na końcu kodu może zmodyfikować wywołanie z jego początku
  * powszechne stosowanie rekurencji w miejsce pętli
  * definiuje problem (dane i reguły) i poszukuje odpowiedzi na zadane pytanie
    * funkcyjne
      * zamiast instrukcji używa się wyrażeń, więc brak pojęcia stanu programu
      * cały algorytm sprowadza się do obliczenia wartości pewnej (zazwyczaj złożonej) funkcji matematycznej
      * u podstaw programowania funkcyjnego leży rachunek lambda
    * w logice
      * zamiast instrukcji zdania logiczne
      * każde działanie sprowadza się do określenia, czy dane stwierdzenie jest prawdziwy, czy nie

### Obecnie

Obecnie wyróżnia się cztery główne paradygmaty, często traktowane jako
niezależne:

* imperatywny
  * powiązany z koncepcją maszyny von Neumanna
  * polega na wydaniu sekwencji uszeregowanych czasowo rozkazów, zmieniających stan maszyny (stan jej procesora, zawartość pamięci i rejestrów)
  * języki niskiego poziomu (asemblery) operują niemal bezpośrednio na jednostkach pamięci
  * języki wysokiego poziomu wprowadzają twory abstrakcyjne reprezentujące składowe maszyny, np. zmienne reprezentują jednostki pamięci
  * języki czysto imperatywne: C, Pascal, Fortran, Basic, asemblery
* obiektowy
  * z rodziny imperatywnej, więc struktura i logika kodu taka sama
  * zmiana na poziomie struktury danych — dane grupowane z operacjami, które można na nich wykonać, powstaje w ten sposób obiekt
  * hermetyzacja, interfejsy, dziedziczenie, polimorfizm dynamiczny, abstrakcja danych, klasa, obiekt, klara potomna, macierzysta, metoda, pole, komunikat (wywołanie metody), protokół obiektu (zbiór sposobów odwołania się do obiektu)
  * jeśli nie wykorzystuje się obiektów, język obiektywny nie do odróżnienia od języka czysto imperatywnego
  * języki obiektowe: C++, Java, C#, Python, Ruby, Delphi/Object Pascal, Ada, ...
* funkcyjny
  * Haskell
* w logice
  * Prolog

Większość języków (niemal wszystkie nowoczesne) jest hybrydowa i nie podlega dokładnie pod tylko jeden paradygmat.

## 49. Gramatyki bezkontekstowe – definicje, charakterystyki i przykłady

**Gramatyka** — gramatyka formalna, w której wszystkie reguły wyprowadzania wyrażeń są postaci:
$$A\rightarrow \Gamma$$
gdzie:

* $A$ — symbol nieterminalny
* $\Gamma$ — dowolny ciąg symboli terminalnych i nieterminalnych (może być pusty)

Każdy język bezkontekstowy generowany jest przez pewną gramatykę bezkontekstową.

**Gramatyka bezkontekstowa G** — czwórka **G = (V,T,P,S)**, gdzie:

* **V** — **zbiór zmiennych**  — każda zmienna jest tożsama z jednym językiem; jedna ze zmiennych jest wyróżniona odpowiadając symbolowi początkowemu S, reszta to pomocnicze klasy łańcuchów
* **T** — **zbiór symboli końcowych** — niepusty zbiór skończony, zawierający łańcuchy definiowanego języka
* **P** — **zbiór produkcji** — skończony zbiór reguł pozwalających na rekurencyjne zdefiniowanie języka
  * produkcja — para $(A,\Gamma)$, czyli reguła postaci $A\rightarrow\Gamma$, gdzie $A\in V$, $\Gamma\in (T\cup V)^*$
  * inaczej produkcja regułą typu
    $$GŁOWA \rightarrow CIAŁO$$
    gdzie:
    * $GŁOWA$ — zmienna definiowana przez daną produkcję
    * $CIAŁO$ — to $\varepsilon$ lub łańcuch utworzony ze zmiennych i terminali
  * Cała reguła określa sposób tworzenia łańcuchów w języku
reprezentowanym przez zmienną będącą głową.
* **S** — **symbol początkowy**

Można to zapisać w sposób zwarty:

* $T \neq\empty$
* $S\in V$
* $T \cap V=\empty$
* $P\subset V\times (T\cup V)^*$

### Gramatyka

* operuje na więcej niż jednym języku, a więc odpowiada jej cały zestaw automatów lub pojedynczy automat złożony
* wyrażenia regularne (RE) spełniają rolę wzorców łańcuchów akceptowanych przez ten automat
* produkcje wykorzystują RE do określania reguł budowania akceptowanych łańcuchów

### Przykład

Gramatyka opisująca liczby parzyste w zapisie binarnym:

G = (V,T,P,S) = $(\{lparz\}, \{0,1\}, \{lparz\rightarrow0\ lparz,  lparz\rightarrow1\ lparz, lparz \rightarrow 0\}, lparz)$

Do definiowania gramatyk używa się najczęściej wyprowadzeń, czyli produkcji w kierunku $GŁOWA \rightarrow CIAŁO$. Można też używać wnioskowania rekurencyjnego, tj. odwrócić kierunek produkcji $GŁOWA \leftarrow CIAŁO$.

Rodzaje wyprowadzeń:

* lewostronne — budowanie wyrażeń od lewj do prawej, pierwsza zmienna od lewej zastępowana jednym z ciał jej produkcji
* prawostronne — budowanie wyrażeń od prawej do lewej, pierwsza zmienna od prawej zastępowana jednym z ciał jej produkcji

Poniższe procedury rozstrzygające, czy łańcuch końcowy w należy do języka zmiennej A są sobie równoważne:

* wnioskowanie rekurencyjne
* uogólnione wyprowadzenie $A \Rightarrow^*_G w$
* uogólnione wyprowadzenie lewostronne $A \Rightarrow^*_{G,l} w$
* uogólnione wyprowadzenie prawostronne A$A \Rightarrow^*_{G,p} w$
* konstrukcja drzewa wyprowadzenia o korzeniu $A$ i łańcuchu wynikowym $\omega$

![Gramatyka bezkontekstowa](/src/img/paradygmaty/gram_bezkont_1.png)
![Wyprowadzenie lewostronne](/src/img/paradygmaty/wyprowadzenie_lewostr.png)
![drzewo wyprowadzeń](/src/img/paradygmaty/drzewo_wypr.png)

## 50. Analiza leksykalna, syntaktyczna i semantyczna kodu

### Typowy schemat kompilacji

![Typowy schemat kompilacji](/src/img/paradygmaty/schemat_kompilacji.png)
![analizy](/src/img/paradygmaty/analizy.png)

### Analiza leksykalna

* wykonywana przez **skaner** (inaczej analizator leksykalny zazwyczaj posługuje się językiem regularnym, w którym alfabetem są znaki używane do zapisania kodu)
* wykonywana na podstawie reguł, które do skanera dostarczone są z zewnątrz
* polega na analizie kodu i klasyfikacji poszczególnych łańcuchów znaków za pomocą znaczników („tokenizacja kodu”); tokeny to zmienne późniejszej gramatyki
* skaner tworzy plik z rozbiorem leksykalnym analizowanego kodu, który staje się jednym z plików wejściowych dla parsera
* w linuksie używany jest flex (fast lexical analyser generator), kompatybilny z leciwym już programem lex
![skaner](/src/img/paradygmaty/skaner.png)

### Analiza syntaktyczna

* wykonywana przez parser (generator parserów)
* opiera się na regułach parsera oraz pliku z danymi pochodzącymi od skanera
* reguły parsera to produkcje gramatyki zdefiniowane na tych samych tokenach, które były używane w regułach skanera
* parser tworzy pełną gramatykę (w postaci drzewa wyprowadzeń, tu nazywanym drzewem parsowania)
* w linuksie parser (funkcję parsującą) generuje bison, następca programu yacc (parser generator)
* generator parserów działa w oparciu o język bezkontekstowy, zdefiniowany na tokenach wygenerowanych wcześniej przez skaner.

![Parser](/src/img/paradygmaty/parser.png)

### Analiza semantyczna

* analiza znaczeniowa, czyli przypisanie do abstrakcyjnych tworów opisywanych tokenami (zmiennymi gramatyki) takimi jak wyrażenie, etykieta, zmienna, operator itd. konkretnych wartości
* analizowany jest kod pośredni generowany przez skaner i parser
* zajmuje się tym część kompilatora
* sprawdzane są zgodności typów zmiennych
* wyszukiwane są takie same etykiety w programie i twory im przypisane są utożsamiane
* analizowane są pętle i rekurencje
* generowane komunikaty o błędach
* tworzony jest nowy kod pośredni

![Analiza semantyczna](/src/img/paradygmaty/analiza_sematyczna.png)

## 51. Rodzaje błędów w kontekście analizy leksykalnej, syntaktycznej i semantycznej kodu

* **leksykalne** (słownikowe) – pomylone identyfikatory zmiennych, słów kluczowych, brak cudzysłowów
* **syntaktyczne** (składniowe) – brak znaków specjalnych (przecinek, kropka, średnik), niedomknięte nawiasy, niedokończone struktury blokowe (if...then...fi, begin...end)
* **semantyczne** (znaczeniowe) – zazwyczaj jest to niezgodność typów, czyli użycie czegoś w kontekście, w którym to coś nie ma sensu (np.operacja na liście wykonywana na zmiennej napisowej)

Dodatkowo:

* **logiczne** – błędy programisty, który koduje nie to, co zamierza, np. używa operatora porównania == zamiast przypisania =
* **algorytmiczne** – błędy programisty, który używa niepoprawnego algorytmu

## 52. Deklaratywne programowanie funkcyjne: rachunek lambda, monady

### Rachunek lambda

**Rachunek lambda** — reguły składania i wykonywania obliczeń, w których podstawowym elementem składowym jest funkcja.

Dwa podejścia:

* **funkcje jako grafy** – odwzorowanie wejścia na wyjście (podejście nowoczesne) – dwie funkcje są tożsame, jeśli dla danego wejścia dają równe sobie wyjścia
* **funkcje jako reguły** – dane najczęściej wzorem – dwie funkcje są tożsame, jeśli wykonują na wejściu równoważne sobie operacje (co skutkuje równym sobie wynikom, ale teraz nie tylko wynik, ale sposób jego otrzymania jest brany pod uwagę)

![Przykładowa lambda](/src/img/paradygmaty/lambda.png)

* można opuścić kropkę ($\lambda x.M$ równoważne $λxM$)
* funkcję kilku zmiennych $\lambda x(\lambda y(\dots (\lambda zM)\dots ))$ zapisuje się krócej jako $\lambda xy\dots z.M$
* dla złożenie kilku wyrażeń zakłada się łączność lewostronną (tzn. $MNK$ jest równoważne $(MN)K$)
* przykład
  * złożenie $f\circ f$ funkcji kwadratowej $f(x)=x^2$ dla $x=5$ $(\lambda f.\lambda x.f(f(x)))(\lambda y.y^2)(5)=625$
* NApisy w rachunku lambda to termy należące do zbioru $\Lambda$, który konstruuje się z pewnego przeliczalnego zbioru zmiennych $Var$ jako zbió© słów nad alfabetem $\sum =Var\cup \{(,)\lambda \}$
  * Typy termów
    * zmienna $x\in Var\Rightarrow x\in\Lambda$
    * lambda-abstrakcja $\lambda x.M\in\Lambda$ dla dowolnych $x\in Var$ i $M\in\Lambda$
    * aplikacja $(MN)\in \Lambda$ dla dowolnych $M,N\in\Lambda$
  
### Monady

* pozwala na zdefiniowanie reguł składania funkcji o częściowo niezgodnych typach
* pozwala na zdefiniowanie reguł przekazywania wartości funkcji na wejście innej funkcji
* rozwiązuje tym samym problem: funkcją, która ma robić kilka rzeczy (np. obliczać wartość i wypisywać dane na ekranie), jako czysta funkcja nie może generować efektów ubocznych, więc w takich sytuacjach efekt ten musi być częścią zwracanej wartości i ten problem rozwiązują monady
  * w Haskellu
    * `>>=` jest funkcją wiążącą instancje monady z obliczeniami
    * `>>` operator analogiczny do `>>=`, ale nie wykorzystujący wyniku poprzedniej operacji
    * Monada `Maybe`
    * `return`, `do ... return`
* Praktyczne zastosowanie
  * funkcje wieloargumentowe są rozbijane na jednoelementowe i sklejane razem
  
    `plus x y = \x -> (\y -> x + y)`
  * listy są tworami o nieustalonej z góry długości, być może puste, więc monada typu List pozwala na definiowanie obliczeń mogących zwracać 0, 1 lub więcej wartości
  * operacje I/O są obsługiwane w Haskellu poprzez odpowiednią monadę, ponieważ są to najczęściej efekty uboczne działania funkcji (właściwe obliczenia plus operacja I/O)
  * obsługa błędów

## 53. Deklaratywne programowanie w logice: klauzule Horne'a, nawracanie

### Klauzule Horne'a

**klauzula Horne'a** — wyrażenie logiczne, w którym co najwyżej jeden człon nie jest zanegowany

Ogólna postać klauzuli Horna: $\overline{p_1}\lor\overline{p_2}\lor\overline{p_3}\lor q$, co można przeprowadzić do postaci równoważnej $(\overline{p_1}\lor\overline{p_2}\lor\overline{p_3}\lor q) \iff (\overline{p_1}\land\overline{p_2}\land\overline{p_3} \Rightarrow q)$.

W prologu klauzule Horne'a są zapisywane w postaci:
`q:-p1,p2,p3.` co znaczy 'q jest prawdziwe, jeśli p1, p2 i p3 są prawdziwe'.

### Nawracanie

**Nawracanie** (backtracing) — — cofnięcie się i przyjęcie innej strategii uzgadniania rozwiązanie problemu. Zdarza się, że cel może zostać spełniony na więcej niż jeden sposób. Gdy zachodzi konieczność wybrania jednej z wielu możliwości, Prolog wybiera pierwszą z nich (w kolejności występowania w pliku) i zapamiętuje miejsce, w którym wybór ten został dokonany. Jeśli w jakimś momencie nie powiedzie się próba obliczenia celu, system ma możliwość powrócenia do miejsca ostatnio dokonanego wyboru i zastąpienia go wyborem alternatywnym. Ten sam mechanizm działa też, gdy cel zostanie obliczony, pozwala wtedy znaleźć alternatywne rozwiązania.
