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

## Step 1: Drivetrain Subsystem Imports

```java
import edu.wpi.first.wpilibj2.command.SubsystemBase;
import edu.wpi.first.wpilibj.drive.DifferentialDrive;
import edu.wpi.first.wpilibj.motorcontrol.Spark;
```

---

## Step 2: Drivetrain Subsystem Properties

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

## Step 3: Create Constructor for the subsystem

```java
  /** Creates a new Drivetrain. */
  public Drivetrain() {
    SendableRegistry.addChild(m_diffDrive, m_leftMotor);
    SendableRegistry.addChild(m_diffDrive, m_rightMotor);

    // We need to invert one side of the drivetrain so that positive voltages
    // result in both sides moving forward. Depending on how your robot's
    // gearbox is constructed, you might have to invert the left side instead.
    m_rightMotor.setInverted(true);

    // Use inches as unit for encoder distances
    m_leftEncoder.setDistancePerPulse((Math.PI * kWheelDiameterInch) / kCountsPerRevolution);
    m_rightEncoder.setDistancePerPulse((Math.PI * kWheelDiameterInch) / kCountsPerRevolution);
    resetEncoders();
  }
```

---

## Step 4: Create methods

```java
  public void arcadeDrive(double xaxisSpeed, double zaxisRotate) {
    m_diffDrive.arcadeDrive(xaxisSpeed, zaxisRotate);
  }
  public void resetEncoders() {
    m_leftEncoder.reset();
    m_rightEncoder.reset();
  }
```

---

## Step 5: Best Practices

1. Keep each subsystem focused on a single mechanism.
2. Expose only the methods needed by commands.
3. Use default commands for continuous control (e.g., joystick driving).
4. Always use `addRequirements()` in commands to prevent conflicts.

---

## Step 5: Extension Ideas
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
