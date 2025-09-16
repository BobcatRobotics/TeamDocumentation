# Quiz: FRC Subsystems (Java, WPILib)

## Multiple Choice

1. What is the primary purpose of a **subsystem** in Command-Based programming?  
   a) To define joystick buttons  
   b) To encapsulate hardware and provide methods for commands  
   c) To deploy robot code to the roboRIO  
   d) To monitor battery voltage  

2. Which of the following is an example of a subsystem?  
   a) DriveForward command  
   b) Drivetrain  
   c) Joystick button  
   d) Timer  

3. What is the purpose of a **default command**?  
   a) To run a command when the robot is disabled  
   b) To continuously control a subsystem when no other command is using it  
   c) To initialize sensors at startup  
   d) To deploy code automatically  

4. What does `addRequirements()` do in a command?  
   a) Starts a timer  
   b) Prevents multiple commands from using the same subsystem simultaneously  
   c) Sets joystick mappings  
   d) Configures motor controllers  

---

## True/False

5. Commands should directly manipulate hardware without using subsystem methods.  
- True  
- False  

6. Subsystems help make robot code modular and reusable.  
- True  
- False  

7. Only one subsystem is allowed per robot in Command-Based programming.  
- True  
- False  

---

## Short Answer

8. Explain why subsystems are important in Command-Based programming.  

9. Name two benefits of using a default command for a subsystem.  

10. Describe how a command interacts with a subsystem to perform an action.  

---

## Bonus Question

11. You want your robot to drive forward for 2 seconds when a button is pressed. Outline the steps to create the command and bind it to a button using the subsystem.
