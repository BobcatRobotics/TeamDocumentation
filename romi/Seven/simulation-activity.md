# Simulating CTRE Products in WPILib (FRC Java)

## Overview

CTRE (Cross The Road Electronics) produces popular FRC devices like the **Talon SRX, Talon FX (Falcon 500), and Victor SPX**.
WPILib supports **simulation of these devices**, allowing teams to test motor control and sensor integration without a physical robot.

---

## Learning Objectives

By the end of this lesson, students will be able to:

1. Understand how CTRE devices can be simulated in WPILib.
2. Use CTRE simulation classes to mimic motor and sensor behavior.
3. Integrate simulated motor feedback into robot code for testing and debugging.

---

## Supported Devices

* **Talon SRX**
* **Victor SPX**
* **Talon FX (Falcon 500)**
* **Pigeon IMU**

> Note: Some advanced features like closed-loop control may require additional setup in simulation.

---

## Setting Up CTRE Simulation

### 1. Add Dependencies

Ensure your `build.gradle` includes CTRE Phoenix libraries:

```gradle
dependencies {
    implementation "com.ctre.phoenix:services:7.0.5"
}
```

Replace `7.0.5` with the latest version.

---

### 2. Import Simulation Classes

CTRE Phoenix provides `sim` classes for key devices:

```java
import com.ctre.phoenix.motorcontrol.can.TalonFX;
import com.ctre.phoenix.motorcontrol.can.TalonFXSimCollection;
import com.ctre.phoenix.sensors.PigeonIMU;
import com.ctre.phoenix.sensors.PigeonIMUSimCollection;
```

---

### 3. Create and Simulate Motors

```java
// Create TalonFX motor
TalonFX motor = new TalonFX(1);

// Create simulation collection
TalonFXSimCollection motorSim = motor.getSimCollection();

// Set simulated motor outputs
motorSim.setSupplyCurrent(30.0);   // Simulate current draw
motorSim.setBusVoltage(12.0);      // Simulate voltage
motorSim.setQuadraturePosition(2048); // Simulate encoder counts
```

---

### 4. Simulate Sensors

#### Pigeon IMU Example

```java
PigeonIMU imu = new PigeonIMU(0);
PigeonIMUSimCollection imuSim = imu.getSimCollection();

// Simulate yaw angle
imuSim.setRawHeading(90.0);
```

* You can also simulate pitch and roll angles for testing autonomous routines.

---

## Integrating Simulation into Robot Code

* Motors and sensors behave like real hardware in code.
* Example with drivetrain subsystem:

```java
public class Drivetrain extends SubsystemBase {
    private final TalonFX leftMotor = new TalonFX(1);
    private final TalonFX rightMotor = new TalonFX(2);

    public void arcadeDrive(double forward, double rotation) {
        leftMotor.set(ControlMode.PercentOutput, forward + rotation);
        rightMotor.set(ControlMode.PercentOutput, forward - rotation);
    }

    public void simulate(double deltaTime) {
        // Update simulated encoder positions
        TalonFXSimCollection leftSim = leftMotor.getSimCollection();
        leftSim.setQuadraturePosition(leftSim.getQuadraturePosition() + 100 * deltaTime);

        TalonFXSimCollection rightSim = rightMotor.getSimCollection();
        rightSim.setQuadraturePosition(rightSim.getQuadraturePosition() + 100 * deltaTime);
    }
}
```

---

## Best Practices

1. Use **simulation classes** (`TalonFXSimCollection`, `PigeonIMUSimCollection`) to test autonomous routines.
2. Combine with WPILib simulation for full robot behavior.
3. Use **small time steps** (`deltaTime`) to update simulated positions and velocities accurately.
4. Record telemetry with AdvantageKit or Shuffleboard for validation.

---

## Summary

Simulating CTRE devices in WPILib allows teams to **test motor controllers and sensors without hardware**, providing a safe and efficient way to debug robot code, validate autonomous routines, and integrate with telemetry systems.

---

## Resources

* [CTRE Phoenix Documentation](https://www.ctr-electronics.com/)
* [WPILib Simulation Documentation](https://docs.wpilib.org/en/stable/docs/software/simulation/index.html)
* [FRC TalonFX Simulation Example](https://github.com/wpilibsuite/allwpilib/tree/main/wpilibjExamples/src/main/java/edu/wpi/first/wpil)
