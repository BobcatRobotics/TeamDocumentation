# Classes in Java

In Java, a **class** is a blueprint for creating objects. It defines the properties (fields) and behaviors (methods) that the objects created from the class will have.

## Defining a Class

```java
public class Car {
    // Fields (attributes)
    String color;
    String model;
    int year;

    // Method (behavior)
    void displayInfo() {
        System.out.println("Model: " + model + ", Color: " + color + ", Year: " + year);
    }
}
```

## Creating Objects

You can create objects (instances) of a class using the `new` keyword.

```java
public class Main {
    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.color = "Red";
        myCar.model = "Toyota";
        myCar.year = 2020;

        myCar.displayInfo();
    }
}
```

## Constructors

A **constructor** is a special method used to initialize objects.

```java
public class Car {
    String color;
    String model;
    int year;

    // Constructor
    Car(String color, String model, int year) {
        this.color = color;
        this.model = model;
        this.year = year;
    }

    void displayInfo() {
        System.out.println("Model: " + model + ", Color: " + color + ", Year: " + year);
    }
}

public class Main {
    public static void main(String[] args) {
        Car myCar = new Car("Blue", "Honda", 2022);
        myCar.displayInfo();
    }
}
```

## Encapsulation

Encapsulation is the practice of keeping fields private and providing public methods to access and modify them.

```java
public class Car {
    private String model;

    public void setModel(String model) {
        this.model = model;
    }

    public String getModel() {
        return model;
    }
}
```

## Summary

* A class is a blueprint for objects.
* Objects are instances of a class.
* Constructors initialize objects.
* Fields represent properties; methods represent behaviors.
* Encapsulation protects object data using private fields and public methods.
