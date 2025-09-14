# Java Basics: Methods

## Intro
Methods in Java are **blocks of code that perform a specific task**.  
They help make code **reusable, modular, and organized**. In FRC, methods are used for actions like moving motors, reading sensors, or running autonomous routines.

---

## 1️⃣ Declaring a Method

Syntax:

```java
accessModifier returnType methodName(parameters) {
    // Code to execute
}
```

Example:

```java
public int addNumbers(int a, int b) {
    return a + b;
}
```

---

## 2️⃣ Calling a Method
```java
int result = addNumbers(5, 3);
System.out.println(result); // 8
```

---

## 3️⃣ Method Parameters
```java
public void setMotorSpeed(int motorID, double speed) {
    // Set motor speed
}
```
Call example:
```java
setMotorSpeed(1, 0.8);
```

---

## 4️⃣ Return Values
```java
public double getAverage(double a, double b) {
    return (a + b) / 2;
}

public void printMessage(String message) {
    System.out.println(message);
}
```

---

## 5️⃣ Overloading Methods
```java
public int multiply(int a, int b) { return a * b; }
public double multiply(double a, double b) { return a * b; }
```

---

## 6️⃣ Example in FRC Context
```java
public void driveForward(double speed, int duration) {
    leftMotor.set(speed);
    rightMotor.set(speed);
    Timer.delay(duration);
    leftMotor.stop();
    rightMotor.stop();
}
```

---

## 7️⃣ Best Practices
- Use descriptive names
- Keep methods short and focused
- Use parameters instead of hardcoding
- Comment public methods with Javadoc
