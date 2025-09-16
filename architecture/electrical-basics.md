# Electrical Basics (for programmers)

## Introduction
The **FIRST Robotics Competition (FRC) Control System** is the hardware and software that allows teams to control their robots.  
It connects driver inputs, robot code, and actuators (motors, pneumatics) to enable reliable competition operation.

---

## Goals
- Learn about motor controllers (TalonFX, SparkMAX)
- Understand sensors (encoders, gyros, limit switches)
- Overview of pneumatics
- Compare CAN vs. PWM connections

## Main Components

### 1. roboRIO
- The **central robot controller**, provided by NI (National Instruments).
- Runs the robot code deployed by the team (Java, C++, or Python).
- Connects to sensors, actuators, and CAN bus devices.
- Equipped with:
  - USB ports
  - Ethernet port
  - PWM, DIO, and Analog inputs
  - CAN bus interface

---

### 2. Power Distribution Hub (PDH) / PDP
- Distributes power from the main robot battery to all components.
- Includes circuit breakers for safety.
- Monitors voltage and current (useful for debugging and telemetry).

---

### 3. Pneumatics Hub (PH) / PCM
- Controls pneumatic solenoids and compressors.
- Connected via the CAN bus.

---

### 4. Motor Controllers
- Devices that interface between the roboRIO (via PWM or CAN) and motors.
- Common models: Talon FX, Spark MAX, Victor SPX.
- Provide features like:
  - Built-in PID control
  - Current limiting
  - Sensor feedback (encoders)

---

### 5. Sensors
- Provide feedback to the robot code.
- Common sensors:
  - **Encoders** (measure rotation, distance)
  - **Gyroscopes / IMUs** (measure orientation)
  - **Limit switches**
  - **Cameras** (for vision processing)

---

### 6. CAN Devices
- CAN (**Controller Area Network**) is a communication bus that allows multiple devices to talk to the roboRIO efficiently.  
- Advantages of CAN:
  - Faster communication compared to PWM/DIO.
  - Two-way data transfer (device → roboRIO, roboRIO → device).
  - Reduces wiring complexity.
- Common CAN devices in FRC:
  - **Motor Controllers** (Talon FX, Spark MAX, Victor SPX)
  - **Power Distribution Hub (PDH)** / **PDP**
  - **Pneumatics Hub (PH)** / **PCM**
  - **REV CAN-based sensors** (e.g., CAN encoders)
  - **CANcoders** for absolute position sensing
- Each device must have a **unique CAN ID**, configurable with vendor software (Phoenix Tuner, REV Hardware Client, etc.).

---

### 6. Driver Station
- Software that runs on the driver’s laptop.
- Communicates with the Field Management System (FMS).
- Allows human drivers/operators to control the robot via joysticks, gamepads, or custom control boards.
- Displays robot status (battery, connection, errors).

---

### 7. Radio
- Provides wireless communication between the robot and the Driver Station.
- Configured using the FRC Radio Configuration Tool.
- Operates on a secure, field-assigned Wi-Fi channel during competition.

---

## Control Flow
1. **Driver Inputs**: Commands are sent from joysticks/gamepads to the Driver Station.  
2. **Communication**: The Driver Station transmits inputs over Wi-Fi to the robot’s radio.  
3. **roboRIO Execution**: The roboRIO runs the team’s code, processes inputs, and determines actuator outputs.  
4. **Actuators & Feedback**: Motor controllers and pneumatics execute actions; sensors send data back to the roboRIO.  
5. **Telemetry**: Data is sent back to the Driver Station and displayed on Shuffleboard/SmartDashboard.

---

## Safety Features
- **Robot Signal Light (RSL)**: Indicates robot state (enabled, disabled, errors).  
- **E-Stop (Emergency Stop)**: Disables the robot immediately when pressed on the Driver Station or Field control.  
- **Circuit Protection**: Fuses and breakers protect electronics from damage.

---

## Summary
The FRC control system combines hardware (roboRIO, motor controllers, sensors, radio) and software (WPILib, Driver Station, FMS) to provide teams with a **reliable, safe, and competition-ready platform** for robot control.

---

## Resources
- [Official FRC Control System Documentation](https://docs.wpilib.org/en/stable/docs/controls-overviews/control-system-hardware.html)  
- [WPILib Documentation](https://docs.wpilib.org)  
