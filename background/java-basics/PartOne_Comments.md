# Java Basics: Comments

## Intro
Comments are used in Java to **explain code, make it more readable, and temporarily disable code**.  
They are ignored by the compiler and do not affect program execution.

---

## Single-Line Comments

- Start with `//`
- Used for short explanations or notes

```java
// This is a single-line comment
int speed = 100; // speed of the robot motor
```

## Multi-Line Comments

- Start with `/*` and ends with an `*/`
- Used for longer explanations

```java
/*
This is a multi-line comment.
You can write several lines of notes here.
Useful for explaining complex code sections.
*/
int motorCount = 4;
```

## Documentation Comments ( Javadocs )

- Start with `/**` and ends with an `*/`
- Used to autogenerate documentation with javadocs plugins
- Includes special tags like @param, @return, @throws , to define important details

```java
/**
 * Sets the speed of the motor.
 *
 * @param speed The desired speed in RPM.
 * @return true if the motor was set successfully.
 */
public boolean setMotorSpeed(int speed) {
    // Implementation goes here
    return true;
}
```

---

## Best Paractices
- Always comment why, not what - code itself should be readable
- Use javadoc for public methods and classes
- avoid excessive commenting; clear code reduces the need for comments with simple to read commetns
- use multi-line comments for sections of code that are temporarily disabled otherwise known as "commented out"

---


## An Example
```java
// Initialize the drivetrain motors
MotorController leftMotor = new MotorController(1);
MotorController rightMotor = new MotorController(2);

/*
  Calibrate sensors before starting the autonomous routine.
  Make sure the gyro is zeroed and encoders are reset.
*/
gyro.calibrate();
encoder.reset();
```

-- 

## Summary

| Comment Type   | Syntax        | Use Case                                      |
|----------------|---------------|----------------------------------------------|
| Single-line    | `// comment`  | Quick notes, inline explanations             |
| Multi-line     | `/* comment */` | Longer explanations, temporarily disable code |
| Documentation  | `/** comment */` | Auto-generated documentation, Javadoc      |