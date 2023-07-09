# Inżynieria oprogramowania
[`back to README.md`](../README.md)
## 39. Standardowe metodyki procesu wytwórczego oprogramowania

Metodyka jest ustandaryzowanym dla wybranego obszaru wiedzy/nauki podejściem do rozwiązywania właściwych problemów. Metodyki abstrahują od merytorycznego kontekstu danego obszaru, a skupiają się na metodach realizacji zadań związanych z zarządzaniem projektem informatycznym.

### SDLC (Software Development Life Cycle) 
Ustandaryzowany zbiór procedur i procesów stosowany podczas rozwiązywania problemów wynikłych w trakcie projektowania i wdrażania oprogramowania traktowanego jako nieodłączna część określonego systemu informatycznego nazywamy metodyką rozwoju oprogramowania SDM (ang. Software Development Methodology) albo cyklem rozwoju systemów informatycznych SDLC (ang. System Development Life
Cycle).

![SDLC](/src/img/io/metodyki/sdlc.png)

### Model (proces) kaskadowy

W modelu kaskadowym fazy rozwoju oprogramowania następują sekwencyjnie, aby przejść do następnej poprzenia musi zostać zakończona. Nie ma możliwości powrotu do poprzedniej fazy — interpretacja ścisła (w interpretacji ogólnej na początku fazy $n+1$ można dokonać modyfikcaji na elementach fazy $n$).

* łatwo zarządza się projektem, ustala harmonogram, koszty i tworzy dokumentację
* wysoki koszt błędów, długa przerwa w kontakcie z klientem (między rozpoczęciem a oddaniem produktu)
![model kaskadowy](/src/img/io/metodyki/waterfall.png) 

### Model (proces) iteracyjny

* projektowaniei implementacja jedyne części pełnego produktu
* kroki procesu na przemian powtarzane — wiele razy przechodzimy przez każdy z tych etapów


![model iteracyjny](/src/img/io/metodyki/iteracyjny.png)

* koncepcja początkowa — wizja w formie zwięzłego opisu
* analiza — szczegółowy opis wymagań, zrozumienie dziedziny problemu
* projektowanie — przekształcenie wymagań w model, który może zostać zaimplementowany
* implementacja — tworzenie kodu
* testowanie — sprawdzenie czy produkt spełnia wymagania
* wdrożenie — dostarczenie produktu do klienta

### Model V

* każdy etap kończy się stworzenien danych wejścioych dla następnej fazy oraz odpowiadającej fazy testowania
* zaleca jak najwcześniejsze rozpoczęcie procesu tworzenia planów testów, specyfikacji testowej i samego testowania

![Model V](/src/img/io/metodyki/v.png)

### Realizacja iteracyjna i przyrostowa

* wybierany jest fragment funkcjonalności, który zostanie zaimplementowany, następuje projekt, implementacja i testowanie i w ten sposób powstaje część produktu, proces ten powtarzano aż do uzyskania pełnej funkcjonalności produktu

![Realizacja iteracyjna i przyrostowa](/src/img/io/metodyki/iret_przyr.png)

### Programowanie odkrywcze

* budowa systemu zaraz po określeniu wymagań
* jeżeli system nie działa poprawnie, budowana jest nowa wersja

![Programowanie odkrywcze](/src/img/io/metodyki/programowanie_odkrywcze.png)


### Prototypowanie

* gdy prototyp niewydolny to realizacja modelem kaskadowym
* ułatwia zrozumienie wymagań klienta
* wykrywa nieporozumienia z klientem, brakujące funkcje systemu, trudności w implementacji, braki w specyfiakcji wymagań
* możńa prowadzić szkolenie zanim zostanie stworzony pełny system
* budowanie prototypu jest dość kosztowne

![Prototypowanie](/src/img/io/metodyki/prototypowanie.png)

### GRAPPLE


* GRAPPLE (Guidlines for Rapid Application Engineering) 
* wykorzystano w niej wiele wcześniejszych idei projektowania aplikacji
* często utożsamiene z metodologią RAD (Rapid Application Development), co nie jest dość ścisłe

![Grapple](img/io/metodyki/grapple.png)

### Metodyka spiralna

* proces tworzenia oprogramowania ma postać spirali, której każda pętla reprezentuje jedną iterację procesu
* najbardziej wewnętrzna pętla przedstawia początkowe etapy projektowania, np. studium wykonalności, kolejna definicji wymagań systemowych, itd.

![Model spiralny](/src/img/io/metodyki/spiralny.png)

## 40. Metodyki zwinne – SCRUM

**Programowanie zwinne** (ang. agile software development) – zbiór metodologii tworzenia oprogramowania, które opierają się na iteracyjno-przyrostowym rozwoju produktu.

### SCRUM

**SCRUM** — iteracyjne i przyrostowe ramy zarządzania procesem produkcyjnym (ang. framework) zgodne ze Scrum Guide. Nie jest to metodyka zwinna, ale są to ramy postępowania (framework), nie ma "dwóch" zespołów pracujących w identycznym scrumie.

* może mieć zastowowani w realizacji procesów produkcyjnych w oparciu o metodyki zwinne

* fundamenty SCRUM:
    * **inspection** — inspekcja, uważne przyglądanie się rzeczywistości, np. potrzebom klienta
    * **adaptation** — adaptacja, na podstawie obserwacji podejmowane odpowiednie działania
    * **transparency** — przejrzystość, dzięki niej można podejmować decyzje na podstawie faktów (rzeczywistego a nie zafałszowanego obrazu rzeczywistości), a nie domysłów
* **Scrum Team**
    * samozarządzający sie zespół — organizacja stawia cel, zespół sam decyduje jak go osiągnąć
    * role w zespole:
        * **Product Owner** — właściciel produktu, osoba odpowiedzialna za wizję, wartość produktu i decyzje o kierunku rozwoju, odpowiada, żeby produkt był zgodny z wymaganiami klienta
        * **Scrum Master** — osoba odpowiedzialna za to, żeby zespół pracował produktywnie, pomaga zespołowi osiągnąć lepsze rezultaty
        * wykonawcy — osoby, które tworzą produkt
* działanie
    * zespól pracuje w **Sprintach** (iteracjach) o określonej długości (zwykle od 1 do 4 tygodni, zaleca się stosowanie sprintów stałej długości); zmiany w każdym Sprintcie powinny wnosić zauważalną nową wartość funkcjonalną 
    * na początku wszystko co jest do zrobienia jest umieszczane w **Product Backlog** (aktualizaowany i porządkowany przez Product Ownera)
    * następnie zespół planuje **Sprint** (planowanie podczas **Sprint Planning**, plan działania jest umieszczany w **Sprint Backlog**, do którego wszyscy mają dostęp — transparencja)
    * **Daily Scrum** — krótkie, codzinne spotkania zespołu,na których sprawdzane jest czy plan ciągle aktualny i jeśli trzeba to podejowane są działania (inspekcja i adaptacja)
    * **Sprint Review** — spotkanie zespołu na koniec Sprintu, przedstawienie efektów pracy zainteresowanym osobom i na podstawie feedbacku podejmowane decyzje o dalszych etapach prac (inspekcja i adaptacja) 
    * **Sprint Retrospective** — spotkanie zespołu po Sprint Review, na którym zespół analizuje swoją pracę i podejmuje decyzje o poprawie procesu (inspekcja i adaptacja sposobu pracy); pomaga w tym Scrum Master

    
    

### Inne metodyki zwinne

* XP (Extreme Programming)
    * programista w centrum
    * korzystanie z wzorców 
    * programowanie w parach
    
    ![XP (Extreme Programming)](/src/img/io/metodyki/xp.png)
* Test-driven development (TDD)
    * najpierwt testy, potem implementacja, potem refaktoryzacja

    ![Test-driven development (TDD)](/src/img/io/metodyki/tdd.png)

## 41. Testowanie oprogramowania

**Testowanie** — ma na celu weryfikację i walidację oprogramowania.

**Weryfikacja** — czy produkt zgodny z wytycznymi zasad programowania, z zastosowaniem odpowiednich narzędzi i technik; dokonywana podczas testów systemowych i integracyjnych.
    * statyczna — inspekcja kody, przed skompilowaniem
    * dynamiczna — testowanie kodu, po skompilowaniu, z danymi wejściowymi

**Walidacja** — czy produkt spełnia oczekiwania klienta; dokonywana podczas testów akceptacyjnych, ważna też analiza dokumentacji.

### Rodzaje testów ze względu na fazę

* testy jednostkowe — testowanie pojedynczych klas, metod, funkcji
    * test białej skrzynki — testy z uwzględnieniem wiedzy o testowanym kodzie
    * w funkcjach sprawdza się ścieżki przepływu czynności, gdy pętla to:
        * boundaty test — działania w pętli nie wykonywane lub działania w każdej pętli są wykonywane raz dodatkowo wszystkie ścieżki wewnątrz pętli są raz wykonane
        * interior test — działania we wnętrzu pętli uważa się za przetestowane, jeśli zostały wykonane wszystkie ścieżki, które są możliwe przy dwukrotnym powtórzeniu pętli
* testy integracyjne — testowanie integracji komponentów
    * model wielkiego wybuchu (*big-bang testing*) — testowane są wszystkie moduły na raz
    * integracja z dołu (*bottom-up testing*) — testowane są najpierw moduły od najniższego poziomu do wyższych; używa się tzw. *driverów* (komponentów, które symulują wywołania modułów wyższego poziomu) 
    * integracja z góry (*top-down testing*) — testowane są najpierw moduły od najwyższego poziomu do wyższych; używa się tzw. *zaślepek* (komponentów, które symulują wywołania modułów niższego poziomu)
* testy funkcjonalne — ocena spełnienia określonych wymagań 
    * testy czarnej skrzynki — testy bez uwzględnienia wiedzy o testowanym kodzie, nie jest brany pod uwagę mechanizm działania funkcjonlaności
* testy systemowe — testowanie całego systemu, sprawdzenie zgodności z założeniami; testowanie na rzeczywistym środowisku
* testy akceptacyjne — testowanie systemu przez klienta
    * testy alfa — testy przeprowadzane przez testerów, którzy są częścią zespołu tworzącego oprogramowanie
    * testy beta — testy przeprowadzane przez użytkowników

### Podział testów ze względu na rodzaj

* testy regresji — sprawdzenie czy zmiany w kodzie nie spowodowały błędów w dotychczas działających funkcjonalnościach
* testy wydajnościowe — sprawdzenie wydajności systemu
* testy statyczne —  badanie niezawodności systemu na podstawie miar takich, jak: prawdopodobieństwo wystąpienia błędu, częstotliwość występowanie błędu, czas dostępności systemu
* testy bezpieczeństwa (penetracyjne) — symulowanie ataków na system
* testy białej skrzynki — testy z uwzględnieniem wiedzy o działaniu komponentów systemu
* testy czarnej skrzynki — testy bez uwzględnienia wiedzy o działaniu komponentów systemu, bierze się pod uwagę wynik test i stan lub działania początkowe
* testy end-to-end — wykonywanie pełnych scenariuszy przypadków użycia od początku do końca
* testy dostępności — sprawdzenie czy system jest dostępny dla osób niepełnosprawnych
* testy eksploracyjne — testowanie bez wcześniejszego planowania, oparte na doświadczeniu testera, nieplanowane
* testy dymu — yp testów regresji, polegający na wstępnych, powierzchownych testach ujawniających niepowodzenia na tyle kluczowe, aby odrzucić testowaną wersję oprogramowania
* testy poczytalności – typ testów regresji, które są bardziej rozbudowane od testów dymu i sprawdzają szerszy zakres funkcjonalności, ale wciąż są płytsze niż typowe testy regresji – mają za zadanie sprawdzić czy warto poświęcać zasoby na dogłębne testowanie (np. przed wyborem wersji kandydującej do wydania),
* fuzz testing – technika, w której dostarcza się nieprawidłowe lub losowe dane wejściowe i monitoruje pojawianie błędów, testy są zautomatyzowane

![etapy testowania](/src/img/io/etapy_testowania.png)

* testy automatyczne – testy oprogramowania zaprojektowane i wdrożone w taki sposób, aby powtarzalne procedury testujące były wykonywane bez udziału testera
* testy półautomatyczne — tester
używa narzędzi pomocniczych do testowania aplikacji

## 42. Diagramy UML

### Perspektywy w UML

* perspektywa przypadków użycia — opisuje funkcjonalność systemu z punktu widzenia użytkownika, analityków i osób wykonujących testy
    * diagram przypadków użycia, przebiegu, kooperacji, stanów i czynności
* perspektywa projektowa — opisy klas, interfejsów, sekwensji, kooperacji
    * diagram klas, obiektów,  interakcji, stanów i czynności
* perspektywa procesowa — opisuje procesy, które zachodzą w systemie — jak kreowane wątki i procesy
    * diagramy klas, obiektów, interakcji, stanów i czynności
* perspektywa implementacyjna — opisuje komponenty i artefakty, które są użyte do scalenia i fizycznego wdrożenia systemu
    * diagram komponentów, artefaktów
* perspektywa wdrożeniowa — opisuje sprzęt, na którym będzie dział system
    * diagram wdrożenia

### Diagramy UML — podział

* diagramy struktury statycznej modelu
    * diagram klas
    * diagram obiektów
    * diagram komponentów
    * elemntów zawierających strukturę wewnętrzną
    * diagram pakietów
    * diagram profili
    * diagram wdrożenia
* diagramy struktury dynamicznej modelu
    * diagram czynności
    * diagram przypadków użycia
    * diagram stanów
    * diagram sekwencji
    * diagram przeglądu interakcji
    * diagram harmonogramowania
    * diagram komunikacji

### Diagram przypadków użycia

* przypadek użycia — interakcja między aktorem a systemem* definiowanie przypadków użycia
    * aktorzy
        * osoba wchodząca w interakcję z systemem
        * system zewnętrzny
        * część systemu, które mają wpływ na funkcjonowanie systemu, ale same przez ten system nie mogą być zmieniane np. zegar systemowy
    * przypadki użycia
    * relacje między aktorami i przypadkami użycia

![Diagram przypadków użycia](/src/img/io/dia_przyp_uzycia/diagram_przypadkow.png)

* dziedziczenie przypadku użycia — p2 dziedziczy po p1
![Dziedziczenie](/src/img/io/dia_przyp_uzycia/diagram_przypadkow.png)
* przebieg podstawowy — p1 zawsze używa p2
![include](/src/img/io/dia_przyp_uzycia/include.png)
* przebieg opcjonalny — p2 może rozszerzyć p1
![extend](/src/img/io/dia_przyp_uzycia/extend.png)


### Diagram klas

* klasa — wzorzec obiektu
* diagram klas — graficzna reprezentacja klas i ich powiązań
* ikona klasy — składa się z
    * nazwa klasy
    * atrybuty (pola)
    * operacje (metody — realizacja operacji)
    * opcjonalnie zobowązania (*class responsibilities*)
![Klasa](/src/img/io/dia_klas/klasa.png)

**Rodzaje klas:**

* klasa konkretna — wszytskie wywoływane operacja zaimplementowane
* klasa polimoorficzna — min. jedna operacja wirtualna (*operacja wirtualna  kursywą*)
* klasa abstrakcyjna — nie może być instancjonowana (*nazwa klasy kursywą*)
* metaklasa — ma zestaw metod, które odpowiadają podstawowym operacjom klasy, takim jak: sposób tworzenia obiektów, destrukcja obiektów, wywoływanie metod, stosowanie mechanizmów dziedziczenia, przypisywanie wartości atrybutom, uzyskiwanie dostępu do atrybutów, mechanizmy posługiwania się wskaźnikami `this(self)`
* klasy aktywne — mogą być źródłem procesu lub wątku

![Klasa aktywna](/src/img/io/dia_klas/klasa_aktywna.png)

**Inne**

* interfejs — operacje bez implementacji, niekoniecznie wszystkie

![Interfejs](/src/img/io/dia_klas/interfejs.png)

* struktury i typ wyliczeniowy

![Struktury i typ wyliczeniowy](/src/img/io/dia_klas/struct_enum.png)

* wzorzec klas (szablon klas)

![szablon](/src/img/io/dia_klas/szablon.png)

**Związki między klasami:**

* generalizacja — relacja dziedziczenia (dziedziczenie to implementacja generalizacji)

![Dziedziczenie](/src/img/io/dia_klas/dziedziczenie.png)

* zależność —  obiekty jednego
typu są funkcyjnie zależne od obiektów innego typu, zależność np. gdy inna klasa jako argument funkcji, w ciele funkcji

![Zależność](/src/img/io/dia_klas/zaleznosc.png)

* zależność klas zaprzyjaźnionych — dostęp do prywatnych składowych klasy 

![Klasa zaprzyjazniona](/src/img/io/dia_klas/friend.png)

* powiązanie (asocjacja) —  obiekty  jednego typu są połączone z obiektami innego typu poprzez atrybuty danych klas

![Asocjacja](/src/img/io/dia_klas/asocjacja.png)

* klasa powiązania — forma przejściowa między powiązaniem a klasą, pozwalająca na dodanie właściwości do powiązania

![klasa powiązania](/src/img/io/dia_klas/klasa_powiazana.png)

* powiązanie kwalifikowane — powiązanie z możliwością określenia kwalifikatora (atrybutu decydującego o związku między klasami)

![powiązanie kwalifikowane](/src/img/io/dia_klas/powiazanie_kwalifikowane.png)

* agregacja prosta — związek rodzaju *całość-część*

![agregacja prosta](/src/img/io/dia_klas/agregacja_prosta.png)

* agregacja całkowita (kompozycja) — związek rodzaju *całość-część*, w których części są tworzone i zarządzane przez obiekt reprezentujący całość. Ani całość, ani części nie mogą istnieć bez siebie, dlatego czasy ich istnienia są bardzo ściśle ze sobą związane i pokrywają się: w momencie usunięcie obiektu całości obiekty części są również usuwane.

![Kompozycja](/src/img/io/dia_klas/kompozycja.png)

* liczbebność powiązań

![Liczebność powiązań](/src/img/io/dia_klas/liczebnosc.png)

### Diagram czynności

* wykorzystywane podczas aporządzania analizy systemu
* do modelowania przepłuwu sterowania między wykonywanymi czynnościami

* ogólny diagram czynności

![Diagram czynności](/src/img/io/dia_czynnosci/dia_czynnosci.png)

* przykład szczegółowego diagramu czynności

![Diagram czynności szczegłówy](/src/img/io/dia_czynnosci/szczegolowy.png)

* wyjątki

![Wyjątki](/src/img/io/dia_czynnosci/exception.png)

* ścieżki współbieżne

![Ścieżki współbieżne](/src/img/io/dia_czynnosci/sciezki_wspolbiezne.png)

* zakres odpowiedzialności

![Zakres odpowiedzialności](/src/img/io/dia_czynnosci/zakres_odpowiedzialnosci.png)

### Diagram obiektów

* **obiekt** — instancja klasy

![Rodzaje obiektów](/src/img/io/dia_obiektow/rodzaje_obiektow.png)

* nazwa obiektu: nazwa klasy (podkreślone)
* obiekt anonimowy — bez nazwy
* obiekt aktywny — inicjuje działanie innych obiektów, implementacyjnie odwzorowany jako osobny wątek lub proces
* obiekty wielokrotne

![Obiekty wielokrotne](/src/img/io/dia_obiektow/obiekty_wielokrotne.png)

### Diagramy stanów

* obrazują sposób zmiany stanów obiektu w czasie w odpowiedzi na zdarzenia i interakcje

![Diagram stanu](/src/img/io/dia_stanu/dia_stanu.png)

Ogólny diagram stanów systemu budowanego kontrolera temperatury
![Ogólny diagram stanów systemu budowanego kontrolera temperatury](/src/img/io/dia_stanu/dia_stanu_temp.png)

Podstany współbieżne

![Podstany współbieżne](/src/img/io/dia_stanu/wspolbiezne.png)

Przejścia alternatywne

![Przejścia alternatywne](/src/img/io/dia_stanu/alternatywne.png)

### Diagramy sekwencji (przebiegu)

* obrazują interakcje między obiektami w czasie
* składa się z:
    * obiektów
    * komunikatów
        * streotypy `<<create>>`, `<<destroy>>`
        * rodzaje
            * synchroniczny — oczekuje na zakończenie wykonania żądania

            ![Synchroniczny](/src/img/io/dia_przebiegu/synchroniczny.png)
            
            * zwrotny — jako jeden z parametrów adres obiektu wywołującego, aby w trakcie lub po wykonaniu żądania mógł komunikować się z obiektem wywołującym

            ![Zwrotny](/src/img/io/dia_przebiegu/zwrotny.png)

            * asynchroniczny — sterowanie wraca natychmiast po wywołaniu, często realizowane jako metody typu `callback()`

            ![Asynchroniczny](/src/img/io/dia_przebiegu/asynchroniczny.png)

    * osi czasu (lini życia)

![Diagram 1](/src/img/io/dia_przebiegu/dia_1.png)

Rekurencja

![Rekurencja](/src/img/io/dia_przebiegu/rekurencja.png)

Przykład
![Diagram 2](/src/img/io/dia_przebiegu/dia_2.png)


Przykład z operatorami interakcji (np. loop, alt, opt, seq)

![Diagram 3](/src/img/io/dia_przebiegu/dia_3.png)

### Diagramy komunikacji (kooperacji)

* pozwalają wymodelować interacje między obiektami lub/i pomiędzy użytkownikiem systemu i obiektami
* nie w czasie

![Diagram 1](/src/img/io/dia_kooperacji/dia_1.png)

![Diagram 2](/src/img/io/dia_kooperacji/dia_2.png)

* obiekty wielokrotne
    * komunikat do wszystkich obiektów

![komunikat do wszystkich obiektów](/src/img/io/dia_kooperacji/dia_3.png)

    * komunikat do wszystkich — ważna kolejność

![komunikat do wszystkich — ważna kolejność](img/io/dia_kooperacji/dia_4.png)

### Diagram współpracy

* pozwalają na modelowanie interakcji między obiektami w otoczeniu i pojakazują ogólną organizację obiektów uczestniczących w interakcji


![Diagram 1](/src/img/io/dia_wspolpracy/dia_1.png)

![Diagram 2](/src/img/io/dia_wspolpracy/dia_2.png)

### Komponenty

* **komponent** — grupa klas pozostających ze sobą w dobrze zdefiniowanych relacjach (dziedziczenie, powiązania, zależności), i służących jednemu, konkretnemu celowi

![komponent](/src/img/io/komponenty/komponent.png)

* komunikują się ze sobą za pomocą interfejsów

![interfejs i komponenty](/src/img/io/komponenty/interf_komp.png)

Przykładowa struktura komponentów

![Struktura](/src/img/io/komponenty/struktura.png)

### Pakiety

* **pakiet** — służy do grupowania i systematyzowania składników modelu o podobnym przeznaczeniu we wspólnej przestrzeni nazw

![Pakiet](/src/img/io/pakiet.png)

![Pakiety](/src/img/io/pakiety.png)

### Diagram wdrożenia

* służy do zobrazowania fizycznej architektury projektowanego systemu
* podstawowym elementem diagramu wdrożenia jest węzeł

![Diagram wdrożenia](/src/img/io/dia_wdrozenia.png)

![Diagram wdrozenia 2](/src/img/io/dia_wdrozenia2.png)

### Diagram harmonogramowania

* opisują interakcje obiektu stworzonego na bazie klasy w aspekcie czasu trwania sekwencji zmian wartości w czasie (stanu), jaki obiekt może przyjmować

Przykład dla obiektu anonimowego

![Diagram harmonogramowania](/src/img/io/dia_harm.png)

### Relacje wyrażanie (manifest) elementów logicznych przez elementy fizyczne

* standardowo klasa powinna mieć swój pplik nagłówkowy i jeśli to konieczne plik źródłowy

![Manifest](/src/img/io/manifest.png)

## 43. Wzorce projektowe programowania obiektowego

*Każdy wzorzec opisuje
problem, który ciągle pojawia się w naszej dziedzinie, a następnie określa
zasadniczą część jego rozwiązania w taki sposób, by można było zastosować je
nawet milion razy za każdym razem w nieco inny sposób.* — Alexander, Ishikawa, Silverstein 1977

**Wzorce projektowe programowania obiektowego** (ang. *design patterns*) 

* typowe rozwiązania często pojawiających się problemów podczas projektowania oprogramowania
*umiejscowione na poziomie interakcji między klasami programu
* wzorce pośredniego poziomu
* określają strukturę i zachowanie komponentów i zestawów klas systemu

### Podział wzorców projektowych

* wzorce konstrukcyjne (kreacyjne, *creational design patterns*) — opisują mechanizmy tworzenia obiektów
    * budowniczy (*builder*)
    * metoda wytwórcza (*factory method*)
    * prototyp (*prototype*)
    * singleton (*singleton*)
    * fabryka abstrakcyjna (*abstract factory*)
* wzorce strukturalne (*structural design patterns*) _ opisują jak składać obiekty i klasy w większe struktury
    * adapter (*adapter*)
    * dekorator (*decorator*)
    * fasada (*facade*)
    * kompozyt (*composite*)
    * most (*bridge*)
    * pełnomocnik (*proxy*)
    * pyłek (*flyweight*)
* wzorce operacyjne (behawioralne, 
*behavioral design patterns*) — dotyczą algorytmów, rozdzielania odpowiedzialności między obiektami i przepływu danych w programie
    * łańcuch odpowiedzialności (*chain of responsibility*)
    * polecenie (*command*)
    * interpreter (*interpreter*)
    * iterator (*iterator*)
    * mediator (*mediator*)
    * memento (*memento*)
    * obserwator (*observer*)
    * stan (*state*)
    * strategia (*strategy*)
    * metoda szablonu (*template method*)
    * wizytator (*visitor*)
> zobacz [wzorce](refactoring.guru/pl/design-patterns)
