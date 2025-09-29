# Comparison Operators in Java

Comparison operators in Java are used to compare two values. They return a **boolean** value (`true` or `false`) and are often used in conditional statements like `if`, `while`, and `for` loops.

## List of Comparison Operators

| Operator | Description              | Example           |
| -------- | ------------------------ | ----------------- |
| `==`     | Equal to                 | `5 == 5` → `true` |
| `!=`     | Not equal to             | `5 != 3` → `true` |
| `>`      | Greater than             | `5 > 3` → `true`  |
| `<`      | Less than                | `5 < 3` → `false` |
| `>=`     | Greater than or equal to | `5 >= 5` → `true` |
| `<=`     | Less than or equal to    | `3 <= 5` → `true` |

## Examples

```java
int x = 10;
int y = 20;

boolean result1 = (x == y); // false
boolean result2 = (x != y); // true
boolean result3 = (x > y);  // false
boolean result4 = (x < y);  // true
boolean result5 = (x >= 10); // true
boolean result6 = (y <= 20); // true
```

## Using Comparison Operators in Conditional Statements

```java
int age = 18;
if (age >= 18) {
    System.out.println("You are an adult.");
} else {
    System.out.println("You are a minor.");
}
```

## Combining Comparison Operators with Logical Operators

You can combine comparison operators with logical operators (`&&`, `||`, `!`) for complex conditions.

```java
int x = 15;
int y = 10;
if (x > 10 && y < 20) {
    System.out.println("Both conditions are true.");
}
```

## Summary

* `==` → Equal to
* `!=` → Not equal to
* `>` → Greater than
* `<` → Less than
* `>=` → Greater than or equal to
* `<=` → Less than or equal to
* Often used in conditional statements and loops
* Can be combined with logical operators for complex conditions
