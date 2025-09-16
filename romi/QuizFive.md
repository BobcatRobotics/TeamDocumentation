# Quiz: Simulating CTRE Devices in WPILib (FRC Java)

## Multiple Choice

1. What is the primary purpose of simulating CTRE devices in WPILib?  
   a) Replace WPILib entirely  
   b) Test motor controllers and sensors without hardware  
   c) Control motors faster than real hardware  
   d) Connect the robot to the FRC Field Management System  

2. Which class do you use to simulate a Talon FX motor?  
   a) `TalonFXSimCollection`  
   b) `TalonFXController`  
   c) `TalonFXHardware`  
   d) `TalonFXLogger`  

3. How can you simulate a Pigeon IMU yaw angle?  
   a) `setYawAngle()`  
   b) `simulateYaw()`  
   c) `imuSim.setRawHeading()`  
   d) `imu.setYaw()`  

4. Why should you use small time steps (`deltaTime`) when updating simulated motors?  
   a) To save memory  
   b) To more accurately reflect real motor movement  
   c) To prevent exceptions in code  
   d) To avoid connecting to the robot  

---

## True/False

5. Simulated CTRE devices cannot be used with autonomous commands.  
- True  
- False  

6. Logging and telemetry (e.g., AdvantageKit, Shuffleboard) can be used with simulated CTRE devices.  
- True  
- False  

7. Simulated sensors always perfectly replicate real-world physical behavior, including friction and collisions.  
- True  
- False  

---

## Short Answer

8. Explain how `TalonFXSimCollection` can be used to simulate encoder values.  

9. What are the benefits of simulating CTRE devices before deploying code to the physical robot?  

10. Describe how you would integrate simulated TalonFX motors into a drivetrain subsystem for testing autonomous routines.  

---

## Scenario Question

11. You are testing a new autonomous routine using Talon FX motors and a Pigeon IMU. The routine involves driving forward 3 meters, turning 90 degrees, and then stopping. Describe the steps you would take to simulate both the motors and the IMU, record telemetry, and verify that the routine behaves as expected.
