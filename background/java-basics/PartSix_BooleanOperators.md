# Boolean Operators in Java

In Java, **boolean operators** are used to perform logical operations on boolean expressions (`true` or `false`). These operators are essential for controlling the flow of a program using conditional statements like `if`, `while`, and `for`.

## Boolean Data Type

A boolean variable can only hold one of two values:

```java
boolean isJavaFun = true;
boolean isFishTasty = false;
```

## Logical Operators

| Operator | Description | Example                   |            |        |   |                |
| -------- | ----------- | ------------------------- | ---------- | ------ | - | -------------- |
| `&&`     | Logical AND | `true && false` → `false` |            |        |   |                |
| \`       |             | \`                        | Logical OR | \`true |   | false`→`true\` |
| `!`      | Logical NOT | `!true` → `false`         |            |        |   |                |

### Examples

```java
boolean a = true;
boolean b = false;
boolean result;

result = a && b; // false
result = a || b; // true
result = !a;     // false
```

## Comparison Operators

| Operator | Description              | Example           |
| -------- | ------------------------ | ----------------- |
| `==`     | Equal to                 | `5 == 5` → `true` |
| `!=`     | Not equal to             | `5 != 3` → `true` |
| `>`      | Greater than             | `5 > 3` → `true`  |
| `<`      | Less than                | `5 < 3` → `false` |
| `>=`     | Greater than or equal to | `5 >= 5` → `true` |
| `<=`     | Less than or equal to    | `3 <= 5` → `true` |

Example:

```java
int x = 10;
int y = 20;
boolean result = (x < y) && (x != 0); // true
```

## Short-Circuit Operators

* `&&` stops evaluation if the first operand is `false`.
* `||` stops evaluation if the first operand is `true`.

```java
int a = 5;
int b = 0;
if (b != 0 && (a / b
```
