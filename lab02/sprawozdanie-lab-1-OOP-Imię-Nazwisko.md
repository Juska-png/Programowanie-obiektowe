## I. Dokumentacja do lab. nr 3 - "Klasy oraz ich elementy składowe, metody klasy"
## II. Eryk Sulich - niestacjonarne, semestr III
## III. Przedmiot - "Programowanie obiektowe"

## IV. Opis zadania do realizacji
Do zrealizowania były następujące zadania:  
  - Zadanie 1. - Klasa Film z polami tytul, rezyser, rokProdukcji, obejrzany oraz metodami obejrzyj(), wyswietlInfo(),  
  - Zadanie 2. - klasa KalkulatorTemperatur z metodami statycznymi celsiusToFahrenheit(double) i fahrenheitToCelsius(double).,  
  - Zadanie 3. - Zaimplementuj klasę BankAccount z metodami deposit(double), withdraw(double) i getBalance() oraz podstawową walidacją.,  
  - Zadanie 4. - klasa StudentGroup, która posiada pole statyczne zliczające liczbę utworzonych obiektów klasy Student.
- Zadanie 5. - klasa Rectangle z konstruktorem, polami width i height oraz metodami area() i perimeter() wykorzystującymi this.
- Zadanie 6. - klasa metoda z varargs (np. sum(int... numbers)) i pokaż jej użycie dla różnych liczb argumentów. Poniżej przykład z varargs:


## V. Technologie wykorzystane w zadaniu
  - Java,

## VI. Realizacja zadania
<br>

#### 1. Kod Javy (lub Pythona)
Zadanie 1.
```java
    public class Film {
    String tytul;
    String rezyser;
    int rokprodukcji;
    boolean obejrzany;

    void obejrzyj() {
        obejrzany = true;
        System.out.println("Obejrzano: \"" + tytul + "\"");
    }

    void wyswietlInfo() {
        System.out.println("Tytuł: " + tytul);
        System.out.println("Autor: " + rezyser);
        System.out.println("Strony: " + rokprodukcji);
        System.out.println("Obejrzana: " + (obejrzany ? "Tak" : "Nie"));
    }

    public static void main(String[] args) {
        Film f = new Film();
        f.tytul = "Lalka";
        f.rezyser = "Maciej Kawalski";
        f.rokprodukcji = 2026;

        Film i = new Film();
        i.tytul = "Avatar";
        i.rezyser = "James Francis Cameron";
        i.rokprodukcji = 2009;

        f.wyswietlInfo();
        System.out.println();
        f.obejrzyj();
        f.wyswietlInfo();
        System.out.println();
        i.wyswietlInfo();
        System.out.println();
        i.obejrzyj();
        i.wyswietlInfo();
    }
}
```
Zadanie 2.
```java
    public class KalkulatorTemperatur {

    double celsiusToFahrenheit(double a, double b){
        return a*b+32;
    }

    double fahrenheitToCelsius(double a){
        return (a-32)* 5/9;
    }

    public static void main(String[] args) {
        KalkulatorTemperatur kalk = new KalkulatorTemperatur();
        System.out.println("20 stopni C to " + kalk.celsiusToFahrenheit(20,1.8) +" F");
        System.out.println("200 stopni F to " + kalk.fahrenheitToCelsius(200) +" C");
    }

}
```

Zadanie 3.
```java
public class BankAccount {

    private double balance = 0;

    public void deposit(double stan) {
        if (stan > 0) {
            balance = balance + stan;
        } else {
            System.out.println("Kwota musi byc wieksza od 0");
        }
    }

    public void withdraw(double stan) {
        if (stan <= 0) {
            System.out.println("Kwota musi byc wieksza od 0");
        } else if (stan > balance) {
            System.out.println("Brak pieniedzy na koncie");
        } else {
            balance = balance - stan;
        }
    }

    public double getBalance() {
        return balance;
    }

    public static void main(String[] args) {
        BankAccount konto = new BankAccount();

        konto.deposit(100);
        konto.deposit(50);

        System.out.println("Saldo: " + konto.getBalance());

        konto.withdraw(40);

        System.out.println("Saldo po wyplacie: " + konto.getBalance());
    }
}

```

Zadanie 4. - klasa StudentGroup
```java
public class StudentGroup {
    private String imie;
    private double numer;

    public static int liczbaStudentów = 0;

    StudentGroup(String imie, double numer) {
        this.imie = imie;
        this.numer = numer;
        liczbaStudentów++;
    }

    static int getLiczbaStudentów() {
        return liczbaStudentów;
    }
}
```

Zadanie 4. - klasa Student
```java
public static void main(String[] args) {
    new StudentGroup("Anna", 01);
    new StudentGroup("Jan", 02);
    new StudentGroup("Ewa", 03);
    new StudentGroup("Paula", 04);

    System.out.println("Liczba studentów: " +  StudentGroup.getLiczbaStudentów());
}

```

Zadanie 5.
```java
public class Rectangle {
    private double width;
    private double height;

    // this rozróżnia pole klasy od parametru
    Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    double area() {
        return this.width * this.height;
    }

    double perimeter() {
        return 2 * (this.width + this.height);
    }

    void wyswietl() {
        System.out.printf("Prostokąt %.1f x %.1f, pole=%.2f, obwód=%.2f%n",
                width, height, area(), perimeter());
    }

    public static void main(String[] args) {
        Rectangle p = new Rectangle(2, 8);
        p.wyswietl();
    }
}
```
Zadanie 6.
```java
public class MetodyVarargs {
    static int suma(int... liczby) {
        int wynik = 0;

        for (int l : liczby) {
            wynik = wynik + l;
        }
        return wynik;
    }
    public static void main(String[] args) {
        System.out.println(suma(6, 7));
        System.out.println(suma(6, 7, 6));
        System.out.println(suma(6, 7, 6, 7));
        System.out.println(suma(6, 7, 6, 7, 6));
    }
}
```

#### 2. Zrzuty ekranu pokazujące wynik działania aplikacji/skryptu:  
Zadanie 1.
![Zadanie1.png](Zadanie1.png)

Zadanie 2.
![Zadanie 2.png](Zadanie%202.png)

Zadanie 3.
![Zadanie3.png](Zadanie3.png)

Zadanie 4.
![Zadanie4.png](Zadanie4.png)

Zadanie 5.
![Zadanie5.png](Zadanie5.png)

Zadanie 6.
![Zadanie6.png](Zadanie6.png)

<br>
