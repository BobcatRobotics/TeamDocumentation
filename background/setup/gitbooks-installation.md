# Gitbook installation 

Welcome! This quick start guide will get you set up this gitbook locally 

---

## Installation & Setup Checklist
- [Setup Checklist](backgroud/setup-checklist-handout.md)

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
