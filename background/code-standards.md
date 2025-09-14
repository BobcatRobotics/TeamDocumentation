# Code Standards & Code Quality

## Intro
Good coding practices improve reliability, readability, and collaboration.  
Following consistent standards helps teams work together efficiently and reduces bugs in robot code.

---

## 1️⃣ Naming Conventions
**Intro:** Proper naming makes your code readable and self-documenting.

**Guidelines:**
- **Classes:** PascalCase (`DrivetrainSubsystem`)  
- **Methods/Functions:** camelCase (`setMotorSpeed`)  
- **Variables:** camelCase (`leftMotor`)  

**Goals:**
- Recognize and apply standard Java naming conventions
- Ensure team code is readable and consistent

---

## 2️⃣ Project Structure
**Intro:** Organize files logically so team members can quickly find code.

**Guidelines:**
- `src/main/java/frc/robot/` for robot code  
- `subsystems/` for each subsystem class  
- `commands/` for command classes  
- `constants/` for configuration values  
- `utilities/` for helper classes  

**Goals:**
- Maintain a clear project hierarchy
- Keep related code grouped together

---

## 3️⃣ Comments & Documentation
**Intro:** Proper comments explain why code exists, not what it does.

**Guidelines:**
- Use `//` for short explanations  
- Use `/** */` for JavaDoc-style comments on classes and methods  
- Avoid redundant comments that simply restate the code  

**Goals:**
- Write clear, concise comments
- Document important methods and subsystems for the team

---

## 4️⃣ Formatting & Style
**Intro:** Consistent formatting improves readability and reduces merge conflicts.

**Guidelines:**
- Indentation: 4 spaces per level  
- Braces on the same line for methods and loops  
- Keep lines ≤ 120 characters  
- Use Spotless plugin or Checkstyle for automatic formatting  

**Goals:**
- Keep code consistently formatted
- Reduce style-related merge conflicts
- Learn to use automated formatting tools

---

## 5️⃣ Testing & Debugging
**Intro:** Test code frequently to catch errors early.

**Guidelines:**
- Use the built-in WPILib **simulator** for initial testing  
- Write **unit tests** for utility functions  
- Use logging (`DriverStation.reportWarning`, AdvantageKit, etc.) for runtime debugging  

**Goals:**
- Write testable and debuggable code
- Catch issues early in development
- Use logging to monitor robot behavior

---

## 6️⃣ Code Reviews & Collaboration
**Intro:** Peer reviews help catch mistakes and improve team knowledge.

**Guidelines:**
- Use **GitHub Pull Requests** for code changes  
- Review for naming, formatting, logic, and readability  
- Provide constructive feedback  

**Goals:**
- Improve code qual
