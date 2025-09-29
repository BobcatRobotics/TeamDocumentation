# Lesson: Command-Based Programming with WPILib on the ROMI Robot (Java)

## Intro
This lesson introduces students to **Command-Based Programming** using the **WPILib framework** on the **ROMI robot**.
Students will learn how to structure code with subsystems and commands, then implement basic autonomous and teleoperated behaviors.

---

## Goals
- Understand subsystems, commands, and RobotContainer
- Use dependency injection (`require()`)
- Write a simple command-based drivetrain program

## Learning Objectives

By the end of this lesson, students should be able to:

1. Understand the purpose of the Command-Based framework in WPILib.
2. Create subsystems for the ROMI drivetrain and onboard features.
3. Write commands to move the robot and react to inputs.
4. Test teleoperated and autonomous behaviors using the Driver Station or WPILib Simulation.

---

## Prerequisites

* Basic Java programming knowledge.
* WPILib installed and working development environment (VS Code with WPILib extension).
* ROMI robot set up and configured with Raspberry Pi and WPILibPi image.
* Familiarity with Git (optional, but recommended).

---

## Key Concepts

### What is Command-Based Programming?

* **Subsystems**: Represent major hardware components (e.g., drivetrain).
* **Commands**: Units of robot behavior that operate subsystems (e.g., drive forward, turn, stop).
* **Scheduler**: Runs commands, ensuring they don’t conflict over subsystems.
* **Benefits**:

  * Encourages modular, reusable code.
  * Easier to test and expand.
  * Scales well for competition robots.

---

## Step 1: Create a New WPILib Project

1. Open VS Code → WPILib: Create a new project.
2. Select **Template: Command-Based**.
3. Language: **Java**.
4. Project type: **Romi**.
5. Name your project `RomiCommandDemo`.

---

## Step 2: Define Subsystems

### Example: Drivetrain Subsystem (`Drivetrain.java`)

* Use the built-in `DifferentialDrive` class from WPILib.
* Connect it to the ROMI’s motors.

```java
public class Drivetrain extends SubsystemBase {
    private final DifferentialDrive drive;

    private final Spark leftMotor = new Spark(0);
    private final Spark rightMotor = new Spark(1);

    public Drivetrain() {
        drive = new DifferentialDrive(leftMotor, rightMotor);
    }

    public void arcadeDrive(double forward, double rotation) {
        drive.arcadeDrive(forward, rotation);
    }
}
```

---

## Step 3: Create Commands

### Example: Drive Forward Command

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
        drivetrain.arcadeDrive(0.5, 0.0); // drive forward at half speed
    }

    @Override
    public void end(boolean interrupted) {
        drivetrain.arcadeDrive(0, 0); // stop
    }

    @Override
    public boolean isFinished() {
        return timer.get() > 2.0; // stop after 2 seconds
    }
}
```

---

## Step 4: Bind Commands to Controls

In `RobotContainer.java`, set up controller bindings.

```java
private final Joystick controller = new Joystick(0);

private void configureButtonBindings() {
    new JoystickButton(controller, 1) // Button A
        .whenPressed(new DriveForward(drivetrain));
}
```

---

## Step 5: Autonomous Mode

In `RobotContainer.java`, return an autonomous command.

```java
public Command getAutonomousCommand() {
    return new DriveForward(drivetrain);
}
```

This makes the ROMI drive forward for 2 seconds during autonomous.

---

## Step 6: Test and Iterate

* Deploy code with **WPILib → Deploy Robot Code**.
* Run in **Teleop mode** and test button bindings.
* Run in **Autonomous mode** and verify the Drive Forward behavior.
* Expand by creating new commands:

  * Turn in place.
  * Drive in a square.
  * Follow joystick input continuously.

---

## Extensions

* Use **command groups** (`SequentialCommandGroup`, `ParallelCommandGroup`) for multi-step routines.
* Add the **Onboard Encoder** and **Gyro** from the ROMI for feedback-based commands.
* Create a **Default Command** for the drivetrain that maps joystick input to movement.

---

## Wrap-Up

Command-Based programming helps organize robot behavior into modular units that can be reused, combined, and tested.
The ROMI robot provides a safe, accessible way to practice these skills before applying them to a full FRC robot.

---

## Resources

* [WPILib Command-Based Programming Guide](https://docs.wpilib.org/en/stable/docs/software/commandbased/index.html)
* [Using the ROMI Robot](https://docs.wpilib.org/en/stable/docs/romi/index.html)
