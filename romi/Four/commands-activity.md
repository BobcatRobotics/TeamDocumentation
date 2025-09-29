# Activity: ROMI Robot Commands Practice

## Objective
Students will apply the **New Commands Framework** on a ROMI robot to create, schedule, and execute commands using both traditional `CommandBase` classes and lambda-based functional commands.

---

## Materials
- FRC ROMI Robot Kit  
- Computer with VS Code / WPILib installed  
- USB or Wi-Fi connection to ROMI  
- Joysticks or game controllers (optional)  

---

## Learning Goals
- Implement commands to control the ROMI robot’s drivetrain.  
- Practice binding commands to joystick buttons using lambdas.  
- Use command groups for sequential and parallel actions.  
- Apply timers and default commands for continuous control.

---

## Activity Steps

### Part 1: Drivetrain Commands
1. Create a **Drivetrain** subsystem for the ROMI robot.  
   - Include methods for `arcadeDrive(forward, rotation)` and stopping the motors.  
2. Create a **DriveForward** command using `CommandBase`.  
   - Make the robot move forward for 2 seconds.  
3. Test the command by scheduling it in `RobotContainer` or using a button.

---

### Part 2: Functional Commands
1. Implement a **lambda-based command** that drives the ROMI forward at half speed.  
   - Use `RunCommand` and `withTimeout(2.0)` to limit duration.  
2. Schedule this functional command and observe the behavior.  

---

### Part 3: Sequential and Parallel Commands
1. **Sequential Command Group**:  
   - Drive forward → Turn right 90 degrees → Drive forward again.  
2. **Parallel Command Group** (optional if robot has additional mechanisms like LEDs or a buzzer):  
   - Drive forward while activating a secondary subsystem simultaneously.  

---

### Part 4: Joystick Control and Default Commands
1. Bind a joystick button to the **DriveForward** command.  
2. Create a **default command** for the drivetrain to control it using the joystick continuously.  
3. Test that pressing buttons interrupts the default command correctly.

---

## Discussion Questions
1. What are the benefits of using the **New Commands Framework** with ROMI robots?  
2. How do functional commands simplify simple actions compared to traditional `CommandBase` classes?  
3. How can command groups help in autonomous routines?

---

## Extension Ideas
- Add sensors like bump switches and create commands that respond to sensor input.  
- Use timers or encoders to create precise movement sequences.  
- Combine multiple subsystems (like a buzzer or LEDs) to create more complex behaviors.

---
