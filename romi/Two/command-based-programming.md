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
5. Name your project `LessonTwo`.

---

## Step 2: Define Subsystems

### Example: Drivetrain Subsystem (`Drivetrain.java`)

* Use the built-in `DifferentialDrive` class from WPILib.
* Connect it to the ROMI’s motors.

---

## Step 3: Create Commands

### Example: Arcade Drive Command

This command when executed will accept input from two joysticks and drive accordingly.

```java
public class ArcadeDrive extends Command {
  private final Drivetrain m_drivetrain;
  private final Supplier<Double> m_xaxisSpeedSupplier;
  private final Supplier<Double> m_zaxisRotateSupplier;

  /**
   * Creates a new ArcadeDrive. This command will drive your robot according to the speed supplier
   * lambdas. This command does not terminate.
   *
   * @param drivetrain The drivetrain subsystem on which this command will run
   * @param xaxisSpeedSupplier Lambda supplier of forward/backward speed
   * @param zaxisRotateSupplier Lambda supplier of rotational speed
   */
  public ArcadeDrive(
      Drivetrain drivetrain,
      Supplier<Double> xaxisSpeedSupplier,
      Supplier<Double> zaxisRotateSupplier) {
    m_drivetrain = drivetrain;
    m_xaxisSpeedSupplier = xaxisSpeedSupplier;
    m_zaxisRotateSupplier = zaxisRotateSupplier;
    addRequirements(drivetrain);
  }

  // Called when the command is initially scheduled.
  @Override
  public void initialize() {}

  // Called every time the scheduler runs while the command is scheduled. Takes in the joystick values as the speed and rotation of the romi.
  @Override
  public void execute() {
    m_drivetrain.arcadeDrive(m_xaxisSpeedSupplier.get(), m_zaxisRotateSupplier.get());
  }

  // Called once the command ends or is interrupted.
  @Override
  public void end(boolean interrupted) {}

  // Returns true when the command should end.
  @Override
  public boolean isFinished() {
    return false;
  }
}
```

---

## Step 4: Bind Commands to Controls

In `RobotContainer.java`, set up controller bindings. drivetrain is the instance of the subysystem.

```java
private final Drivetrain m_drivetrain = new Drivetrain();
private final Joystick m_controller = new Joystick(0);

private void configureButtonBindings() {
    drivetrain.setDefaultCommand(new ArcadeDrive(
        drivetrain, () -> -m_controller.getRawAxis(1), () -> -m_controller.getRawAxis(2))));
}
```

---

## Step 5: Autonomous Mode

In `RobotContainer.java`, return an autonomous command.

```java
public Command getAutonomousCommand() {
    return new ArcadeDrive(
        drivetrain, () -> -1, () -> 0);
}
```

This makes the ROMI drive forward during autonomous.

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

---

## Wrap-Up

Command-Based programming helps organize robot behavior into modular units that can be reused, combined, and tested.
The ROMI robot provides a safe, accessible way to practice these skills before applying them to a full FRC robot.

---

## Resources

* [WPILib Command-Based Programming Guide](https://docs.wpilib.org/en/stable/docs/software/commandbased/index.html)
* [Using the ROMI Robot](https://docs.wpilib.org/en/stable/docs/romi/index.html)
