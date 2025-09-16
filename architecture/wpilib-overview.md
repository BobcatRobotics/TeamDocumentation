# WPILib Overview

## Introduction
WPILib (WPI Library) is the official software library used in the **FIRST Robotics Competition (FRC)**.  
It provides a set of tools, APIs, and frameworks that help teams write reliable robot code in **Java, C++, or Python (via RobotPy)**.

---
## Goals
- Understand `Robot.java` and `Main.java`
- Learn robot lifecycle methods (init, periodic, disabled, teleop, autonomous)
- Introduction to command-based programming

## Key Features
- **Hardware Abstraction**  
  Provides APIs to control motors, sensors, pneumatics, and other robot hardware.

- **Command-Based Framework**  
  Encourages modular, reusable, and testable robot code through commands and subsystems.

- **Simulation Support**  
  Allows teams to test robot code without access to the physical robot using desktop simulation tools.

- **Built-In Tools**  
  - Driver Station  
  - SmartDashboard / Shuffleboard for telemetry  
  - PathWeaver for trajectory planning  
  - Robot Characterization tools ( sysid )
  - AdvantageScope -> data visualization and logging

- **Cross-Platform**  
  Works across Windows, macOS, and Linux, with deployment to the roboRIO (robot controller).

---

## Languages Supported
- **Java** (most commonly used, full support)  
- **C++** (full support, lower-level control)  
- **Python (RobotPy)** – community-supported implementation of WPILib.

---

## Typical WPILib Project Structure
- `Robot.java` / `Robot.cpp` – Main entry point for the robot program.  
- **Subsystems** – Encapsulate hardware (e.g., drivetrain, arm).  
- **Commands** – Define actions for subsystems (e.g., drive forward, shoot ball).  
- **OI / Input** – Handles driver and operator controls.

---

## Why WPILib Matters
- **Standardization**: Ensures all teams have a reliable foundation.  
- **Educational**: Introduces students to software engineering best practices.  
- **Community Support**: Large FRC community contributes examples, extensions, and tutorials.  
- **Competition Ready**: Code runs directly on the **NI roboRIO**, the controller used in official FRC robots.

---

## Resources
- [WPILib Official Documentation](https://docs.wpilib.org)  
- [WPILib GitHub](https://github.com/wpilibsuite/allwpilib)  
- [FRC Control System Overview](https://docs.wpilib.org/en/stable/docs/controls-overviews/control-system-hardware.html)

---
