# Simulation

## Intro
Simulation in WPILib allows FRC teams to **test and debug robot code without physical hardware**.
Using the WPILib Simulator, you can simulate robot subsystems, sensors, and commands directly on your computer.
This is particularly useful for early development, debugging, or practicing autonomous routines safely.

---
## Goals
By the section you should be able too:

1. Understand the purpose of simulation in FRC.
2. Set up a WPILib robot project for simulation.
3. Simulate drivetrain, sensors, and commands.
4. Visualize telemetry in the simulator and debug code without the robot.

---

## Benefits of Simulation

* **Early Testing**: Verify code logic before deploying to the robot.
* **Safe Development**: Test autonomous and complex routines without risking hardware damage.
* **Continuous Integration**: Combine with CI pipelines for automated testing.
* **Telemetry Visualization**: Use simulated sensors and Shuffleboard for monitoring.

---

## Setting Up Simulation

### Step 1: Create a Command-Based Robot Project

1. Open VS Code with the WPILib extension.
2. Create a **Command-Based Java project**.
3. Select the **Simulation** target when prompted, or later in `build.gradle`.

### Step 2: Enable Simulation in VS Code

* Open the **WPILib Simulation** panel.
* Click **Simulate Robot Code**.
* The simulator will launch a virtual robot environment.

---

## Simulating Subsystems

### Drivetrain Example

```java
public class Drivetrain extends SubsystemBase {
    private final PWMVictorSPX leftMotor = new PWMVictorSPX(0);
    private final PWMVictorSPX rightMotor = new PWMVictorSPX(1);

    public void arcadeDrive(double forward, double rotation) {
        leftMotor.set(forward + rotation);
        rightMotor.set(forward - rotation);
    }
}
```

* Motors automatically respond in the simulator.
* You can observe motion in the **simulated 2D field**.

### Sensor Simulation

* Many sensors have simulation classes:

  * `EncoderSim` for encoders
  * `GyroSim` for gyroscopes
  * `PWM/DIO/Analog` simulation for motor controllers and switches

```java
EncoderSim leftEncoderSim = new EncoderSim(leftEncoder);
leftEncoderSim.setDistance(5.0); // Simulate 5 meters traveled
```

---

## Simulating Commands

* Commands work the same way in simulation as on the robot.
* Example: Autonomous routine simulation:

```java
SequentialCommandGroup autoRoutine = new SequentialCommandGroup(
    new DriveForward(drivetrain, 2.0),
    new Turn(drivetrain, 90)
);
autoRoutine.schedule();
```

* You can watch the robot follow the sequence in the simulator.

---

## Using Telemetry in Simulation

* Shuffleboard can display simulated sensor values in real time.
* NetworkTables entries are updated by the simulator, just like the real robot.
* AdvantageKit can also log simulated data for analysis.

---

## Best Practices

1. Always test autonomous routines in simulation before using the physical robot.
2. Simulate sensors and motors as accurately as possible.
3. Combine simulation with logging to verify expected behaviors.
4. Remember that some physical interactions (like friction or collisions) may not be perfectly simulated.

---

## Summary

Simulation in WPILib is a powerful tool for **developing, testing, and debugging** FRC Java code without hardware.
It allows teams to build confidence in robot behaviors, test autonomous routines, and integrate telemetry systems before going to the field.

---

## Resources

* [WPILib Simulation Documentation](https://docs.wpilib.org/en/stable/docs/software/simulation/index.html)
* [WPILib API for Java](https://first.wpi.edu/wpilibj/)
* \[FRC Java Tutorials on Simulation]\([https://docs.wpilib.org/en/stable/docs/software/tutorials/index.h](https://docs.wpilib.org/en/stable/docs/software/tutorials/index.h)
