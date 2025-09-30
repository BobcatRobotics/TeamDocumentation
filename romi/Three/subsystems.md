# Subsystems

## Introduction

In **Command-Based Programming**, a **Subsystem** represents a distinct hardware component or group of components on the robot.
Subsystems encapsulate the robot's hardware (motors, sensors, solenoids) and provide methods for controlling them. This keeps code organized, modular, and reusable.

---

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

---

### Step 2: Define the Subsystem Properties

Example: `Drivetrain` subsystem from the RomiReference Example.

```java
  private static final double kCountsPerRevolution = 1440.0;
  private static final double kWheelDiameterInch = 2.75591; // 70 mm

  // The Romi has the left and right motors set to
  // PWM channels 0 and 1 respectively
  private final Spark m_leftMotor = new Spark(0);
  private final Spark m_rightMotor = new Spark(1);

  // The Romi has onboard encoders that are hardcoded
  // to use DIO pins 4/5 and 6/7 for the left and right
  private final Encoder m_leftEncoder = new Encoder(4, 5);
  private final Encoder m_rightEncoder = new Encoder(6, 7);

  // Set up the differential drive controller
  private final DifferentialDrive m_diffDrive =
      new DifferentialDrive(m_leftMotor::set, m_rightMotor::set);

  // Set up the RomiGyro
  private final RomiGyro m_gyro = new RomiGyro();

  // Set up the BuiltInAccelerometer
  private final BuiltInAccelerometer m_accelerometer = new BuiltInAccelerometer();
```

---

### Step 3: Define the Subsystem constructor

Constructor must implement any 'final' properties.
Set up or configure any motors , encoders, sensors.

---

### Step 4: Define the Subsystem methods

Implement any methods , almost always include a manual control mode 
as well as methods to read encoders and stop any motors.

---

### Step 5: Define the Subsystem Commands

Implement any commands to automate specific features. For example automating the control of a motor to a specific velocity or position.

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
