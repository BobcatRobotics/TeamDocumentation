# Unit Testing in WPILib Java

In **FRC (FIRST Robotics Competition)**, robot code is often complex,
with multiple subsystems, commands, and hardware interactions. Unit
testing allows teams to test their robot logic **without needing a
physical robot**. WPILib supports unit testing using **JUnit**.

------------------------------------------------------------------------

## Why Unit Test in WPILib?

-   **Test logic without hardware** (simulation environment).\
-   **Verify commands and subsystems** behave as expected.\
-   **Catch errors early** before deploying to the robot.\
-   **Safer refactoring** when making code changes.

------------------------------------------------------------------------

## Setting Up JUnit in WPILib

WPILib projects created with the official **VS Code + WPILib extension**
already include dependencies for JUnit. No extra setup is required.

Your tests should go in the `src/test/java` folder.

------------------------------------------------------------------------

## Example: Testing a Subsystem

Suppose you have a simple drivetrain subsystem:

``` java
import edu.wpi.first.wpilibj2.command.SubsystemBase;

public class DriveSubsystem extends SubsystemBase {
    private double speed = 0;

    public void setSpeed(double value) {
        speed = value;
    }

    public double getSpeed() {
        return speed;
    }
}
```

You can write a test for it like this:

``` java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

class DriveSubsystemTest {

    @Test
    void testSetAndGetSpeed() {
        DriveSubsystem drive = new DriveSubsystem();
        drive.setSpeed(0.5);
        assertEquals(0.5, drive.getSpeed(), 1e-9);
    }
}
```

------------------------------------------------------------------------

## Example: Testing Commands

Commands in WPILib are highly testable because they follow a lifecycle
(`initialize`, `execute`, `end`, `isFinished`).

For example, a simple command:

``` java
import edu.wpi.first.wpilibj2.command.CommandBase;

public class DriveCommand extends CommandBase {
    private final DriveSubsystem drive;

    public DriveCommand(DriveSubsystem subsystem) {
        drive = subsystem;
        addRequirements(drive);
    }

    @Override
    public void initialize() {
        drive.setSpeed(0.5);
    }

    @Override
    public void end(boolean interrupted) {
        drive.setSpeed(0);
    }
}
```

Test for the command:

``` java
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

class DriveCommandTest {

    @Test
    void testInitializeSetsSpeed() {
        DriveSubsystem drive = new DriveSubsystem();
        DriveCommand command = new DriveCommand(drive);

        command.initialize();
        assertEquals(0.5, drive.getSpeed(), 1e-9);
    }

    @Test
    void testEndStopsDrive() {
        DriveSubsystem drive = new DriveSubsystem();
        DriveCommand command = new DriveCommand(drive);

        command.initialize();
        command.end(false);
        assertEquals(0.0, drive.getSpeed(), 1e-9);
    }
}
```

------------------------------------------------------------------------

## Simulation in WPILib Testing

For more complex subsystems (like motors, sensors, encoders), WPILib
provides **simulation classes** (e.g., `PWMSim`, `EncoderSim`,
`SimDevice`).

These allow you to test hardware interactions without real hardware. For
example:

``` java
import edu.wpi.first.wpilibj.Encoder;
import edu.wpi.first.wpilibj.simulation.EncoderSim;
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

class EncoderTest {

    @Test
    void testEncoderSimulation() {
        Encoder encoder = new Encoder(0, 1);
        EncoderSim encoderSim = new EncoderSim(encoder);

        encoderSim.setDistance(42.0);
        assertEquals(42.0, encoder.getDistance(), 1e-9);
    }
}
```

------------------------------------------------------------------------

## Running Tests

-   In **VS Code (WPILib Extension)**:

    -   Open the Command Palette → `WPILib: Run Tests`.\

-   With **Gradle**:

    ``` bash
    ./gradlew test
    ```

------------------------------------------------------------------------

## Best Practices

1.  **Test subsystems in isolation** (no external dependencies).\
2.  **Mock or simulate hardware** instead of requiring a robot.\
3.  **Keep tests fast** (avoid delays and long loops).\
4.  **Test commands' lifecycle** (`initialize`, `execute`, `end`).\
5.  **Integrate tests in CI/CD** so they run automatically.

------------------------------------------------------------------------

## Summary

Unit testing in WPILib Java uses **JUnit** and WPILib's simulation
tools. By writing subsystem and command tests, FRC teams can validate
robot behavior early, reduce debugging time, and increase reliability
both on and off the field.


## Activity

Given the example above , create a new romi robot project and add a unittest that validates your drive train system.
Demonstrate that your unittest executes and all your tests pass.

1.  **Turn Left Command** validate that the actual directions of each corresponding motor are turning the expected direction.\
2.  **Turn Right Command** validate that the actual directions of each corresponding motor are turning the expected direction.\
3.  **Drive Forward Command** validate that both motors are are turning in the expected direction.\
4.  **Drive Reverse/Backwards Comamnd** validate that both motors are are turning in the expected direction.\
5.  **Expected commands have executed in sequence correctly** validate that each command has successfully completed in sequence ( forward, right , left , reverse )