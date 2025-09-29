# Lesson: Integrating AdvantageKit into a New FRC Robot Project (Java)

## Overview

This lesson teaches students how to **integrate AdvantageKit** into a new Java-based FRC robot project. AdvantageKit provides **logging, telemetry, and replay** functionality, which helps in debugging and analyzing robot performance.

---

## Learning Objectives

By the end of this lesson, students will be able to:

1. Understand the purpose and benefits of AdvantageKit.
2. Set up AdvantageKit in a new robot project.
3. Log subsystem inputs and outputs.
4. Use AdvantageKit to monitor telemetry in real-time and replay logs for analysis.

---

## Prerequisites

* WPILib installed and working.
* Basic understanding of Java and Command-Based programming.
* Familiarity with subsystems and commands.

---

## Step 1: Create a New Robot Project

1. Open VS Code with WPILib extension.
2. Create a new robot project (Command-Based, Java).
3. Verify that the project builds and deploys to a practice robot or simulator.

---

## Step 2: Add AdvantageKit Dependencies

Edit your `build.gradle` file to include AdvantageKit dependencies:

```gradle
dependencies {
    implementation 'org.littletonrobotics.akit:akit-core:4.1.2'
    implementation 'org.littletonrobotics.akit:akit-autolog:4.1.2'
}
```

> Replace `4.1.2` with the latest version available.

---

## Step 3: Configure AdvantageKit in Robot.java

Modify the `Robot` class to extend `LoggedRobot`:

```java
import org.littletonrobotics.junction.LoggedRobot;
import org.littletonrobotics.junction.Logger;
import org.littletonrobotics.junction.datafile.WPILOGWriter;

public class Robot extends LoggedRobot {
    @Override
    public void robotInit() {
        Logger.recordMetadata("ProjectName", "MyRobot");
        Logger.addDataReceiver(new WPILOGWriter("/U/logs"));
    }

    @Override
    public void robotPeriodic() {
        Logger.updateInputs();
    }

    @Override
    public void disabledInit() {
        Logger.stop();
    }
}
```

---

## Step 4: Log Subsystem Data

In each subsystem, record important inputs and outputs:

```java
public class Drivetrain extends SubsystemBase {
    private final Spark leftMotor = new Spark(0);
    private final Spark rightMotor = new Spark(1);

    public void arcadeDrive(double forward, double rotation) {
        leftMotor.set(forward + rotation);
        rightMotor.set(forward - rotation);

        // Log motor outputs
        Logger.getInstance().recordOutput("Drivetrain/LeftMotor", leftMotor.get());
        Logger.getInstance().recordOutput("Drivetrain/RightMotor", rightMotor.get());
    }
}
```

---

## Step 5: Log Commands

Record command execution for debugging:

```java
public class DriveForward extends CommandBase {
    @Override
    public void initialize() {
        Logger.getInstance().recordOutput("DriveForward/Status", "Started");
    }

    @Override
    public void end(boolean interrupted) {
        Logger.getInstance().recordOutput("DriveForward/Status", interrupted ? "Interrupted" : "Finished");
    }
}
```

---

## Step 6: Replay and Telemetry

* Logs are saved to `/U/logs` on the robot.
* Use **AdvantageScope** to view telemetry and replay logs:
  [AdvantageScope GitHub](https://github.com/Mechanical-Advantage/AdvantageScope)

---

## Step 7: Best Practices

1. Log meaningful data (subsystems, sensors, commands).
2. Avoid logging excessively to prevent performance issues.
3. Use consistent naming for all keys (e.g., `Subsystem/Variable`).
4. Review logs after testing or matches to improve robot performance.

---

## Summary

Integrating AdvantageKit into a new robot project allows teams to **monitor, debug, and analyze** robot performance effectively.
Using logging, telemetry, and replay, teams gain a better understanding of robot behavior and can make data-driven improvements.

---

## Resources

* [AdvantageKit Documentation](https://docs.advantagekit.org)
* [AdvantageScope GitHub Repository](https://github.com/Mechanical-Advantage/AdvantageScope)
* [AdvantageKit GitHub Repository](https://github.com/Mechanical-Advantage/AdvantageKit)
