# Quiz: WPILib New Commands Framework (Java, FRC)

## Multiple Choice

1. What is the primary purpose of a **command** in WPILib?  
   a) To define subsystems  
   b) To perform actions on subsystems in a modular way  
   c) To deploy code to the roboRIO  
   d) To monitor joystick input  

2. Which of the following is a **functional command**?  
   a) A class extending `CommandBase`  
   b) A lambda-based `RunCommand`  
   c) A `SequentialCommandGroup`  
   d) A `ParallelCommandGroup`  

3. What is the correct order of the command lifecycle?  
   a) `execute()`, `initialize()`, `end()`, `isFinished()`  
   b) `initialize()`, `execute()`, `isFinished()`, `end()`  
   c) `isFinished()`, `initialize()`, `execute()`, `end()`  
   d) `end()`, `execute()`, `initialize()`, `isFinished()`  

4. What does `addRequirements()` do in a command?  
   a) Initializes sensors  
   b) Prevents conflicts between commands using the same subsystem  
   c) Starts a timer  
   d) Binds a command to a joystick button  

---

## True/False

5. A **default command** runs automatically when no other command is using a subsystem.  
- True  
- False  

6. You cannot combine multiple commands in a sequence using the new framework.  
- True  
- False  

7. Lambda-based functional commands are ideal for short, simple actions.  
- True  
- False  

---

## Short Answer

8. Explain the advantages of using functional commands (lambdas) over full command classes.  

9. How do `SequentialCommandGroup` and `ParallelCommandGroup` differ in executing commands?  

10. Describe how you would bind a command to a joystick button using a lambda expression.  

---

## Bonus Question

11. You want your robot to drive forward while running the intake at the same time for 3 seconds. Describe how you could implement this using the new commands framework.
