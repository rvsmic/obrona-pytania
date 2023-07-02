# Matematyka
[`back to README.md`](../README.md)
## 1. Wektory i macierze – definicje i podstawowe operacje. 
Fajny wzór w latex: $a^2 + b^2 = c^2$ 
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
## 2.  Funkcje skrótu (mieszające) i ich zastosowania. 
...
## 3. Problemy rekurencyjne i ich rozwiązywanie. 
...
## 4. Podstawowe charakterystyki statystyki opisowej i matematycznej. 
