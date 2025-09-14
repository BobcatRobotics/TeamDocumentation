
# Java Basics: Variables

## Intro
Variables in Java are used to **store data values**. Each variable has a **type**, a **name**, and a **value**.  
They allow your program to store and manipulate information during execution.

---

## 1️⃣ Declaring Variables

Syntax:

```java
type variableName = value;
```

Example:

```java
int motorSpeed = 100;       // Integer variable
double batteryVoltage = 12.5; // Decimal variable
boolean isEnabled = true;   // Boolean variable
String robotName = "Romi";  // Text variable
```

---

## 2️⃣ Primitive Data Types

| Type      | Size / Description            | Example       |
|-----------|-------------------------------|---------------|
| `int`     | 32-bit integer                | `int count = 10;` |
| `double`  | 64-bit floating-point number  | `double speed = 3.14;` |
| `boolean` | true or false                 | `boolean active = true;` |
| `char`    | Single character              | `char grade = 'A';` |
| `byte`    | 8-bit integer                 | `byte smallNumber = 100;` |
| `short`   | 16-bit integer                | `short distance = 300;` |
| `long`    | 64-bit integer                | `long score = 1000000L;` |
| `float`   | 32-bit floating-point number  | `float pi = 3.14f;` |

---

## 3️⃣ Reference Types

- Used to store **objects** or **more complex data**
- Most common example: `String`

```java
String teamName = "FRC Team 1234";
MotorController leftMotor = new MotorController(1);
```

---

## 4️⃣ Variable Naming Rules

- Must **start with a letter, `_` or `$`**
- Can contain letters, digits, `_`, and `$`
- Cannot use **reserved keywords** (like `int`, `class`, `if`)
- Use **camelCase** for variables

```java
int robotSpeed;        // Good
int RobotSpeed;        // Allowed, but not standard
int 123speed;          // ❌ Invalid
```

---

## 5️⃣ Changing Variable Values

Variables can be **updated after declaration**:

```java
int motorSpeed = 100;
motorSpeed = 120;  // Update value
```

---

## 6️⃣ Constants (Final Variables)

- Use `final` to make a variable **unchangeable**
- By convention, constants use **UPPERCASE**

```java
final double MAX_SPEED = 5.0;
```

---

## 7️⃣ Examples in FRC Context

```java
int leftMotorSpeed = 100;    // Speed of the left motor
int rightMotorSpeed = 100;   // Speed of the right motor
boolean isAutonomous = true; // Is the robot in autonomous mode
final double WHEEL_DIAMETER = 6.0; // Inches
```

---

## 8️⃣ Best Practices

- Use **descriptive variable names** (`leftMotorSpeed` instead of `lms`)  
- Prefer **final constants** for fixed values  
- Initialize variables when declaring if possible  
- Keep related variables **grouped together** for readability
