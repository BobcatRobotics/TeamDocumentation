# Quiz: AdvantageKit and Logging in FRC (Java)

## Multiple Choice

1. What is the primary purpose of AdvantageKit?  
   a) Control motors and sensors  
   b) Provide logging, telemetry, and deterministic replay  
   c) Replace WPILib entirely  
   d) Connect the robot to the FRC Field Management System  

2. Which class should your `Robot` class extend to use AdvantageKit?  
   a) `TimedRobot`  
   b) `LoggedRobot`  
   c) `CommandRobot`  
   d) `SubsystemBase`  

3. Which AdvantageKit component allows you to **visualize telemetry and replay logs**?  
   a) WPILib Shuffleboard  
   b) AdvantageScope  
   c) RoboRIO Dashboard  
   d) NetworkTables Viewer  

4. Where are logs typically stored on the robot?  
   a) `/home/lvuser/logs`  
   b) `/U/logs`  
   c) `C:/RobotLogs`  
   d) `/tmp/logs`  

---

## True/False

5. Functional commands (lambdas) cannot be logged with AdvantageKit.  
- True  
- False  

6. Excessive logging can impact robot performance.  
- True  
- False  

7. Logging subsystem outputs and command states can help with debugging and post-match analysis.  
- True  
- False  

---

## Short Answer

8. Explain the difference between `recordInput()` and `recordOutput()` in AdvantageKit.  

9. Why is it recommended to use consistent key names when logging subsystem data?  

10. Describe how AdvantageKit can be used to replay robot actions for testing or analysis.  

---

## Scenario Question

11. You are building a new robot and want to track drivetrain motor speeds, joystick inputs, and command execution. Describe the steps you would take to integrate AdvantageKit into your project, including initialization, logging, and visualization.
