# Bazy danych
[`back to README.md`](../README.md)
## 34. Normalizacja baz danych – pierwsza, druga i trzecia postać normalna.
Postać normalna — postać relacji w bazie danych, w której nie występuje redundancja (nadmiarowość), czyli powtarzanie się tych samych informacji. Doprowadzenie relacji do postaci normalnej nazywa się normalizacją (lub dekompozycją) bazy danych. Wyróżnia się następujace postacie normalne 1NF, 2NF, 3NF, BCNF (Boyce’a-Codda), 4NF i 5NF. 4NF i 5NF w zasadzie wyłącznie w rozważaniach teoretycznych.
* Pierwsza postać normalna (1NF) 
    * relacja opisuje jeden obiekt
    * zdefiniowany klucze relacji
    * atrybuty niekluczowe są w zależności funkcyjnej od klucza
    * wartości atrybutów są elementarne (atomowe, niepodzielne) – każda kolumna jest wartością skalarną (atomową), a nie macierzą lub listą czy też czymkolwiek, co posiada własną strukturę
    * nie zawiera kolekcji (powtarzających się grup informacji)
    * kolejność wierszy może być dowolna (znaczenie danych nie zależy od kolejności wierszy)
    
    ![przed_1nf](/src/img/bazy-danych/przed_normalizacja.png)

    ![po_1nf](/src/img/bazy-danych/1NF_1.png)
* Druga postać normalna (2NF)
    * spełnia założenia 1NF
    * żadna kolumna niekluczowa nie jest częściowo funkcyjnie zależna od jakiegokolwiek klucza potencjalnego
    * Przykład: klucz potencjalny składa się z dwóch pól: "Imię" oraz "Nazwisko". Przy założeniu, że każde imię ma przypisaną jedną płeć, czyli, że płeć zależy tylko od jednego z atrybutów klucza potencjalnego, tabela nie spełnia warunków na drugą postać normalną.

    ![przed_nf2_pracownicy](/src/img/bazy-danych/przed_normalizacja_2NF.png)

    ![po_nf2_pracownicy](/src/img/bazy-danych/2NF_1.png)

    ![nowa_tabla_po_nf2](/src/img/bazy-danych/2NF_2.png)

* Trzecia postać normalna (3NF)
    * spałnia założenia 2NF
    * żaden atrybut niekluczowy nie jest zależny funkcyjnie od innych atrybutów niekluczowych
    * Przykład: Klucz potencjalny składa się tu z dwóch pól: "Imię" oraz "Nazwisko". Oba atrybuty niekluczowe: "Stanowisko" oraz "Stawka za godzinę" są zależne od całego klucza potencjalnego- tzn. dany pracownik ma przyporządkowane jedno stanowisko i jedną stawkę godzinową. Przy założeniu, że każde stanowisko jest tak samo płatne, to wartości w kolumnie „Stawka za godzinę” są zależne jedynie od pola „Stanowisko”, a tylko pośrednio od klucza potencjalnego. 
    
    ![przed_nf3_pracownicy](/src/img/bazy-danych/przed_normalizacja_3NF.png)

    ![po_nf3_pracownicy](/src/img/bazy-danych/3NF_1.png)

    ![nowa_tabla_op_nf3](/src/img/bazy-danych/3NF_2.png)
    
## 35. Modele baz danych (logiczny, relacyjny, fizyczny).
### Model logiczny
Model logiczny składa się ze zbioru encji  oraz ich atrybutów (wraz z określeniem typu danych, wymagalności,
ograniczeń) i klucze główne. Pomiędzy tak zdefiniowanymi zbiorami encji kreśli się relacje o określonych własnościach.
![model logiczny](/src/img/bazy-danych/logiczny.png)
Związki pomiędzy encjami w modelu logicznym (CMD):
* jeden do jednego (1:1) (związek wymagany z jednej
strony)
  ![1:1](/src/img/bazy-danych/image-9.png)
* jeden do wielu (1:N) (nie wymagany z żadnej strony)
  ![1:N](/src/img/bazy-danych/image-10.png)
* wiele do jednego (N:1) (wymagany z jednej strony)
  ![N:1](/src/img/bazy-danych/image-12.png)
* wiele do wielu (N:M) (nie wymagany)
  ![N:M](/src/img/bazy-danych/image-11.png)
### Model relacyjny
Model relacyjny jest oparty na matematycznym pojęciu relacji, która jest reprezentowana
fizycznie jako tabela. W modelu tym, strukturą danych jest relacja.

Model ten wprowadził:
* Solidne podstawy matematyczne (rachunek relacji) pozwalający rozwiązywać problemy
semantyki, spójności i redundancji danych.
* Umożliwienie przy wykorzystaniu algebry relacji rozwoju języków przetwarzania
danych opartych na przetwarzaniu zbiorów

Relacja posiada następujące cechy:
* każdy atrybut relacji ma unikalną nazwę,
* porządek atrybutów w relacji nie jest istotny,
* porządek krotek w relacji nie jest istotny i nie jest elementem definicji relacji,
* wartości atrybutów są atomowe (elementarne),
* relacja nie zawiera rekordów (krotek) powtarzających się.

Relacyjna baza danych:
* Baza danych jest zbiorem powiązanych relacji.
* Schemat relacji jest zbiorem {atrybut, dziedzina, [ograniczenia integralnościowe]}.
* Schemat bazy danych jest zbiorem schematów relacji.
* Relacja jest zbiorem krotek.
* Krotka jest listą wartości atomowych.
* Klucz główny relacji - atrybut lub grupa atrybutów jednoznacznie znakująca wszystkie możliwe krotki (unikalność wartości klucza).
* Klucz prosty - klucz składający się z jednego atrybutu
* Klucz złożony - klucz składający się z grupy atrybutów.
* Klucz naturalny - klucz składający się z atrybutów występujących naturalnie w projektowanej relacji, np. PESEL pracownika.
* Klucz sztuczny - wprowadzony sztucznie atrybut, zaprojektowany z myślą o pełnieniu funkcji klucza głównego, np. ID_PRAC typu liczby rzeczywistej,wzrastającej automatycznie przy wprowadzaniu nowej krotki.

### Model fizyczny
Model fizyczny (PDM) jest to model, który jest zależny od konkretnej implementacji bazy danych. W modelu fizycznym określa się typy danych, indeksy, klucze obce, ograniczenia, itp. Model fizyczny jest tworzony na podstawie modelu logicznego.
![model fizyczny](/src/img/bazy-danych/image-13.png)

## 36. Rodzaje zapytań w języku SQL.
Zapytania zaliczamy do jednej z czterech  kategorii:
* SQL DML (ang. Data Manipulation Language – "język manipulacji danymi") — do wykonywania operacji na danych; (dane tekstowe muszą być zawsze ujęte w znaki pojedynczego cudzysłowu (')):
  * `INSERT`
    * `INSERT INTO pracownicy
    (imie, nazwisko, pensja, staz) VALUES ('Jan', 'Kowalski', 5500, 1);`
  * `UPDATE`
    * `UPDATE pracownicy SET pensja = pensja * 1.1 WHERE staz > 2;`
  * `DELETE`
    * `DELETE FROM pracownicy WHERE imie = 'Jan' AND nazwisko = 'Kowalski';`
* SQL DDL (ang. Data Definition Language – "język definicji danych") — operacje na strukturach, w których przechowywane są dane:
  * `CREATE` (np. `CREATE TABLE`, `CREATE DATABASE`) — utworzenie struktury (np, bazy, tablei, indeksu, itp.)
    * `CREATE TABLE pracownicy
(
    imie varchar(255), 
    nazwisko varchar(255), 
    pensja float,
    staz int
);`
  * `DROP` — usunięcie struktury
    * `DROP TABLE pracownicy;`
  * `ALTER` (np. `ALTER TABLE ADD COLUMN ...`)— zmiana struktury (dodanie kolumny, zmiana typu danych) 
    * `ALTER TABLE pracownicy
    ADD dzial varchar(255);`
* SQL DCL (ang. Data Control Language – "język kontroli nad danymi") — do nadawania uprawnień do obiektów bazodanowych:
  * `GRANT` — nadanie uprawnień do pojedynczych obiektów lub globalnie konkretnemu użytkownikowi (np. `GRANT ALL PRIVILEGES ON EMPLOYEE TO PIOTR WITH GRANT OPTION` – przyznanie wszystkich praw do tabeli EMPLOYEE użytkownikowi PIOTR z opcją pozwalającą mu nadawać prawa do tej tabeli)
  * `REVOKE` — odebranie uprawnień (np. `REVOKE ALL PRIVILEGES ON EMPLOYEE FROM PIOTR` - odebranie użytkownikowi wszystkich praw do tabeli EMPLOYEE)
  * `DENY` — odmowa uprawnień
* SQL DQL (ang. Data Query Language – "język definiowania zapytań") — formułowanie zapytań do bazy danych:
  * `SELECT` — często traktuje się jako część języka DML, ale to podejście nie wydaje się właściwe, ponieważ DML z definicji służy do manipulowania danymi - ich tworzenia, usuwania i uaktualniania.
    * `SELECT * FROM emp WHERE salary > 1000 order by seniority DESC;` — DESC malejąco, ASC rosnąco
  * `SELECT INTO` — dodatkowo modyfikuje (przepisuje, tworzy) dane; na pograniczu DML i DQL


Instrukcje SQL w obrębie zapytań tradycyjnie zapisywane są wielkimi literami, jednak nie jest to wymóg. Każde zapytanie w SQL-u musi kończyć się znakiem średnika (;).
## 37. Funkcje w języku SQL.

* Oracle — https://drive.google.com/drive/folders/1_lTvQF-mQFe5d8FA3U_od7YRN-xQ_C7d
  * funkcje numeryczne np.:
    * `ABS(n)`
    * `CEIL(n)`
    * `COS(n)`
    * `EXP(n)`
    * `LN(n)`
    * `ROUND(n)`
    * `SQRT(n)`
    * `TRUNC(n [, m])`
  * funkcje znakowe zwracające wartości znakowe np.:
    * `CONCAT(s1, s2)`
    * `INITCAP(s)` — pierwsza litera wielka, pozostałe małe
    * `LOWER(s)`
    * `LPAD(s, n [, c])` — dopełnienie z lewej strony
    * `REPLACE(s, s1, s2)` — zamiana s1 na s2 w s
    * `RPAD(s, n [, c])` — dopełnienie z prawej strony
    * `SUBSTR(s, n [, m])` — podciąg od n do m
  * funkcje znakowe zwracające wartości liczbowe
    * `ASCII(s)` — kod ASCII pierwszego znaku s
    * `INSTR(s1, s2 [, n [, m]])` — pozycja podciągu s2 w s1 od n do m
    * `LENGTH(s)`
  * funkcje operujące na datach np.:
    * `ADD_MONTHS(data, n)`
    * `EXTRACT(element FROM data)`
    * `LAST_DAY(data)` — ostatni dzień miesiąca daty
    * `MONTHS_BETWEEN(data1, data2)` — LICZBA MIESIĘCY POMIĘDZY DATAMI
    * `NEXT_DAY(data, dzień tyg)` — data następnego dnia tygodnia
    * `ROUND(data [, fmt])` — zaokrąglenie daty do jednostki określonej przez fmt
    * `SYSDATE`
    * `TO_CHAR(data [, fmt[, nlsparams]])`
  * funkcje konwertujące
    * `TO_CHAR(n [, fmt])`
    * `TO_DATE(s [, fmt])`
    * `TO_NUMBER(s [, fmt])`
  * inne np.:
    * `COALESCE(e1, e2, ..., en)` — zwraca pierwszy niepusty argument, gdy wszystkie są puste zwraca NULL
    * `DECODE(wyr, s1, r1, s2,r2,...[, domyślna])`
    * `CASE WHEN war1 THEN r1 WHEN war2 THEN r2 ... [ELSE p] END`
    * `GREATEST(e1, e2, ..., en)`
    * `LEAST(e1, e2, ..., en)`
    * `NVL(e1, e2)` — zwraca e1, jeśli nie jest NULL, w przeciwnym razie zwraca e2
    * `NVL2(e1, e2, e3)` — zwraca e2, jeśli e1 nie jest NULL, w przeciwnym razie zwraca e3
  
## 38. Transakcje w bazach danych. 
Transakcja w bazie danych — seria jednej lub więcej operacji wykonywanych jako pojedyncza, atomowa jednostka pracy (albo wszystkie operacje w transakcji zostaną zakończone sukcesem, albo żadna z nich nie zostanie zastosowana w bazie danych). Transakcje są wykorzystywane do zapewnienia spójności i integralności danych poprzez zapewnienie, że baza danych pozostaje spójna nawet w przypadku awarii systemu lub błędów. Są niezbędne do umożliwienia współbieżnego dostępu, zapewnienia atomowości,  odzyskiwania danych oraz zapewnienia właściwości ACID.


Cechy transakcji zapewniające niezawodność bazy danych — Właściwości  ACID to zestaw właściwości, które zapewniają niezawodność transakcji bazodanowych:

* Atomowość: transakcja jest traktowana jako pojedyncza, niepodzielna jednostka pracy. Oznacza to, że albo wszystkie operacje w transakcji są zakończone sukcesem, albo żadna z nich nie jest stosowana w bazie danych. W przypadku niepowodzenia baza danych jest cofana do stanu sprzed transakcji, co pozwala zachować spójność.
* Spójność: baza danych pozostaje w spójnym stanie przez cały czas trwania transakcji. DBMS sprawdza ograniczenia integralności przed i po transakcji i zwija transakcję, jeśli któreś z ograniczeń zostanie naruszone.
* Izolacja: zmiany dokonane przez transakcję nie są widoczne dla innych transakcji, dopóki transakcja nie zostanie popełniona. Izolacja ta pomaga zapobiegać konfliktom pomiędzy współbieżnymi transakcjami.
* Trwałość: zmiany dokonane przez transakcję są trwałe i przetrwają wszelkie kolejne awarie. DBMS używa techniki zwanej logowaniem, aby zapewnić, że zmiany dokonane przez transakcję mogą być cofnięte w przypadku niepowodzenia.
Razem, właściwości te zapewniają, że baza danych pozostaje niezawodna i spójna pomimo współbieżnych transakcji i awarii systemu.

Działanie transakcji:

* Transakcja w bazie danych rozpoczyna się od wykonania pojedynczej operacji, takiej jak wstawienie danych do tabeli. Jeśli w ramach tej samej transakcji wykonywane są inne procedury, to wszystkie one są wykonywane jako pojedyncza jednostka atomowa. System zarządzania bazą danych (DBMS) wykorzystuje menedżera transakcji do śledzenia poszczególnych operacji transakcyjnych i zapewnienia, że są one wykonywane we właściwej kolejności.
* Kiedy transakcja jest uruchamiana, DBMS tworzy nowy kontekst transakcji i przypisuje go do bieżącego wątku wykonania. Wszelkie operacje na bazie danych, które są wykonywane w ramach tego kontekstu, są uważane za część transakcji.


* Dokładna składnia rozpoczęcia i zakończenia transakcji zależy od konkretnego systemu zarządzania bazą danych (DBMS). Na przykład w SQL możesz rozpocząć transakcję przy użyciu polecenia BEGIN TRANSACTION i zakończyć ją przy użyciu polecenia COMMIT lub ROLLBACK. W innych systemach DBMS podobne polecenia mogą mieć inną składnię. Po zakończeniu operacji, transakcja może zostać wykonana lub cofnięta. Jeśli transakcja zostanie zatwierdzona, DBMS stosuje wszystkie operacje w transakcji do bazy danych, czyniąc je trwałymi. Jeśli transakcja jest wycofana, DBMS cofa wszystkie operacje w transakcji, przywracając bazę danych do stanu sprzed rozpoczęcia transakcji.

Jakie przykłady operacji na bazie danych mogą być częścią transakcji?
* wstawianie
* aktualizacja lub usuwanie danych w tabeli 
* tworzenie lub modyfikacja tabeli
* tworzenie lub modyfikacja indeksu.


Transakcje są izolowane — zmiany dokonane przez transakcję nie są widoczne dla innych transakcji, dopóki transakcja nie zostanie popełniona. Izolacja ta pomaga zapobiegać konfliktom między współbieżnymi transakcjami. 

DBMS wykorzystuje technikę zwaną blokowaniem, aby zapewnić, że tylko jedna transakcja ma dostęp do określonego fragmentu danych w danym momencie. Zapobiega to modyfikowaniu tych samych danych przez inne transakcje, co mogłoby powodować konflikty.

