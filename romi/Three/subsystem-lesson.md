# Lesson: Understanding Subsystems in FRC (Java, WPILib)

## Overview

This lesson introduces students to **Subsystems** in the Command-Based robot framework.
Subsystems represent the hardware components of a robot (e.g., drivetrain, shooter, intake) and provide modular, reusable methods for commands to control them.

---

## Learning Objectives

By the end of this lesson, students will be able to:

1. Explain the purpose of subsystems in Command-Based programming.
2. Create a subsystem class in Java using WPILib.
3. Encapsulate hardware and expose control methods for commands.
4. Integrate subsystems with commands and default commands.

---

## Prerequisites

* Basic understanding of Java programming.
* WPILib installed with a working robot project.
* Familiarity with motor controllers, sensors, and the robot’s physical hardware.

---

## Key Concepts

### What is a Subsystem?

* Encapsulates a hardware component or mechanism.
* Provides public methods for commands to control the hardware.
* Supports default commands and ensures commands don’t conflict over the same hardware.

### Benefits

* Keeps robot code organized and modular.
* Makes code reusable and easier to test.
* Prevents conflicting commands from controlling the same hardware.

---

## Step 1: Create a Subsystem

### Example: Drivetrain Subsystem

```java
import edu.wpi.first.wpilibj2.command.SubsystemBase;
import edu.wpi.first.wpilibj.drive.DifferentialDrive;
import edu.wpi.first.wpilibj.motorcontrol.Spark;

public class Drivetrain extends SubsystemBase {
    private final Spark leftMotor = new Spark(0);
    private final Spark rightMotor = new Spark(1);
    private final DifferentialDrive drive = new DifferentialDrive(leftMotor, rightMotor);

    public Drivetrain() {
        // Initialize motors or sensors if needed
    }

    public void arcadeDrive(double forward, double rotation) {
        drive.arcadeDrive(forward, rotation);
    }
}
```

---

## Step 2: Create Commands for the Subsystem

### Example: DriveForward Command

```java
import edu.wpi.first.wpilibj2.command.CommandBase;
import edu.wpi.first.wpilibj.Timer;

public class DriveForward extends CommandBase {
    private final Drivetrain drivetrain;
    private final Timer timer = new Timer();

    public DriveForward(Drivetrain subsystem) {
        drivetrain = subsystem;
        addRequirements(drivetrain);
    }

    @Override
    public void initialize() {
        timer.reset();
        timer.start();
    }

    @Override
    public void execute() {
        drivetrain.arcadeDrive(0.5, 0.0);
    }

    @Override
    public void end(boolean interrupted) {
        drivetrain.arcadeDrive(0, 0);
    }

    @Override
    public boolean isFinished() {
        return timer.get() > 2.0;
    }
}
```

---

## Step 3: Bind Commands in RobotContainer

```java
private final Joystick controller = new Joystick(0);

private void configureButtonBindings() {
    new JoystickButton(controller, 1)
        .whenPressed(new DriveForward(drivetrain));
}
```

---

## Step 4: Best Practices

1. Keep each subsystem focused on a single mechanism.
2. Expose only the methods needed by commands.
3. Use default commands for continuous control (e.g., joystick driving).
4. Always use `addRequirements()` in commands to prevent conflicts.

---

## Step 5: Extension Ideas

* Create subsystems for shooter, intake, or arm mechanisms.
* Use encoders or gyros for feedback in subsystem methods.
* Combine multiple commands using `SequentialCommandGroup` or `ParallelCommandGroup`.

---

## Summary

Subsystems are essential building blocks of a well-structured Command-Based robot program.
They encapsulate hardware, simplify command creation, and help maintain clean, modular, and safe robot code.

---

## Resources

* [WPILib Subsystems Documentation](https://docs.wpilib.org/en/stable/docs/software/commandbased/subsystems.html)
* [WPILib Command-Based Programming Guide](https://docs.wpilib.org/en/stable/docs/software/commandbased/index.html)
