# Matematyka
[`back to README.md`](../README.md)
## 1. Wektory i macierze – definicje i podstawowe operacje.

### Wektor

Obiekt matematyczny opisywany za pomocą wielkości:

* modułu (nazywanego też – zdaniem niektórych niepoprawnie – długością lub wartością),
* kierunku,
* zwrotu (określającym orientację wzdłuż danego kierunku)
  ![wektor](/src/img/matematyka/wektor.png)

Przestrzeń euklidesowa — przestrzeń opisywana przez geomotrię euklidesową. Jednowymiarową przestrzeń euklidesową nazywa się prostą euklidesową, a dwuwymiarową – płaszczyzną euklidesową. Przestrzenie euklidesowe nazywa się również afinicznymi przestrzeniami euklidesowymi, w odróżnieniu od liniowych przestrzeni euklidesowych, nazywanych też przestrzeniami unitarnymi.

W przestrzeni euklidesowej wektory można rozumieć dwojako:

* wektory zaczepione — dowolne odcinki (kierunek i moduł) z wyróżnioną kolejnością punktów końcowych (zwrot);
* wektory swobodne — sam kierunek wraz ze zwrotem oraz modułem, przy czym punkt początkowy (zaczepienia) nie jest istotny.

#### Własności wektorów w układzie współrzędnych kartezjańskich z wektorami bazowymi $\vec{e}_1=(1,0,0),\ \vec{e}_2=(0,1,0),\ \vec{e}_3=(0,0,1)$

$a= \alpha_1 \vec{e}_1 + \alpha_2 \vec{e}_2 + \alpha_3 \vec{e}_3$

* równość — dwa wektory są równe, jeżeli mają równe wartości i kierunki (wraz ze zwrotami); odpowiadające współrzędne tych wektorów będą równe:

  Wektor $\vec{a}=(a_1,b_1,c_1)$ jest równy wektorowi $\vec{b}=(a_2,b_2,c_2)$, jeżeli $a_1=a_2$, $b_1=b_2$ i $c_1=c_2$.

* suma:
  
  $\vec{a}=(a_1,b_1,c_1)$ i $\vec{b}=(a_2,b_2,c_2)$ jest równa wektorowi $\vec{c}=(a_1+a_2,b_1+b_2,c_1+c_2)$
* różnica:
  
 $\vec{a}=(a_1,b_1,c_1)$ i $\vec{b}=(a_2,b_2,c_2)$ jest równa wektorowi $\vec{c}=(a_1-a_2,b_1-b_2,c_1-c_2)$

* mnożenie przez skalar:
  
  $\vec{a}=(a_1,b_1,c_1)$ i $\alpha$ jest równa wektorowi $\vec{c}=(\alpha a_1,\alpha b_1,\alpha c_1)$
* długość, moduł, norma $||\vec{a}||$ — długość wektora $\vec{a}$, równa pierwiastkowi kwadratowemu sumy kwadratów jego współrzędnych:
  
  $||\vec{a}|| = \sqrt{a_1^2 + a_2^2 + a_3^2}$
  
  lub erwiastkowi kwadratowemu z iloczynu skalarnego wektora przez siebie:

  $||\vec{a}|| = \sqrt{\vec{a} \cdot \vec{a}}$
* iloczyn skalarny (iloczyn wewnętrzny) — wynikiem skalar

  $\vec{a} \cdot \vec{b} = ||\vec{a}|| \cdot ||\vec{b}|| \cdot cos \theta$

  gdzie $\theta$ jest kątem między wektorami $\vec{a}$ i $\vec{b}$.
* iloczyn wektorowy (iloczyn zewnętrzny) — ma sens jedynie w 3 wymiarach; wynikiem wektor
  
  $\vec{a} \times \vec{b} = ||\vec{a}||||\vec{b}||sin\theta\ \vec{n}$

  gdzie $\vec{n}$ jest wektorem jednostkowym prostopadłym do płaszczyzny wyznaczonej przez wektory $\vec{a}$ i $\vec{b}$, który uzupełnia układ prawoskrętny (reguła prawj dłoni).
  ![reguła prawej dłoni](/src/img/matematyka/regula_prawej_dloni.png)
  $\vec{a} \times \vec{b}=(a_2b_3-a_3b_2)e_1+(a_3b_1-a_1b_3)e_2+(a_1b_2-a_2b_1)e_3$
  * jeżeli wektory $\vec{a}$ i $\vec{b}$ są współliniowe, to ich iloczyn wektorowy jest równy zerowemu wektorowi
  * własności
    * antyprzemienność: $\vec{a} \times \vec{b} = -\vec{b} \times \vec{a}$
    * rozdzielność względem dodawania: $\vec{a} \times (\vec{b} + \vec{c}) = \vec{a} \times \vec{b} + \vec{a} \times \vec{c}$
    * zgodność z mnożeniem przez skalar: $(\alpha \vec{a}) \times \vec{b} = \alpha (\vec{a} \times \vec{b}) = \vec{a} \times (\alpha \vec{b})$
  
* wektor jednostkowy, wersor — wektor o długości 1, wskazujący kierunek i zwrot wektora $\vec{a}$, (normalizacja — przekształcenie wektora $\vec{a}$ w wektor jednostkowy):

  $\vec{e}=\frac{\vec{a}}{||\vec{a}||}$
* wektor zerowy — o długości 0

### Macierz

W matematyce macierz to układ liczb, symboli lub wyrażeń zapisanych w postaci prostokątnej tablicy.

W algebrze liniowej macierze wprowadza się często jako sposób skondensowanego zapisu układów równań liniowych, co ma na celu wyeliminowanie powtarzających się elementów standardowej notacji układów równań tego rodzaju z wieloma niewiadomymi.

![przykładowa macierz](/src/img/matematyka/macierz_ex.png)
Macierz składająca się elementów rozmieszczonych w $m$ poziomych wierszach i $n$ pionowych kolumnach: element w drugim wierszu i pierwszej kolumnie macierzy oznaczony jest symbolem $a_{21}$.

Dane wpisane w macierz nazywa się jej elementami, współczynnikami lub wyrazami; każdy element można jednoznacznie zidentyfikować, podając jego wskaźniki lub indeksy – zwykle w tej kolejności: numer wiersza i kolumny macierzy, w której stoi. Para złożona z liczby wierszy i kolumn nazywana jest typem macierzy – często liczby te oddziela się znakiem $\times$.

#### Rodzaje macierzy:

* kwadratowa – macierz, której liczba wierszy jest równa liczbie kolumn ($n\times n$); w macierzy kwadratowej:
  * stopień macierzy — ilczba wierszy (kolumn)
  * główna przekątna (główną diagonalą lub często po prostu przekątną bądź diagonalą) — ciąg elementów o równych wskaźnikach wiersza i kolumny ($a_{11}, a_{22}, \dots, a_{nn}$)
  * przekątne leżące nad lub pod główną przekątną nazywa się odpowiednio nadprzekątną lub podprzekątną macierzy
  * przekątną, której wiersz rośnie od pierwszego do ostatniego, a kolumna maleje od ostatniej do pierwszej nazywa czasem przeciwprzekątną lub antyprzekątną ($a_{1n}, a_{2,n-1}, \dots, a_{n1}$)
* prostokątne – macierz, której liczba wierszy jest różna od liczby kolumn ($m\times n$).

#### Oznaczenia macierzy:

* podmacierz macierzy — dowolny zbiór elementów macierzy powstały po skreśleniu pewnej liczby wierszy i kolumn
  * podmacierze główne — są to podmacierze kwadratowe zawierające pewną liczbę początkowych wyrazów głównej przekątnej
* Macierz klatkowa to macierz, w której wprowadzono podział elementów na grupy kolejnych wierszy i kolumn – obrazowo czyni się to, prowadząc poziome i pionowe linie między wierszami i kolumnami macierzy, dzieląc ją na podmacierze nazywane klatkami

  ![macierz klatkowa](/src/img/matematyka/macierz_klatkowa.png)

#### Operacje na macierzach: 

* równość macierzy – macierze są równe, gdy mają takie same wymiary (ten sam typ) i odpowiadające sobie elementy są równe
  $$A = B \Leftrightarrow a_{ij} = b_{ij}\ \forall{i,j}$$ 
  przy założeniu, że typy obu macierzy są takie same
* dodawanie macierzy — macierze muszą być tego samego typu
  $$A+B = C \Leftrightarrow c_{ij} = a_{ij} + b_{ij}\ \forall{i,j}$$
  przy założeniu, że typy obu macierzy są takie same
* mnożenie przez skalar
  $$cA=B \Leftrightarrow b_{ij} = ca_{ij}\ \forall{i,j}$$
   przy założeniu, że typy obu macierzy są takie same
* mnożenie macierzy (iloczyn Cauchy’ego)
  * dla $A$ typu $m\times n$\, i $B$ typu $n\times p$ iloczynem $AB$ jest macierz $C$ typu $m\times p$ o elementach $c_{ij}$ zdefiniowanych wzorem:
  $$AB = C \Leftrightarrow c_{ij} = \sum_{k=1}^n a_{ik}b_{kj}\ \forall{i,j}$$
  * mnożenie jest  łączne, ale nie przemienne
  * obustronnie rozdzielne względem dodawania
  * zgodne z mnożeniem przez skalar
  ![iloczyn macierzy](/src/img/matematyka/iloczyn.png)
* przestawienie/transpozycja macierzy – zamiana jej kolumn i wierszy miejscami (z zachowaniem kolejności)
  * $(AB)^T=A^TB^T$
  * ${(A^T)}^T = A$
* operacje elementarne:
  * zamiana miejscami dwóch wierszy
  * przemnożenie jednego wiersza przez skalar różny od 0
  * dodanie do jednego wiersza innego wiersza macierzy
  * **Macierz elementarna** to macierz powstała z macierzy jednostkowej przez wykonanie jednej z operacji elementarnych. 
  * Podobnie definiuje się operacje elementarne na kolumnach macierzy.

Macierz jednostkowa:
![macierz jednostkowa](/src/img/matematyka/macierz_jednostkowa.png)

#### Macierze kwadratowe

* macierz diagonalna – macierz kwadratowa, której wszystkie elementy poza główną przekątną są zerami; często zapisuje się jako $diag(a_{11}, a_{22}, \dots, a_{nn})$, gdzie $n$ to stopień macierzy
* macierz dolnotrójkątna (górnotrójkątna) – macierz kwadratowa, której wszystkie elementy nad (pod) główną przekątną są zerami
* macierz trójkątna – macierz dolnotrójkątna lub górnotrójkątna
* macierz unitrójkątna (jednostkowa)— macierz trójkątna, której elementy na głównej przekątnej są równe 1
* macierz symetryczna – macierz kwadratowa, której elementy spełniają warunek $a_{ij} = a_{ji}\ \forall{i,j}$
* macierz skalarna – macierz diagonalna, której wszystkie elementy na głównej przekątnej są równe $diag(a,a,a,\dots,a)$
  * I = $diag(1,1,1,\dots,1)$ — macierz jednostkowa
  * $AB=BA=I$ — $B$ jest macierzą odwrotną do $A$ i oznacza się ją $A^{-1}$, o macierzy $A$ mówi się wtedy, że jest odwracalna
* wyznacznik macierzy
  * $det(A)$ — wyznacznik macierzy $A$
  * gdy $det(A)=0$ to macierz $A$ jest osobliwa (nieodwracalna)
  * macierz jest odwracalna wtedy i tylko wtedy,
    * gdy jej wyznacznik jest różny od zera — czyli jest nieosobliwa
    * rząd macierzy jest maksymalny czyli równy stopniowi macierzy
  * $det(AB)=det(A)det(B)$
  * oblicznie
    * macierz 2 stopnia ![def_2_st](/src/img/matematyka/det_2_st.png)
    * macierz 3 stopnia — reguła Sarrusa 
    * macierz $n \geq 2$ stopnia — rozwinięcie Laplace’a — pozwala sprowadzić oblicznie wyznacznika stopnia $n$ do obliczenia $n$ wyznaczników stopnia $n-1$. Rozwijać można względem dowolnego wiersza lub kolumny.
      * Niech $A=[a_{ij}] \in M_{n}(K)$ wtedy
        * $det A =\sum_{i=0}^{n}(-1)^{i+j}a_{ij}M{ij}$ — rozwienięcie względem j-tej kolumny
        * $det A =\sum_{j=0}^{n}(-1)^{i+j}a_{ij}M{ij}$ — rozwienięcie względem i-tego wiersza
  
        gdzie $M_{ij}$ jest minorem macierzy $A$ odpowiadającym elementowi $a_{ij}$ , tj. wyznacznikiem macierzy stopnia $n − 1$ powstaaej z macierzy $A$ w wyniku wykreślenia i-tego wiersza i j-tej kolumny.

## 2.  Funkcje skrótu (mieszające) i ich zastosowania.

Funkcja skrótu, funkcja mieszająca lub funkcja haszująca – funkcja przyporządkowująca dowolnie dużej liczbie krótką wartość o stałym rozmiarze, tzw. skrót nieodwracalny.

### Zastosowania

* weryfikacja integralności/spójności danych
* większość algorytmów podpisu cyfrowego działa na zasadzie wygenerowania skrótu wiadomości
* do weryfikacji haseł
* identyfikacja plików — systemy kontorli wersji takie jak Git czy Mercurial używają funkcji skrótu SHA do identyfikacji różnego rodzaju zawartości
* do ustalenia krótkich i łatwych do weryfikacji sygnatur dla dowolnie dużych zbiorów danych. Sygnatury mogą:
  * chronić przed przypadkowymi lub celowo wprowadzonymi modyfikacjami danych (sumy kontrolne),
  * przy optymalizacji dostępu do struktur danych w programach komputerowych (tablice mieszające/z haszowaniem).

### Kryteria kryptograficznej funkcji skrótu w zależności od zastosowania

* odporność na kolizje — brak praktycznej możliwości wygenerowania dwóch dowolnych wiadomości o takim samym skrócie
* odporność na kolizje konkretnych wiadomości pierwszego i drugiego rzedu — brak praktycznej możliwości wygenerowania wiadomości o takim samym skrócie jak wskazana wiadomość
* jednokierunkowość —  brak możliwości wnioskowania o wiadomości wejściowej na podstawie wartości skrótu

Dodatkowo w niektórych zastosowaniach wymagane:

* pseudolosowość
* uwierzytelnienia wiadomości
* niemożności odróżnienia od losowej wyroczni – uczynienie niemożliwym do znalezienia dla przeciwnika dwóch wiadomości, dla których wartości funkcji skrótu nieznacznie się różnią

### Przykładowe funkcje i algorytmy

* SHA
* MD5
  
## 3. Problemy rekurencyjne i ich rozwiązywanie.

**Rekurencja, rekursja** — odwoływanie się funkcji lub definicji do samej siebie.

**Rekurencja ogonowa** — rodzaj rekurencji, w której ostatnia operacja wykonywana przez funkcję to rekurencyjne wywołanie samej siebie lub zwrócenie końcowego wyniku

### Przykłady

* ciąg Fibonacciego
$$
F_n=
\begin{cases}
0 & \quad \text{dla  }n=0\\
1 & \quad \text{dla  }n=1\\
F_{n-2}+F_{n-1} & \quad \text{dla }n>1
\end{cases}
$$
* definicja silni
$$
F_n=
\begin{cases}
1 & \quad \text{dla  }n=0\\
nF_{n-1} & \quad \text{dla }n\geq1
\end{cases}
$$
* funkcja Ackermanna
$$
A(m,n)=
\begin{cases}
n+1 & \quad \text{dla  }m=0\\
A(m-1,1) & \quad \text{dla  }m>0\ i\ n=1\\
A(m-1,A(m,n-1)) & \quad \text{dla }m>0\ i\ n>0
\end{cases}
$$

## 4. Podstawowe charakterystyki statystyki opisowej i matematycznej.

### Statystyka opisowa

Dział statystyki zajmujący się metodami opisu danych statystycznych uzyskanych podczas badania statystycznego. Celem stosowania metod statystyki opisowej jest podsumowanie zbioru danych i wyciągnięcie pewnych podstawowych wniosków i uogólnień na temat zbioru.

#### Techniki stystyki opisowej

* opis tabelaryczny — dane w postaci tabel, różnego rodzaju podsumowania np. szereg rozdzielny
* graficzna reprezentacja wyników — np. w formie 
  * histogram, wielobok liczebności i krzywa liczebności — na podstawie danych z szeregu rozdzielczego
  * wykres Lorenza — koncentracja wartości cechu
* wyznaczanie miar rozkładu
  * miary położenie, np. kwantyl
    * w tym miery tendencji centralnej
      * średnia arytmetyczna
      * średnia geometryczna
      * średnia harmoniczna
      * średnia kwadratowa — pozwala oszacować rząd wielkości serii danych liczbowych lub funkcji ciągłej, użyteczny zwłaszcza w przypadku, gdy wielkości różnią się znakiem
      $$M2=\sqrt{\frac{a_1^2+\dots+a_n^2}{n}}$$
      * mediana — wartość środkowa
      * moda/dominanta — wskazuje na wartość o największym prawdopodobieństwie wystąpienia, lub wartość najczęściej występująca w próbie
  * miary zróżnicowania
    * odchylenie standardowe — miara zróżnicowania; jak szeroko watrości jakiejść wielkości rozrzucone wokół jej średniej; pierwiastek z wariancji
    * wariancja — miara zmienności zmiennej losowej będąca kwadratem różnicy wartości zmiennej losowej X i jej wartości oczekiwanej; W statystyce opisowej obliczana jest jako średnia arytmetyczna kwadratów odchyleń (różnic) poszczególnych wartości cechy od średniej
    * średnie odchylenie bezwzględne
    * współczynnik zamienności
  * miary asymertii
    * współczynnik skośności
    * współczynnik asymetrii
  * miary koncentracji
    * współczynnik Ginieg
    * kurtoza

### Statystyka matematyczna

Dział statystyki, używający teorii prawdopodobieństwa i innych działów matematyki do rozwijania statystyki z czysto matematycznego punktu widzenia. Zajmuje się metodami wnioskowania statystycznego, które polegają na tym, że na podstawie wyników uzyskanych z próby formułujemy wnioski o całej zbiorowości (populacji).

* Estymacja
* Weryfikacja hipotez — sprawdzanie sądów o populacji przez badanie jej wycinka
  * wnioskowanie częstościowe, z użyciem P-wartości 
  * iloraz wiarygodności – służące do rozstrzygnięcia, w jakiej proporcji dane świadczą na rzecz dwóch porównywanych hipotez
  * wnioskowanie bayesowskie, z użyciem czynnika Bayesa – służące do wyrażenia subiektywnej pewności, jaką można, na podstawie danych i wcześniejszych oczekiwań, przypisać danej hipotezie