# Homework Assignment: Understanding Subsystems in FRC Java (WPILib)

## Overview
In FRC robot code, **subsystems** represent major hardware components of the robot.  
They allow programmers to organize code in a structured and modular way, so that different parts of the robot can be controlled independently.

---

## What is a Subsystem?
- A **subsystem** is a class that represents a **hardware component** or **mechanical system** on the robot.  
- Examples of subsystems:
  - Drivetrain (motors that move the robot)
  - Shooter (flywheels, motors that launch balls)
  - Intake (rollers that bring game pieces into the robot)
  - Climber (motors and arms for climbing)

Each subsystem:
- Extends the `SubsystemBase` class from WPILib.
- Contains:
  - Motor/controller objects (e.g., `PWMSparkMax`, `TalonFX`).
  - Sensor objects (e.g., encoders, gyros).
  - Methods to control that subsystem (e.g., `driveForward()`, `shootBall()`).
  - Commands to automate actions
---

## Why Use Subsystems?
- **Encapsulation**: Keeps hardware logic in one place.
- **Reusability**: Commands can call subsystem methods without duplicating code.
- **Safety**: WPILib’s scheduler ensures that only one command at a time controls a subsystem.
- **Scalability**: Makes complex robot code easier to manage during competitions.
