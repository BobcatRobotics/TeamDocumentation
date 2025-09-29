# Quiz: Command-Based Programming with WPILib on the ROMI Robot

## Multiple Choice

1. What is the primary purpose of **Command-Based Programming** in WPILib?  
   a) To control the Driver Station  
   b) To organize robot behavior into organized, modular, and reusable units  
   c) To make the robot move faster  
   d) To configure CAN devices automatically  

2. Which of the following is considered a **subsystem**?  
   a) DriveForward command  
   b) Drivetrain  
   c) Joystick button  
   d) Timer  

3. What is the role of a **command** in WPILib?  
   a) To configure the radio connection  
   b) To schedule and control the behavior of subsystems  
   c) To deploy the robot code to the ROMI  
   d) To monitor battery voltage  

4. Which method in a Command is used to determine when it should finish?  
   a) initialize()  
   b) execute()  
   c) isFinished()  
   d) end()  

---

## True/False

5. The **Scheduler** ensures that multiple commands do not conflict over the same subsystem.  
   - True  
   - False  

6. The **Default Command** is automatically run by a subsystem when no other commands are using it.  
   - True  
   - False  

7. Command-Based Programming is only useful for full-size FRC robots, not ROMI robots.  
   - True  
   - False  

---

## Short Answer

8. What is the purpose of the `addRequirements()` method in a Command?  

9. In the example `DriveForward` command, what is the role of the `Timer`?  

10. Name two benefits of using the Command-Based programming structure.  

11. Describe how a command can be bound to a joystick button in `RobotContainer.java`.  

12. What is the main difference between deploying code to a **real FRC robot** versus the **Romi**?

13. Why do you think WPILib uses a **simulation framework** for the Romi instead of direct code deployment?

14. If your Romi doesn’t connect, what are two possible troubleshooting steps you could try?

15. How might you extend the Romi project to do more than just drive (for example, follow a line or use sensors)?

## Bonus Question

16. Explain how you would create a **SequentialCommandGroup** to make the ROMI robot drive forward, turn, and then drive forward again.  
