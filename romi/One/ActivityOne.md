# Student Activity: Programming the Romi

In this activity, you will learn how to create and run your first program for the **Romi robot** using WPILib. You will use Visual Studio Code, the WPILib extension, and the Romi simulation environment.

---

## Learning Goals
- Understand how Romi programs are created in VS Code.
- Learn how to run Romi programs using the WPILib simulation framework.
- Practice editing configuration files when changing network/IP settings.
- Gain confidence in navigating the WPILib development workflow.

---

## Prerequisites
- A laptop with VS Code and the WPILib extension installed.
- Access to a Romi robot with fresh batteries.
- A joystick/gamepad connected to your computer.

---

## Part 1: Create a New Romi Project

1. Open **Visual Studio Code**.
2. Open the **Command Palette** (`Ctrl+Shift+P`).
3. Search for **"New Project"** and select **Create a New Project**.
4. Choose:
   - **Project Type** → `Example`
   - **Language** → Java or C++ (ask your instructor which to use)
   - **Example** → `RomiReference`
5. Fill out the project name and location, then click **Generate Project**.

✅ **Checkpoint:** Make sure your new project has a `Drivetrain` class with a default command.

---

## Part 2: Run Your Romi Program

1. Power on your **Romi robot**.
2. Connect your laptop to the WiFi network broadcast by the Romi (`WPILibPi-<number>`).
3. If your Romi uses a **custom WiFi network**, update the IP address in `build.gradle`:
   ```gradle
   wpi.sim.envVar("HALSIMWS_HOST", "10.0.0.2")
   wpi.sim.addWebsocketsServer().defaultEnabled = true
   wpi.sim.addWebsocketsClient().defaultEnabled = true
   ```
4. In VS Code, open the **Command Palette** again and run **Simulate Robot Code** (or press `F5`).
5. Check the console output for:
   ```
   HALSimWS: WebSocket Connected
   ```

✅ **Checkpoint:** If you see the message above, your Romi is running and ready to drive with the joystick.

---

## Extension Challenge (Optional)

Modify your Romi project to:
- Print a message to the console whenever the robot is enabled.
- Change the default driving speed of the Romi.
- Add a simple autonomous command (e.g., drive forward for 2 seconds).

---

## Submission

- Show your instructor that your Romi can be controlled with the joystick.
- Answer the **Quiz** [here](QuizOne.md)
- (Optional) Demonstrate your Extension Challenge if completed.

---
