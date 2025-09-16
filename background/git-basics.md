# Git Basics

## Intro
Git is a version control system that lets teams track changes, collaborate safely, and manage robot code efficiently**.  
This guide introduces the basics and best practices for FRC teams.

## Goals
- Understand Git vs. GitHub
- Clone repositories and navigate branches
- Commit and push changes to GitHub
- Merge and pull updates

---

## 1️⃣ Installing Git

### macOS
```bash
brew install git
```

### Linux
```bash
sudo apt update
sudo apt install git
```

### Windows
- Download from [https://git-scm.com/download/win](https://git-scm.com/download/win)  
- During installation, choose “Use Git from Git Bash only” for simplicity.  

Verify installation:

```bash
git --version
```

---

## 2️⃣ Git Configuration

Set your name and email (used for commits):

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

Optional: check configuration:

```bash
git config --list
```

---

## 3️⃣ Basic Git Workflow

### Clone a Repository
```bash
git clone https://github.com/your-team/frc-robot.git
cd frc-robot
```

### Check Status
```bash
git status
```

### Add Changes
```bash
git add .
```

### Commit Changes
```bash
git commit -m "Add drivetrain subsystem"
```

### Push to Remote
```bash
git push origin main
```

---

## 4️⃣ Branching Workflow (Recommended for Teams)

1. **Create a feature branch**:
```bash
git checkout -b feature/drivetrain
```

2. **Work on your branch**, commit frequently.

3. **Push your branch**:
```bash
git push origin feature/drivetrain
```

4. **Create a Pull Request** on GitHub for review.

5. **Merge after approval**.

> Benefits: Isolates new features, reduces conflicts, and makes code review easier.

---

## 5️⃣ Pulling Updates from Team

Before starting work, always pull the latest changes:

```bash
git checkout main
git pull origin main
```

- Ensures your local copy is up-to-date.
- Avoids conflicts when multiple students work on the same codebase.

---

## 6️⃣ Resolving Conflicts

Sometimes Git cannot merge changes automatically. Example:

```text
<<<<<<< HEAD
int leftSpeed = 0;
=======
int leftSpeed = 1;
>>>>>>> feature/drivetrain
```

- Edit the file to choose the correct version.
- Then add, commit, and push:

```bash
git add .
git commit -m "Resolve merge conflict in DrivetrainSubsystem"
git push origin feature/drivetrain
```

---

## 7️⃣ Useful Git Commands for FRC Teams

| Command | Description |
|---------|-------------|
| `git log --oneline` | See commit history in compact format |
| `git diff` | See changes not yet staged |
| `git checkout <branch>` | Switch branches |
| `git merge <branch>` | Merge branch into current branch |
| `git stash` | Temporarily save changes without committing |
| `git fetch` | Fetch latest changes from remote without merging |

---

## 8️⃣ Best Practices for FRC Teams

- **Commit frequently** with meaningful messages.  
- **Use feature branches** for new code or experiments.  
- **Pull before you push** to avoid conflicts.  
- **Use Pull Requests** for code review.  
- **Keep main branch stable**: always deployable to robot.

---

## 9️⃣ Resources

- [Pro Git Book](https://git-scm.com/book/en/v2)
