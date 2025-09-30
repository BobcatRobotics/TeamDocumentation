# Activity: Command-Based Programming with WPILib on the ROMI Robot

## Overview
In this activity, you will apply **Command-Based Programming** concepts to control the **ROMI robot** using WPILib.  
You will design subsystems and commands, bind them to controller inputs, and test both **teleoperated** and **autonomous** behaviors.

---

## Activity Goals
- Understand the **Drivetrain subsystem** for the ROMI.
- Understand the **ArcadeDrive command** to drive with joystick inputs.
- Configure **controller bindings** for teleop control.
- Implement a simple **autonomous command** to drive forward.
- Implement a simple **autonomous command** to turn in place.
- Implement a simple **autonomous command** to drive forward , turn right , drive forward, turn right , and finally drive forward.
- Test, debug, and expand your code.

---

## Steps

### Step 1: Create Your Project
1. Open **VS Code** → **WPILib: Create a new project**.
2. Choose:
   - **Template**: Command-Based  
   - **Language**: Java  
   - **Project Type**: Romi  
   - **Name**: `LessonTwo`

---

### Step 2: Define the Drivetrain Subsystem
- Create a `Drivetrain.java` file.  
- Use `DifferentialDrive` from WPILib to connect to the ROMI motors.

💡 *Hint: This subsystem will be required by all drivetrain-related commands.*

---

### Step 3: Write the ArcadeDrive Command
- Create an `ArcadeDrive.java` file.  
- Use joystick input to drive the robot:

```java
@Override
public void execute() {
  m_drivetrain.arcadeDrive(m_xaxisSpeedSupplier.get(), m_zaxisRotateSupplier.get());
}
```

---

### Step 4: Bind Controls in `RobotContainer.java`
- Set `ArcadeDrive` as the **default command** for the drivetrain:

```java
drivetrain.setDefaultCommand(
  new ArcadeDrive(
    drivetrain, 
    () -> -m_controller.getRawAxis(1), 
    () -> -m_controller.getRawAxis(2)
  )
);
```

---

### Step 5: Add an Autonomous Command
- In `RobotContainer.java`, return a command to drive forward:

```java
public Command getAutonomousCommand() {
  return new ArcadeDrive(drivetrain, () -> -1, () -> 0);
}
```

---

### Step 6: Test Your Robot
1. **Deploy code** with WPILib → Deploy Robot Code.  
2. Run in **Teleop mode**:
   - Verify joystick controls.  
3. Run in **Autonomous mode**:
   - Confirm robot drives forward.  

---

### Step 7: Turn In Place
- In `RobotContainer.java`, return a command to turn the robot in place. 
Use the existing commands already in the project to do so.
    - Bind the TurnTime command to a button and implement it to turn for 2 seconds
    - Bind the TurnDegrees command to a button and implement it to turn too 90 degrees.

---

### Step 8: Test Your Robot
1. **Deploy code** with WPILib → Deploy Robot Code.  
2. Run in **Teleop mode**:
   - Verify joystick controls.  
3. Run in **Autonomous mode**:
   - Confirm robot turns in place.  

---

### Step 8: Drive in a Square
- In `RobotContainer.java`, create a command too drive the romi in a square , utilize the drive forward commands and the commands from step 7.
- Set this up as your autonomous command by modifying the getAutonomousCommand method.
- Demonstrate to a mentor your working code.

---

### Step 8: Test Your Robot
1. **Deploy code** with WPILib → Deploy Robot Code.  
2. Run in **Teleop mode**:
   - Verify joystick controls.  
3. Run in **Autonomous mode**:
   - Confirm robot drives in a square.  

---

## Resources
- [WPILib Command-Based Programming Guide](https://docs.wpilib.org/en/stable/docs/software/commandbased/index.html)  
- [Using the ROMI Robot](https://docs.wpilib.org/en/stable/docs/romi/index.html)  
