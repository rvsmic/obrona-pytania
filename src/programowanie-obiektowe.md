# Programowanie obiektowe

[`back to README.md`](../README.md)

## 14. Obiekt i klasa w wybranym języku programowania zorientowanym obiektowo

> **Obiekt** to instancja klasy. **Klasa** to szablon, na podstawie którego tworzone są obiekty.

### Klasa

**Klasa** — częściowa lub całkowita definicja dla obiektów, które będą tworzone na jej podstawie. Klasa posiadają strukturę (**atrybuty**/pola) jak i interfejs — sposób komunikacji z obiektami danej klasy (**metody**) które będą tworzone na jej podstawie. Klasy zazwyczaj są *typami* języka programowania

#### Przykład w Javie

```java
public class Person {
    // ATRYBUTY
    private String name;
    private int age;
    
    // KONSTRUKTOR
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    // METODY
    public String getName() {
        return name;
    }
    
    public int getAge() {
        return age;
    }
    
    public void setName(String name) {
        this.name = name;
    }
    
    public void setAge(int age) {
        this.age = age;
    }
    
    public void introduce() {
        System.out.println("Hi, my name is " + name + " and I am " + age + " years old.");
    }
}
```

Rodzaje klas:

* **Klasa abstrakcyjna** — klasa, która nie może być instancjonowana, służy jako szablon dla innych klas
* **Klasa finalna** — klasa, która nie może być rozszerzona (dziedziczona)
* **Klasa anonimowa** — klasa, która nie posiada nazwy, jest tworzona w miejscu użycia
* **Klasa wewnętrzna/zagnieżdżona** — klasa zdefiniowana wewnątrz innej klasy
* **Klasa lokalna** — klasa zdefiniowana wewnątrz metody/innego bloku kodu
* **Meta-klasa** — klasa, której obiekty są klasami
* **Klasa wirutalna** — klasa, której obiekty są obiektami innych klas

### Obiekt

**Obiekt** — instancja klasy. Obiekt posiada stan (wartości atrybutów) oraz zachowanie (metody). Obiekt jest tworzony na podstawie klasy. Obiekt jest *wartością* języka programowania. Ma też swoją *tożsamość* (cechę odróżniającą go od innych obiektów, np id).

## 15. Hermetyzacja, dziedziczenie i polimorfizm w programowaniu obiektowym

### Hermetyzacja

**Hermetyzacja** — ukrywanie szczegółów implementacji. W programowaniu obiektowym hermetyzacja jest realizowana przez ukrywanie atrybutów klasy (np. poprzez ustawienie ich jako prywatne) i udostępnianie ich za pomocą metod (np. getterów i setterów).

### Dziedziczenie

**Dziedziczenie** — mechanizm, który pozwala na tworzenie nowych klas na podstawie już istniejących.
Klasa, która jest podstawą do stworzenia nowej klasy nazywamy **klasą bazową**.
Klasa, która jest tworzona na podstawie klasy bazowej nazywamy **klasą pochodną**.
Klasa pochodna dziedziczy po klasie bazowej jej atrybuty i metody.
Klasa pochodna może rozszerzać funkcjonalność klasy bazowej poprzez dodanie nowych atrybutów i metod.
Klasa pochodna może nadpisywać metody klasy bazowej.
Klasa pochodna może być bazą dla kolejnej klasy pochodnej. Dziedziczenie jest realizowane przez słowo kluczowe `extends`.

Mechanizm dziedziczenia pozwala na tworzenie hierarchii klas, które są ze sobą powiązane. Klasa pochodna jest bardziej wyspecjalizowana niż klasa bazowa.

### Polimorfizm

**Polimorfizm** — mechanizm, który pozwala na wykonywanie tej samej operacji na różnych typach danych. Polimorfizm jest realizowany przez przeciążanie metod i operatorów oraz przez dziedziczenie. Polimorfizm pozwala na traktowanie obiektów różnych klas w ten sam sposób. Na przykład jeśli klasa `Pies` dziedziczy po klasie `Zwierzę` to obiekt klasy `Pies` może być traktowany jako obiekt klasy `Zwierzę`.

Przykład w Javie:

```java
public class Animal {
    public void makeSound() {
        System.out.println("Animal sound");
    }
}

public class Dog extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Woof");
    }
}

public class Cat extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Meow");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal animal = new Animal();
        Animal dog = new Dog();
        Animal cat = new Cat();
        
        animal.makeSound(); // Animal sound
        dog.makeSound(); // Woof
        cat.makeSound(); // Meow
    }
}
```


* **Polimorfizm ad hoc** — polimorfizm, który jest realizowany przez przeciążanie metod i operatorów
* **Polimorfizm uniwersalny** — polimorfizm, który jest realizowany przez dziedziczenie

* **Polimorfizm statyczny** — polimorfizm, który jest realizowany w czasie kompilacji. Przykładem jest przeciążanie operatorów
* **Polimorfizm dynamiczny** — polimorfizm, który jest realizowany w czasie wykonania. Przykładem jest metody wirtualne — konkretna metoda jest wybierana w czasie wykonania w zależności od typu obiektu

## 16. Interfejsy i klasy abstrakcyjne w programowaniu obiektowym

## 17. Paradygmat i przykłady programowania generycznego (rodzajowego)
