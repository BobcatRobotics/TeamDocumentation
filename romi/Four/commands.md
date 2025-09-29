# Commands

## Intro
In **Command-Based Programming**, a **Command** is a unit of behavior that acts on one or more **subsystems**.
Commands allow you to define robot actions such as moving the drivetrain, operating a shooter, or controlling an arm.

---

## Learning Objectives

By the end of this lesson, students will be able to:

1. Understand what a command is and how it interacts with subsystems.
2. Create a simple command in Java using WPILib.
3. Use command lifecycle methods: `initialize()`, `execute()`, `end()`, and `isFinished()`.
4. Bind commands to joystick buttons and use default commands.

---

## Key Concepts

### Types of Commands

* **InstantCommand**: Runs once and finishes immediately.
* **RunCommand**: Continuously runs a given action until interrupted.
* **CommandBase**: A custom command class that allows full control over the behavior.
* **Command Groups**:

  * **SequentialCommandGroup**: Runs multiple commands in sequence.
  * **ParallelCommandGroup**: Runs multiple commands at the same time.

### Command Lifecycle

1. `initialize()` — Called once when the command starts.
2. `execute()` — Called repeatedly while the command is running.
3. `isFinished()` — Returns `true` when the command should stop.
4. `end(boolean interrupted)` — Called when the command ends or is interrupted.

---

## Creating a Command

### Example: DriveForward Command

```java
import edu.wpi.first.wpilibj2.command.CommandBase;
import edu.wpi.first.wpilibj.Timer;

public class DriveForward extends CommandBase {
    private final Drivetrain drivetrain;
    private final Timer timer = new Timer();

    public DriveForward(Drivetrain subsystem) {
        drivetrain = subsystem;
        addRequirements(drivetrain); // Prevent conflicts
    }

    @Override
    public void initialize() {
        timer.reset();
        timer.start();
    }

    @Override
    public void execute() {
        drivetrain.arcadeDrive(0.5, 0.0); // drive forward
    }

    @Override
    public boolean isFinished() {
        return timer.get() > 2.0; // stop after 2 seconds
    }

    @Override
    public void end(boolean interrupted) {
        drivetrain.arcadeDrive(0, 0); // stop motors
    }
}
```

---

## Binding Commands to Buttons

```java
private final Joystick controller = new Joystick(0);

private void configureButtonBindings() {
    new JoystickButton(controller, 1) // Button A
        .whenPressed(new DriveForward(drivetrain)); // runs command when pressed
}
```

---

## Default Commands

* A **default command** runs automatically for a subsystem when no other command is using it.
* Example: Using joystick input to continuously control the drivetrain.

```java
drivetrain.setDefaultCommand(
    new RunCommand(() -> drivetrain.arcadeDrive(
        joystick.getY(), joystick.getX()), drivetrain)
);
```

---

## Best Practices

1. Use `addRequirements()` to declare subsystem usage.
2. Keep commands focused on a single task.
3. Use command groups for complex behaviors.
4. Reuse commands across teleop and autonomous modes when possible.

---

## Summary

Commands are the building blocks of robot behavior in WPILib’s Command-Based framework.
They interact with subsystems to perform actions and can be combined, scheduled, and bound to controls for modular, reusable, and safe robot code.

---

## Resources

* [WPILib Commands Guide](https://docs.wpilib.org/en/stable/docs/software/commandbased/commands.html)
* [WPILib Command-Based Programming Overview](https://docs.wpilib.org/en/stable/docs/software/commandbased/index.html)







