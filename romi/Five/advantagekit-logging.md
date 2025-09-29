# AdvantageKit & Logging

## Intro
**AdvantageKit** is a logging, telemetry, and replay framework developed by FRC Team 6328 Mechanical Advantage. It enhances logging, provides telemetry visualization, and allows deterministic replay for robot testing and analysis.

## Goals
- Install and configure AdvantageKit
- Record subsystem and sensor data
- Use AdvantageScope to visualize data

### Features

* **Deterministic replay**: Replay robot code in simulation using recorded inputs.
* **Comprehensive logging**: Record joystick inputs, sensor values, and NetworkTables data.
* **Real-time telemetry**: Visualize robot data using AdvantageScope.

More info: [AdvantageKit GitHub repository](https://github.com/Mechanical-Advantage/AdvantageKit)

---

## Getting Started with AdvantageKit

### 1. Add Dependencies

Add AdvantageKit to your `build.gradle` dependencies:

```gradle
dependencies {
    implementation 'org.littletonrobotics.akit:akit-core:4.1.2'
    implementation 'org.littletonrobotics.akit:akit-autolog:4.1.2'
}
```

Replace `4.1.2` with the latest version.

### 2. Configure the Robot Class

Extend `LoggedRobot` and initialize logging:

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

### 3. Record Inputs and Outputs

Use AdvantageKit to log subsystem data:

```java
Logger.recordInput("Drive/LeftSpeed", leftMotor.get());
Logger.recordOutput("Drive/LeftSpeed", leftMotor.get());
```

This allows analysis and replay of subsystem performance.

---

## Replay and Telemetry

### Replay Logs

1. Ensure your robot code matches the version used during logging.
2. Use `WPILOGReader` to read logs:

```java
Logger.setReplaySource(new WPILOGReader("/path/to/logfile"));
```

### Visualize with AdvantageScope

* [AdvantageScope GitHub Repository](https://github.com/Mechanical-Advantage/AdvantageScope)
* Features:

  * Live data streaming
  * Replay analysis

---

## Additional Resources

* [AdvantageKit Documentation](https://docs.advantagekit.org)
* [AdvantageScope GitHub Repository](https://github.com/Mechanical-Advantage/AdvantageScope)
* [AdvantageKit Github Repository](https://github.com/Mechanical-Advantage/AdvantageKit)

---

This setup allows your FRC robot to have detailed telemetry, logging, and replay capabilities for debugging and improving robot performance.
