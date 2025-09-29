# Unit Testing in Java

Unit testing is the practice of testing individual units of source
code---such as methods or classes---to ensure they work as expected. In
Java, the most common framework for unit testing is **JUnit**.

------------------------------------------------------------------------

## Why Use Unit Testing?

-   **Early bug detection**: Problems are found before integrating code.
-   **Code confidence**: Ensures existing features work after changes.
-   **Documentation**: Tests serve as live examples of how code should
    behave.
-   **Maintainability**: Makes refactoring safer.

------------------------------------------------------------------------

## Getting Started with JUnit

JUnit is the de facto standard testing framework for Java. The current
version is **JUnit 5**, also known as **JUnit Jupiter**.

### Adding JUnit Dependency

If you're using Maven, add this to your `pom.xml`:

``` xml
<dependency>
  <groupId>org.junit.jupiter</groupId>
  <artifactId>junit-jupiter</artifactId>
  <version>5.10.0</version>
  <scope>test</scope>
</dependency>
```

If you're using Gradle:

``` gradle
testImplementation 'org.junit.jupiter:junit-jupiter:5.10.0'
```

------------------------------------------------------------------------

## Basic Test Example

Suppose you have a simple `Calculator` class:

``` java
public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
}
```

Here's how you'd write a unit test for it:

``` java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

class CalculatorTest {

    @Test
    void testAdd() {
        Calculator calc = new Calculator();
        int result = calc.add(2, 3);
        assertEquals(5, result, "2 + 3 should equal 5");
    }
}
```

------------------------------------------------------------------------

## Common JUnit Annotations

-   `@Test` → Marks a method as a test case.\
-   `@BeforeEach` → Runs before each test (setup).\
-   `@AfterEach` → Runs after each test (cleanup).\
-   `@BeforeAll` → Runs once before all tests (must be static).\
-   `@AfterAll` → Runs once after all tests (must be static).\
-   `@Disabled` → Skips a test.

------------------------------------------------------------------------

## Assertions

JUnit provides many built-in assertions to validate test results: -
`assertEquals(expected, actual)` - `assertTrue(condition)` -
`assertFalse(condition)` -
`assertThrows(Exception.class, () -> { ... })` - `assertNotNull(object)`

Example:

``` java
@Test
void testDivideByZero() {
    Calculator calc = new Calculator();
    assertThrows(ArithmeticException.class, () -> calc.divide(10, 0));
}
```

------------------------------------------------------------------------

## Best Practices

1.  **One concept per test**: Keep tests small and focused.\
2.  **Readable names**: Name tests descriptively
    (`testAddWithPositiveNumbers`).\
3.  **Avoid dependencies**: Don't rely on external services or
    databases.\
4.  **Automate tests**: Run them with CI/CD pipelines.\
5.  **Test edge cases**: Don't just test the "happy path."

------------------------------------------------------------------------

## Running Tests

-   In **IDE** (like IntelliJ, Eclipse, VS Code), right-click the test
    file and run.\

-   With **Gradlew**:

    ``` bash
    ./gradlew test
    ```

------------------------------------------------------------------------

## Summary

Unit testing in Java---most commonly done with JUnit---ensures
individual pieces of code work as expected. By writing small, focused
test cases, developers can improve code quality, detect bugs earlier,
and refactor safely.
