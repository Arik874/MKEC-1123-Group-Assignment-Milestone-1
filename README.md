# 🔆 STM32 Blinky — NUCLEO-F446RE

A beginner embedded systems project demonstrating GPIO output control by blinking the onboard LED (LD2) on the **STM32 NUCLEO-F446RE** development board using STM32CubeIDE and HAL library.

---

## 📹 Demo Video

▶️ **[Click here to watch the LED blinking demo](#)**
> *(Replace `#` with your actual video link — YouTube, Google Drive, etc.)*

---

## 🛠️ Hardware Required

| Component | Details |
|-----------|---------|
| Development Board | ST NUCLEO-F446RE |
| Microcontroller | STM32F446RETx (Cortex-M4, 180MHz) |
| LED Used | LD2 (Onboard Green LED) |
| LED Pin | PA5 (GPIO Port A, Pin 5) |
| Connection | USB Type-A to Mini-B cable (data cable) |

---

## 💻 Software Required

| Tool | Version |
|------|---------|
| STM32CubeIDE | Latest |
| STM32CubeMX | Included in CubeIDE |
| ST-LINK Driver | STSW-LINK009 |
| Firmware Package | stm32cube_fw_f4 |

---

## 📋 Step-by-Step Setup Guide

### Step 1 — Install STM32CubeIDE
- Download from [st.com](https://www.st.com/en/development-tools/stm32cubeide.html)
- Install with default settings

---

### Step 2 — Create a New Project in STM32CubeMX
1. Open STM32CubeIDE
2. Go to **File → New → STM32 Project**
3. In the board selector, search for **NUCLEO-F446RE**
4. Select it and click **Next**
5. Give your project a name (e.g. `Blinky`)
6. Click **Finish**

---

### Step 3 — Download Firmware Package
- CubeMX will prompt to download `stm32cube_fw_f4`
- Click **Yes** and wait for download to complete
- Click **OK** when done

---

### Step 4 — Configure PA5 as GPIO Output
1. In the **Pinout & Configuration** view, find pin **PA5**
2. Left-click on it → Select **GPIO_Output**
3. Right-click PA5 → **Enter User Label** → type `LD2`

> ✅ CubeMX automatically configures LD2 on NUCLEO-F446RE boards

---

### Step 5 — Clock Configuration
1. Click the **Clock Configuration** tab
2. Set **HCLK = 84 MHz**
3. Press Enter to confirm

---

### Step 6 — Generate Code
1. Click **GENERATE CODE** (top right)
2. Click **Open Project** when prompted

---

### Step 7 — Write the Blink Code

Open `Core/Src/main.c` and inside the `while(1)` loop, add:

```c
/* USER CODE BEGIN WHILE */
while (1)
{
    HAL_GPIO_TogglePin(LD2_GPIO_Port, LD2_Pin);
    HAL_Delay(500);  // 500ms delay — blink every 0.5 seconds
}
/* USER CODE END WHILE */
```

---

### Step 8 — Build the Project
```
Press Ctrl + B
```
✅ Confirm **"Build Finished. 0 errors"** in the console.

---

### Step 9 — Flash to the Board
```
Press Ctrl + F11
```
- Select **Run As → STM32 C/C++ Application**
- Wait for `"Download verified successfully"` in console

---

### Step 10 — Run!
- Press the **black RESET button (B2)** on the board
- Watch **LD2 (green LED) blink every 0.5 seconds** ✅

---

## 📁 Project Structure

```
Blinky/
├── Core/
│   ├── Inc/
│   │   └── main.h
│   └── Src/
│       └── main.c       ← Your blink code is here
├── Drivers/
│   └── STM32F4xx_HAL_Driver/
└── Blinky.ioc           ← CubeMX configuration file
```

---

## 💡 Key Code Explained

```c
// Toggles LD2 between ON and OFF each call
HAL_GPIO_TogglePin(LD2_GPIO_Port, LD2_Pin);

// Waits for 500 milliseconds before next toggle
HAL_Delay(500);
```

| `HAL_Delay()` Value | Blink Speed |
|---------------------|-------------|
| `100` | Very fast |
| `500` | Normal ✅ |
| `1000` | Slow (1 second) |
| `2000` | Very slow (2 seconds) |

---

## 🔍 LED Reference

| LED | Color | Meaning |
|-----|-------|---------|
| LD1 | Green/Red | ST-LINK status (not your code) |
| **LD2** | **Green** | **Your blink code ✅** |
| LD3 | Red | Power indicator |

---

## ⚠️ Common Issues & Fixes

| Problem | Fix |
|---------|-----|
| `No device found on target` | Check USB cable is a **data cable**, check CN2 jumpers |
| LED not blinking after flash | Press **RESET button** on board |
| Same blink speed after code change | Press **Ctrl+S** to save before building |
| LD1 blinking Red/Green | Use **Ctrl+F11** (Run), not F11 (Debug) |

---

## 📜 License
MIT License — Free to use and modify.
