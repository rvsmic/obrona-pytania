# Systemy operacyjne

[`back to README.md`](../README.md)

## 23. Wielowarstwowa organizacja systemów komputerowych.

> Według wykładu profesora Łojewskiego, [wy2 2020/2021](https://drive.google.com/drive/folders/1l-LHcaOcwQoiGkw8m59UWU9ySmLEs_vf)

![warstwy](img/systemy-operacyjne/warstwy-systemu.png)

1. Sprzęt — procesor, pamięć, urządzenia wejścia/wyjścia
2. Jądro systemu — obsługuje sprzęt, ma w sobie sterowniki, które umożliwiają komunikację z urządzeniami, komunikuje się ze sprzętem w sposób bezpośredni
3. API — interfejs programowania aplikacji, umożliwia komunikację z jądrem systemu operacyjnego za pomocą funkcji jądra, w tym **powłoce** (shell)
4. Programy narzędziowe (systemowe) — w tym powłoka, są pierwszymi programami, które są uruchamiane po starcie systemu i umożliwiają komunikację z użytkownikiem (tutaj też jest interpreter poleceń, chyba)
5. Programy użytkowe — oprogramowanie, które jest używane przez użytkownika: gry, edytory, przeglądarki, itp.

Na przykładzie systemu Android:

* Linux Kernel Layer – warstwa jądra systemu operacyjnego oparta na Linuxie
* Native Libraries Layer – natywne biblioteki systemu Android
* Application Framework Layer – warstwa, z którą bezpośrednio komunikują się aplikacje min. zarządzanie oknami, zasobami itp.
* Application Layer – warstwa aplikacji, z którą w interakcję wchodzą użytkownicy, aby np. wykonać połączenie telefoniczne

**Najogólniej to system jest podzielony na jądro oraz programy systemowe (interpreter poleceń, powłoka, itp.).** Programy użytkowe są uruchamiane przez użytkownika, a programy systemowe są uruchamiane przez jądro systemu operacyjnego.

> Według wikipedii [system komputerowy](https://www.wikiwand.com/pl/System_komputerowy) i [system operacyjny](https://www.wikiwand.com/pl/System_operacyjny)

Na początek dwa obrazki z wikipedii:

![logiczne warstwy](https://upload.wikimedia.org/wikipedia/commons/1/18/Operating_system_placement-pl.svg)

Tutaj mamy podział na warstwy logiczne, które są zależne od siebie. System operacyjny pośredniczy między sprzętem a aplikacjami, które są używane przez użytkownika.

![Schemat](https://upload.wikimedia.org/wikipedia/commons/3/3e/System_operacyjny_schemat_ogolny.svg)

Tutaj mamy schemat, gdzie jądro zawiera w sobie sterowniki, które umożliwiają komunikację z urządzeniami. Jądro jest częścią systemu operacyjnego, a system operacyjny jest częścią systemu komputerowego. Powłoka umożliwia użytkownikowi komunikację z jądrem.

Wikipedia wyszczególnia 5 warstw systemu komputerowego:

1. Sprzęt — procesor, pamięć, urządzenia wejścia/wyjścia, sa to podstawowe zasoby systemu komputerowego
2. Oprogramowanie systemowe — kontroluje i koordynuje sprzęt, 
3. Oprogramowanie narzędziowe — interfejsy zapewniające dostęp do zasobów systemu
4. Oprogramowanie użytkowe — oprogramowanie, które jest używane przez użytkownika: gry, edytory, przeglądarki, itp.
5. Użytkownik — człowiek, który używa systemu komputerowego, ale również inny system czy maszyna

## 24. System operacyjny – charakterystyka, zadania, klasyfikacja.

## 25. Procesy i wątki – charakterystyka i problemy.

## 26. Zarządzanie pamięcią operacyjną w systemie operacyjnym.

## 27. Organizacja systemu plików i pamięci zewnętrznej.

> Według jakiś prezek z neta
> <https://kcir.pwr.edu.pl/~witold/opsys/os_fsys_s.pdf>
> <http://edu.pjwstk.edu.pl/wyklady/sop/scb/wyklad9/>
> <https://www.wikiwand.com/pl/System_plik%C3%B3w>

Systam plików to metoda przechowywania, zarządznia i dostępu do plików. Przchowują one również infomacje o tych plikach. Systemy plików stosuje się na roznych mośnikach danych, takich jak dyski, pendrive'y, karty pamięci, itp. Nowoczene aplikacie uzywają sysrtemu plików, a nie bezpośrednio dysku.
Systamy plików są zależne od systemu operacyjnego, a nie od sprzętu.

Z wikipedii:

> Z formalnego punktu widzenia system plików to reguły umieszczania na nośniku abstrakcyjnych danych oraz informacji umożliwiających przechowywanie tych danych, łatwy i szybki dostęp do informacji o danych oraz do tych danych, manipulowania nimi, a także sposobach usuwania ich.

### Organizacja systemu plików

* Logiczna — rekordy o stałej lub zmiennej długości, rekordy są grupowane w pliki, pliki są grupowane w katalogi
* Fizyczna — zbiór bloków dyskowych. Zjawisko fragmentacji powoduje, że plik może być rozproszony na wielu blokach dyskowych

### Operajce na plikach

* tworzenie
* kasoowanie
* odczyt
* zapis

### Atrybuty plików

mogą to być:

* nazwa
* hasło
* typ
* twórca
* właściciel
* uprawnienia
* czas utworzenia
* flagi
  * tekstowy/binary
  * archiwum
  * ukrycia
* rozmiar
* ...
* flagi uniksowe:
  * r — odczyt
  * w — zapis
  * x — wykonanie
  * specjalne:
    * s — setuid
    * t — sticky bit
    *  ...

### Katalogi

Katalog służy do grupowania plików i innych katalogów. Katalogi mogą być zagnieżdżone. Katalogi mogą być puste. Katalogi mogą być ukryte. 

Czasami katalogi przyjmują strukturę:

* drzewa jedenopozionowego
* drzewa wielopozionowego
* grafu acyklicznego
* grafu spójnego
  
### Struktura logiczna/przydziału miejsca na dysku

* ciągły — plik zajmuje ciągły obszar dysku, jest zły bo trzeba znać rozmiar pliku, a jeśli plik jest za duży to nie można go zapisać
* listowy FAT — bloki tworzące plik są rozproszone na dysku, a w pliku jest lista bloków, które należą do pliku. Jest to dobre rozwiązanie, ale trzeba znać rozmiar listy, a jeśli lista jest za duża to nie można jej zapisać. Prostrza impelemntacja zakłada liste jednokierunkową, gdzie koniec jedenego fragmentu wskazuje na początek następnego fragmentu.
* wiele ciągłych obszarów — plik jest podzielony na wiele ciągłych obszarów, które są rozproszone na dysku. W pliku jest lista obszarów, które należą do pliku. **NTFS** używa tego rozwiązania.
* indeksowy — plik jest podzielony na wiele ciągłych obszarów, które są rozproszone na dysku. Bloki są  numerowane i zebrane do jedengo bloku, tzw, bloku indeksowanego. W bloku indeksowanym jest lista numerów bloków, które należą do pliku.

### Nośniki danych

Nośniki danych posiadają strukturę blokową (bloki są najmniejszymi jednostkami, które mogą być odczytywane i zapisywane (w całości)). W dyskach wiekość jednego bloku jest wielokrotnością wielkości sektora.

System operacyjny łączy bloki w klastry
