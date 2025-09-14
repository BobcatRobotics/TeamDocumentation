# Java Basics: If, Else If, and Else

## Intro
In Java, **decision-making statements** allow your program to choose different paths of execution based on conditions.  
The most common ones are **if**, **else if**, and **else**.

---

## 1️⃣ If Statement
The `if` statement executes a block of code only if the condition is `true`.

```java
int score = 85;

if (score > 70) {
    System.out.println("You passed!");
}
```

Output:  
```
You passed!
```

---

## 2️⃣ If-Else Statement
The `else` block runs if the `if` condition is `false`.

```java
int score = 50;

if (score > 70) {
    System.out.println("You passed!");
} else {
    System.out.println("You failed!");
}
```

Output:  
```
You failed!
```

---

## 3️⃣ If-Else If-Else Statement
Use multiple conditions with `else if`.  
The first condition that evaluates to `true` will run.

```java
int score = 85;

if (score >= 90) {
    System.out.println("Grade: A");
} else if (score >= 80) {
    System.out.println("Grade: B");
} else if (score >= 70) {
    System.out.println("Grade: C");
} else {
    System.out.println("Grade: F");
}
```

Output:  
```
Grade: B
```

---

## 4️⃣ Nested If Statements
You can put an `if` inside another `if`.

```java
boolean isMember = true;
int age = 20;

if (isMember) {
    if (age >= 18) {
        System.out.println("Adult member");
    } else {
        System.out.println("Minor member");
    }
} else {
    System.out.println("Not a member");
}
```

---

## 5️⃣ Example in FRC Context

```java
double batteryVoltage = 11.5;

if (batteryVoltage >= 12.0) {
    System.out.println("Battery is fully charged.");
} else if (batteryVoltage >= 10.5) {
    System.out.println("Battery is OK for matches.");
} else {
    System.out.println("Battery is too low! Replace immediately.");
}
```

---

## ✅ Best Practices
- Keep conditions simple and readable.  
- Avoid deeply **nested if statements** → consider `switch` or separate methods.  
- Use **descriptive variable names** so conditions are clear.  
