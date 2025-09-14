# Application Requirements

## Intro
Before writing any robot code, students need the right tools installed and configured.

## WPILib Requirements
Before installing WPILib, make sure your computer meets the following requirements:

- **Operating System**:  
  - Windows 10/11 (64-bit)  
  - macOS 11 or newer  
  - Linux (Ubuntu 22.04 recommended, other distros may work)  

- **Java Development Kit (JDK)**:  
  - WPILib includes its own OpenJDK, but having JDK 17+ installed system-wide is recommended.  

- **Disk Space**:  
  - At least 1.5 GB free for the WPILib tools and dependencies.  

- **VS Code**:  
  - WPILib installer comes with a customized version of VS Code that includes all required extensions.  

- **Internet Connection**:  
  - Required for the initial installation (GradleRIO will also fetch dependencies the first time you build a project).  

⚠️ Note: If you already have a global installation of VS Code or Java, WPILib will not interfere—it installs its own versions in a separate directory.

## Student Checklist
Each student must download the student checklist from 
👉 [Student Checklist](setup-checklist-handout.md)


## WPILib Installation
The easiest way to install WPILib is by following the official setup guide:  
👉 [WPILib Installation Guide](https://docs.wpilib.org/en/latest/docs/zero-to-robot/step-2/wpilib-setup.html)

### Steps (summary from official docs):
1. Download the WPILib installer for your operating system from [GitHub Releases](https://github.com/wpilibsuite/allwpilib/releases).
2. Run the installer and follow the prompts.  
   - On Windows: run the `.exe` file  
   - On macOS/Linux: extract and run the install script  
3. Install **VS Code + WPILib extension** (included in the installer).  
4. Verify installation by opening VS Code and creating a new WPILib project.  

⚠️ For Driver Station software, see the [Driver Station & Game Tools](driver-station.md) page.

## Goals
- Install WPILib and VS Code
- Configure Java (JDK + GradleRIO)
- Understand the Driver Station software