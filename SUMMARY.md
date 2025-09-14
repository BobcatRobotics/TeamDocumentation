# FRC Fall Training - Quick Start

Welcome! This quick start guide will get you set up for FRC Programming Training.

---

## Project Setup Checklist
- [Setup Checklist](background/setup-checklist.md)  

---


## 1️⃣ Install Node.js via Command Line

### macOS / Linux (Homebrew or package manager) / Windows

```bash
# macOS
brew install node

# Ubuntu/Debian
sudo apt update
sudo apt install nodejs npm

# Download Node.js LTS installer
Invoke-WebRequest -Uri "https://nodejs.org/dist/v20.5.1/node-v20.5.1-x64.msi" -OutFile "node-lts.msi"
Start-Process msiexec.exe -Wait -ArgumentList '/i node-lts.msi /quiet'
```

# Install gitbook
```bash
npm install -g gitbook-cli
```

# 4️⃣ Download the repository
```bash
git clone https://github.com/BobcatRobotics/TeamDocumentation.git
cd TeamDocumentation
```

# Run the gitbook
```bash
gitbook install
gitbook serve
```


# FRC Fall Training - Quick Start

Welcome! This quick start guide will get you set up for FRC Programming Training.

---


# Summary

## Background
- [Application Requirements](background/application-requirements.md)
  - 🖥️ [WPILib Requirements & Installation](background/application-requirements.md)
  - 🎮 [Driver Station & Game Tools](background/driver-station.md)
  - ✅ [Setup Checklist](background/setup-checklist.md)
- 💻 [Java Basics](background/java-basics.md)
- 🔧 [Git Basics](background/git-basics.md)
- 🌐 [Team Git Workflow](background/team-git-workflow.md)
- 📏 [Code Standards & Code Quality](background/code-standards.md)

## Architecture
- 🏗️ [WPILib Overview](architecture/wpilib-overview.md)
- ⚡ [Electrical Basics](architecture/electrical-basics.md)

## ROMI Lessons
- 🤖 [Command-Based Programming](romi/command-based-programming.md)
- 🛠️ [Subsystems](romi/subsystems.md)
- 🎯 [Commands](romi/commands.md)
- 📊 [AdvantageKit & Logging](romi/advantagekit-logging.md)
- 🖥️ [Simulation](romi/simulation.md)

## Advanced Topics
- 🌀 [Swerve Drive](advanced/swerve-drive.md)
- 👁️ [Vision Processing](advanced/vision.md)
- 🤖 [Autonomous Programming](advanced/autonomous.md)

## Additional Resources
- 📚 [Documentation](resources/documentation.md)
- 🔗 [Additional Team Links](resources/team-links.md)
- 🌐 [External Resources](resources/external-resources.md)
