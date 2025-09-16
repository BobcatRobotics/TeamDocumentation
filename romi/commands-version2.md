# WPILib New Commands Framework (Java, FRC)

## Overview

The **New Commands Framework** in WPILib simplifies creating and managing robot actions using **subsystems** and **commands**.
It standardizes command scheduling, allows default commands, and integrates with modern Java features like lambdas.

---

## Learning Objectives

By the end of this lesson, students will be able to:

1. Understand the structure of the new Commands Framework.
2. Create commands using `CommandBase` and functional interfaces.
3. Use `addRequirements()` to prevent conflicts.
4. Combine commands with `SequentialCommandGroup` and `ParallelCommandGroup`.
5. Bind commands to joystick buttons using lambdas.

---

## Key Concepts

### Command Lifecycle

1. `initialize()` — Runs once when the command starts.
2. `execute()` — Runs repeatedly while the command is active.
3. `isFinished()` — Returns `true` when the command should stop.
4. `end(boolean interrupted)` — Called when the command ends or is interrupted.

### New Features

* **Functional commands**: Use lambdas instead of full classes for simple actions.
* **Improved scheduling**: Commands automatically start and stop based on subsystem requirements.
* **Simpler binding**: Bind commands directly to joystick buttons using lambda expressions.

---

## Creating Commands

### Traditional Command Class

```java
public class DriveForward extends CommandBase {
    private final Drivetrain drivetrain;
    private final Timer timer = new Timer();

    public DriveForward(Drivetrain subsystem) {
        drivetrain = subsystem;
        addRequirements(drivetrain);
    }

    @Override
    public void initialize() {
        timer.reset();
        timer.start();
    }

    @Override
    public void execute() {
        drivetrain.arcadeDrive(0.5, 0);
    }

    @Override
    public boolean isFinished() {
        return timer.get() > 2.0;
    }

    @Override
    public void end(boolean interrupted) {
        drivetrain.arcadeDrive(0, 0);
    }
}
```

### Functional Command (Lambda-Based)

```java
Command driveForward = new RunCommand(
    () -> drivetrain.arcadeDrive(0.5, 0),
    drivetrain
).withTimeout(2.0);
```

---

## Command Groups

### Sequential Commands

```java
SequentialCommandGroup autoRoutine = new SequentialCommandGroup(
    new DriveForward(drivetrain),
    new Turn(drivetrain, 90),
    new DriveForward(drivetrain)
);
```

### Parallel Commands

```java
ParallelCommandGroup intakeAndDrive = new ParallelCommandGroup(
    new RunIntake(intake),
    new DriveForward(drivetrain)
);
```

---

## Binding Commands to Controls

```java
Joystick joystick = new Joystick(0);

// Using lambdas
new JoystickButton(joystick, 1)
    .whenPressed(() -> drivetrain.arcadeDrive(0.5, 0))
    .whenReleased(() -> drivetrain.arcadeDrive(0, 0));
```

---

## Best Practices

1. Use functional commands for simple one-line actions.
2. Keep command classes for reusable or complex behaviors.
3. Always use `addRequirements()` to prevent conflicts.
4. Combine commands using groups for autonomous routines.
5. Set default commands for subsystems that require continuous input.

---

## Summary

The **New Commands Framework** in WPILib streamlines robot behavior programming with modern Java features.
It encourages modularity, reusability, and simplifies command scheduling, making it easier for teams to write safe and maintainable robot code.

---

## Resources

* [WPILib New Commands Documentation](https://docs.wpilib.org/en/stable/docs/software/commandbased/commands.html)
* [WPILib Functional Commands Guide](https://docs.wpilib.org/en/stable/docs/software/commandbased/functional-commands.html)
