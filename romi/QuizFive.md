# Quiz: Unit Testing in WPILib Java

Test your knowledge of unit testing with WPILib and JUnit!

---

## Multiple Choice

1. **What is the main purpose of unit testing in WPILib Java?**
   - A) To test hardware wiring  
   - B) To test robot logic without requiring real hardware  
   - C) To deploy code to the robot faster  
   - D) To replace driver practice  

---

2. **Where should you put your test files in a WPILib project?**
   - A) `src/main/java`  
   - B) `src/test/java`  
   - C) `deploy`  
   - D) `gradle`  

---

3. **Which WPILib feature allows simulating hardware like encoders or motors in unit tests?**
   - A) HAL  
   - B) SimDevice and *Sim classes (e.g., `EncoderSim`)  
   - C) NetworkTables  
   - D) DriverStation  

---

4. **Which JUnit annotation is used to mark a test method?**
   - A) `@Run`  
   - B) `@Execute`  
   - C) `@Test`  
   - D) `@Check`  

---

5. **What method in a Command is called when the command finishes or is interrupted?**
   - A) `initialize()`  
   - B) `execute()`  
   - C) `end(boolean interrupted)`  
   - D) `isFinished()`  

---

## True or False

6. **Unit tests in WPILib can only run on a real robot.**  

7. **Commands in WPILib can be tested by checking their lifecycle methods (`initialize`, `execute`, `end`).**  

8. **The Gradle command `./gradlew test` runs your unit tests.**  

9. **Unit tests should rely on real external services like cameras or field sensors.**  

10. **WPILib’s simulation classes allow testing hardware interactions without connecting physical devices.**  

---

## Short Answer

11. **Why is unit testing important for FRC teams, even if they test mostly on a real robot?**

12. **Write the JUnit assertion you would use to check that a variable `speed` equals `0.5` (within a tiny tolerance).**

13. **What are two best practices when writing unit tests for WPILib code?**

14. **How would you simulate an encoder reading of `42.0` in a test using WPILib?**

15. **What is the difference between `initialize()` and `end()` in a WPILib Command?**

---
