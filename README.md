**Milestone 1: STM32 Familiarization (Blinky)**

| Name | Matrics No. |
|------|-------------|
| Muhammad Hafiy Rifqi | MKE251019 |
| Baldwen Raj | MKE251025 |
| Aron Rodrick Lakra | MKE251046 |

## Repository Contents

| File | Description |
|------|-------------|
| `main.c` | Main firmware code — contains the LED blink logic |
| `main.h` | Pin definitions (LD2_Pin, LD2_GPIO_Port) |
| `Blinky.ioc` | STM32CubeMX configuration file |
| `MKEC 1123 Group 2 Milestone 1 Steps` | Full milestone 1 report with setup steps and screenshots |

## Video Demonstration

**[Click here to watch the LED blinking on the NUCLEO-F446RE](https://youtu.be/5i81tzjD-fc)**

## Report

The full setup report with screenshots is available in this repository:
**[MKEC 1123 Group 2 Milestone 1 Steps]**

## Quick Setup Summary

**Hardware:** NUCLEO-F446RE | **LED:** LD2 (PA5) | **IDE:** STM32CubeIDE

**Step 1** — Open STM32CubeIDE → File → New → STM32 Project → search `NUCLEO-F446RE` → Finish

**Step 2** — Click **GENERATE CODE** in CubeMX → Open Project

**Step 3** — In `Core/Src/main.c`, add inside `while(1)`:
```c
HAL_GPIO_TogglePin(LD2_GPIO_Port, LD2_Pin);
HAL_Delay(500); // blink every 0.5s
```

**Step 4** — `Ctrl+S` → `Ctrl+B` (build) → `Ctrl+F11` (flash) → Press **RESET** button on board

LD2 green LED blinks every 0.5 seconds
