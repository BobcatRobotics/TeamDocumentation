# Subsystems

## Introduction

In **Command-Based Programming**, a **Subsystem** represents a distinct hardware component or group of components on the robot.
Subsystems encapsulate the robot's hardware (motors, sensors, solenoids) and provide methods for controlling them. This keeps code organized, modular, and reusable.

---
## Goals
- Write a drivetrain subsystem
- Write an arm subsystem
- Assign default commands to subsystems

## Key Concepts

* **Encapsulation**: Subsystems hide the low-level hardware details from commands.
* **Default Commands**: Each subsystem can have a default command that runs when no other command is using it.
* **Requirements**: Commands specify which subsystems they use to prevent conflicts.

---

## Creating a Subsystem in Java

### Step 1: Import Libraries

```java
import edu.wpi.first.wpilibj2.command.SubsystemBase;
import edu.wpi.first.wpilibj.drive.DifferentialDrive;
import edu.wpi.first.wpilibj.motorcontrol.Spark;
```

### Step 2: Define the Subsystem Class

Example: `Drivetrain` subsystem for a differential drive robot.

```java
public class Drivetrain extends SubsystemBase {
    private final Spark leftMotor = new Spark(0);
    private final Spark rightMotor = new Spark(1);
    private final DifferentialDrive drive = new DifferentialDrive(leftMotor, rightMotor);

    // Constructor
    public Drivetrain() {
        // Initialization code here
    }

    // Method to drive the robot using arcade controls
    public void arcadeDrive(double forward, double rotation) {
        drive.arcadeDrive(forward, rotation);
    }
}
```

---

## Best Practices

1. **Keep subsystems modular**

   * Each subsystem should represent a specific robot mechanism (e.g., drivetrain, shooter, intake).

2. **Expose only necessary methods**

   * Commands interact with the subsystem through public methods (e.g., `arcadeDrive()`), not by directly manipulating motors or sensors.

3. **Use default commands for continuous control**

   * For example, the drivetrain’s default command can read joystick input continuously.

4. **Use `addRequirements()` in commands**

   * Ensures that commands don’t conflict by trying to control the same subsystem simultaneously.

---

## Example: Shooter Subsystem

```java
import edu.wpi.first.wpilibj2.command.SubsystemBase;
import edu.wpi.first.wpilibj.motorcontrol.Spark;

public class Shooter extends SubsystemBase {
    private final Spark shooterMotor = new Spark(2);

    public void runShooter(double speed) {
        shooterMotor.set(speed);
    }

    public void stopShooter() {
        shooterMotor.stopMotor();
    }
}
```

---

## Integrating Subsystems with Commands

* Commands call the subsystem’s public methods to control hardware.
* Example: a `ShootBall` command could call `shooter.runShooter(1.0)` in its `execute()` method.
* This separation makes code cleaner, testable, and reusable.

---

## Summary

* Subsystems are the backbone of the Command-Based robot structure.
* They encapsulate hardware and provide methods for commands to interact with the robot safely.
* Proper use of subsystems improves code organization, reduces bugs, and simplifies complex robot behaviors.

---

## Activity

* Move on too the subsystem lesson at [Student Activity](subsystem-lesson.md) 

---

## Resources

* [WPILib Command-Based Programming Guide](https://docs.wpilib.org/en/stable/docs/software/commandbased/index.html)
* [WPILib Subsystem Reference](https://docs.wpilib.org/en/stable/docs/software/commandbased/subsystems.html)
