# STM32 Blinky — NUCLEO-F446RE

A beginner embedded systems project demonstrating GPIO output control by blinking the onboard LED (LD2) on the STM32 NUCLEO-F446RE development board using STM32CubeIDE and the HAL library.

## Demo Video

Click the link below to watch the LED blinking demonstration:

*Replace with your actual video link (YouTube, Google Drive, etc.)*

---

# Hardware Required

| Component         | Details                            |
| ----------------- | ---------------------------------- |
| Development Board | ST NUCLEO-F446RE                   |
| Microcontroller   | STM32F446RETx (Cortex-M4, 180 MHz) |
| LED Used          | LD2 (Onboard Green LED)            |
| LED Pin           | PA5 (GPIO Port A, Pin 5)           |
| Connection        | USB Type-A to Mini-B data cable    |

---

# Software Required

| Tool             | Version               |
| ---------------- | --------------------- |
| STM32CubeIDE     | Latest                |
| STM32CubeMX      | Included with CubeIDE |
| ST-LINK Driver   | STSW-LINK009          |
| Firmware Package | stm32cube_fw_f4       |

---

# Milestone 1: STM32 Familiarization (Blinking LED)

For the first milestone of the group project, the objective was to blink the onboard LED of the NUCLEO-F446RE development board. This activity helped familiarize the team with GPIO output configuration and embedded software development using STM32CubeIDE and STM32CubeMX.

---

# Video Demonstration

Click the link below to watch the LED blinking demonstration.

---

# Hardware Used

| Component         | Details                         |
| ----------------- | ------------------------------- |
| Development Board | ST NUCLEO-F446RE                |
| LED Used          | LD2 (Onboard Green LED)         |
| LED Pin           | PA5 (GPIO Port A, Pin 5)        |
| Connection        | USB Type-A to Mini-B data cable |

---

# Software Used

| Tool         |
| ------------ |
| STM32CubeIDE |
| STM32CubeMX  |

---

# Step-by-Step Setup Guide

## Step 1 — Install STM32CubeIDE and STM32CubeMX

The software packages were downloaded from the official STMicroelectronics website and installed using the default settings.

---

## Step 2 — Create a New Project in STM32CubeIDE

1. Open STM32CubeIDE.
2. Navigate to **File → New → STM32 Project**.
3. In the board selector, search for **NUCLEO-F446RE**.
4. Select the board and click **Next**.
5. Enter a project name (e.g., *Blinky*).
6. Click **Finish**.

When prompted, select **Yes** to initialize all peripherals with their default configuration.

By default, the board configuration includes multiple GPIO pins, including the LD2 green LED connected to pin PA5.

---

## Step 3 — Download the Firmware Package

STM32CubeMX automatically prompts the user to download the required firmware package:

* `stm32cube_fw_f4`

Click **Yes** and wait for the installation to complete.

---

## Step 4 — Configure PA5 as GPIO Output

1. Open the **Pinout & Configuration** tab.
2. Locate pin **PA5**.
3. Set the pin mode to **GPIO_Output**.
4. Assign the user label **LD2**.

The NUCLEO-F446RE board typically configures LD2 automatically.

---

## Step 5 — Configure the Clock

1. Open the **Clock Configuration** tab.
2. Set the **HCLK** frequency to **84 MHz**.
3. Press **Enter** to apply the configuration.

---

## Step 6 — Generate the Code

1. Click **GENERATE CODE**.
2. Open the generated project in STM32CubeIDE when prompted.

---

## Step 7 — Write the Blink Code

Open the file:

```c
Core/Src/main.c
```

Inside the `while (1)` loop, add the following code:

```c
/* USER CODE BEGIN WHILE */
while (1)
{
    HAL_GPIO_TogglePin(LD2_GPIO_Port, LD2_Pin);
    HAL_Delay(500);
}
/* USER CODE END WHILE */
```

This code toggles the onboard LED state every 500 milliseconds, creating a blinking effect.

---

## Step 8 — Build the Project

1. Press **Ctrl + B** to build the project.
2. Verify that the console displays:

```text
Build Finished. 0 errors
```

---

## Step 9 — Flash the Program to the Board

1. Press **Ctrl + F11**.
2. Select:

```text
Run As → STM32 C/C++ Application
```

3. Wait until the console displays:

```text
Download verified successfully
```

---

## Step 10 — Run the Project

1. Press the black **RESET (B2)** button on the board.
2. Observe the LD2 green LED blinking every 0.5 seconds.

---

# Project Structure

```text
Blinky/
├── Core/
│   ├── Inc/
│   │   └── main.h
│   └── Src/
│       └── main.c
├── Drivers/
│   └── STM32F4xx_HAL_Driver/
└── Blinky.ioc
```

---

# Key Code Explanation

```c
HAL_GPIO_TogglePin(LD2_GPIO_Port, LD2_Pin);
```

Toggles the LD2 LED between ON and OFF states.

```c
HAL_Delay(500);
```

Creates a delay of 500 milliseconds before the next toggle operation.

---

# Delay Timing Reference

| HAL_Delay() Value | Blink Speed           |
| ----------------- | --------------------- |
| 100               | Very Fast             |
| 500               | Normal                |
| 1000              | Slow (1 second)       |
| 2000              | Very Slow (2 seconds) |

---

# LED Reference

| LED | Color     | Function                 |
| --- | --------- | ------------------------ |
| LD1 | Green/Red | ST-LINK status indicator |
| LD2 | Green     | User-programmable LED    |
| LD3 | Red       | Power indicator          |

---

# Common Issues and Solutions

| Problem                             | Solution                                                                      |
| ----------------------------------- | ----------------------------------------------------------------------------- |
| No device detected                  | Ensure the USB cable supports data transfer and verify CN2 jumper connections |
| LED does not blink after flashing   | Press the RESET button on the board                                           |
| Blink speed does not change         | Save the code before rebuilding the project                                   |
| LD1 blinking red/green continuously | Use **Ctrl + F11 (Run)** instead of **F11 (Debug)**                           |

---

# Key Takeaways from the Project

During the development process, there was initial confusion regarding the onboard LEDs. The team mistakenly observed the ST-LINK status LED (LD1), which blinks red and green during flashing and debugging operations. This led to the assumption that there was an issue with the code or board because changing the delay value did not appear to affect the blinking behavior.

After further observation, it was discovered that the actual user-programmable LED was LD2, connected to pin PA5. Once the correct LED was identified, the blinking behavior matched the programmed delay values correctly. This experience highlighted the importance of understanding the board layout and the function of each onboard LED during embedded system debugging.

---

# License

MIT License — Free to use and modify.
