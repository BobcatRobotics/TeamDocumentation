# Continuous Integration for FRC Robot Code with GitHub Actions

This guide explains how to set up **Continuous Integration (CI)** for FRC robot code using **GitHub Actions**. CI ensures that code changes are automatically built and tested when pushed to your repository or submitted in a pull request.

---

## Benefits of CI

* Automatically compiles and tests robot code.
* Prevents broken code from being merged into `main`.
* Provides visible status checks for commits and pull requests.
* Ensures competition-ready stability.

---

## WPILIB Instructions
Students can find the full instructions to this available at 
👉 [Setting up CI for Robot Code using Github Actions](https://docs.wpilib.org/en/stable/docs/software/advanced-gradlerio/robot-code-ci.html)

---

## Setup Instructions

### 1. Create a Workflow File

In your GitHub repository:

* Go to **Actions → New workflow → set up a workflow yourself**.
* Create a file in `.github/workflows/ci.yml`.

### 2. Configure Workflow Triggers

The workflow should run:

* On **push** events to `main`.
* On **pull requests** targeting `main`.

### 3. Define the Build Job

* Use **Ubuntu 22.04** as the runner.
* Use the official **WPILib Docker image** with the RoboRIO toolchains.

### 4. Add Build Steps

1. **Checkout the repo** so the workflow has access to code.
2. **Mark repo as safe** for Git.
3. **Grant permissions** to the Gradle wrapper script.
4. **Run Gradle build** to compile and test.

---

## Example Workflow File

```yaml
name: CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]


# A workflow run is made up of one or more jobs that can run sequentially or in parallel
jobs:
  # This workflow contains a single job called "LessonOne"
  build-main:
    # The type of runner that the job will run on
    runs-on: ubuntu-latest
    defaults:
      run:
        working-directory: 2025-SummerActivity

    # This grabs the WPILib docker container
    container: wpilib/roborio-cross-ubuntu:2024-22.04

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:
    # Checks-out your repository under $GITHUB_WORKSPACE, so your job can access it
    - uses: actions/checkout@v4

    # Declares the repository safe and not under dubious ownership.
    - name: Add repository to git safe directories
      run: git config --global --add safe.directory $GITHUB_WORKSPACE

    # Grant execute permission for gradlew
    - name: Grant execute permission for gradlew
      run: chmod +x gradlew

    - name: Run Checkstyle
      run: ./gradlew checkstyleMain

    - name: Upload Checkstyle report
      if: always()
      uses: actions/upload-artifact@v4
      with:
        name: checkstyle-report
        path: build/reports/checkstyle/

    # Runs a single command using the runners shell
    - name: Compile robot code
      run: ./gradlew build

    # Runs a single command using the runners shell
    - name: Compile and run tests on robot code
      run: ./gradlew test

    # Runs a single command to generate docs of your code
    - name: Generate Docs
      run: ./gradlew javadoc

    - name: Upload Javadocs
      if: always()
      uses: actions/upload-artifact@v4
      with:
        name: javadocs-report
        path: build/docs/javadoc
```

---

## Adding a Build Badge

After the workflow runs successfully, you can add a badge to your `README.md`:

```markdown
![CI](https://github.com/<your-org>/<your-repo>/actions/workflows/ci.yml/badge.svg?branch=main)
```

Replace `<your-org>` and `<your-repo>` with your GitHub organization and repository names.

---

## Summary

* GitHub Actions automates builds and tests.
* Workflow runs on pushes and pull requests.
* Uses WPILib Docker container for FRC code.
* Helps ensure robot code is stable, reliable, and ready for competition.
