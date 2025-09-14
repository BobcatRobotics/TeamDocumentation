
# Java Basics: Math Operations

## Intro
Java provides a variety of ways to perform **mathematical operations** on numbers.  
Understanding these operations is essential for programming robots, calculating motor speeds, distances, and sensor values.

---

## 1️⃣ Arithmetic Operators

| Operator | Description         | Example        | Result |
|----------|-------------------|----------------|--------|
| `+`      | Addition           | `5 + 3`        | `8`    |
| `-`      | Subtraction        | `5 - 3`        | `2`    |
| `*`      | Multiplication     | `5 * 3`        | `15`   |
| `/`      | Division           | `6 / 3`        | `2`    |
| `%`      | Modulus (remainder)| `7 % 3`        | `1`    |

```java
int a = 10;
int b = 3;
int sum = a + b;       // 13
int remainder = a % b; // 1
```

---

## 2️⃣ Shorthand Operators

| Operator | Description          | Example       |
|----------|--------------------|---------------|
| `+=`     | Add and assign      | `a += 5;`    // a = a + 5 |
| `-=`     | Subtract and assign | `a -= 2;`    // a = a - 2 |
| `*=`     | Multiply and assign | `a *= 3;`    // a = a * 3 |
| `/=`     | Divide and assign   | `a /= 2;`    // a = a / 2 |
| `%=`     | Modulus and assign  | `a %= 4;`    // a = a % 4 |

---

## 3️⃣ Increment and Decrement

| Operator | Description        | Example       |
|----------|------------------|---------------|
| `++`     | Increment by 1    | `a++;`       |
| `--`     | Decrement by 1    | `a--;`       |

```java
int counter = 0;
counter++; // counter = 1
counter--; // counter = 0
```

---

## 4️⃣ Math Class

Java provides a built-in `Math` class with **common mathematical functions**:

| Method                 | Description                   | Example          |
|------------------------|-------------------------------|----------------|
| `Math.abs(x)`          | Absolute value                | `Math.abs(-5)` → 5 |
| `Math.max(a, b)`       | Maximum of two numbers        | `Math.max(5, 3)` → 5 |
| `Math.min(a, b)`       | Minimum of two numbers        | `Math.min(5, 3)` → 3 |
| `Math.pow(a, b)`       | a raised to the power of b    | `Math.pow(2, 3)` → 8 |
| `Math.sqrt(x)`         | Square root                   | `Math.sqrt(16)` → 4 |
| `Math.round(x)`        | Round to nearest integer      | `Math.round(3.6)` → 4 |
| `Math.floor(x)`        | Round down                    | `Math.floor(3.6)` → 3 |
| `Math.ceil(x)`         | Round up                      | `Math.ceil(3.1)` → 4 |

```java
double speed = 4.7;
int roundedSpeed = (int) Math.round(speed); // 5
double distance = Math.pow(2, 3);          // 8.0
```

---

## 5️⃣ Example in FRC Context

```java
int leftEncoder = 500;
int rightEncoder = 480;

// Average encoder value
int averageEncoder = (leftEncoder + rightEncoder) / 2;

// Calculate motor output
double speed = Math.min(1.0, averageEncoder / 1000.0);

// Ensure positive value
speed = Math.abs(speed);
```

---

## 6️⃣ Best Practices

- Always **cast or convert** to the correct type when using division (`int / int` truncates decimals)  
- Use `Math` functions for **robust calculations**  
- Prefer **constants** for repeated numbers (e.g., `final double WHEEL_DIAMETER`)  
- Keep calculations **readable** by breaking them into intermediate variables
