# SmartHome Automation

This repository contains the source code for a Smart Home automation project built on the STM32F446RETX microcontroller. The project is generated and configured using STM32CubeMX and is designed to be built with STM32CubeIDE.

## 🌟 System Features

The system operates in two main modes: **Auto Mode** and **Manual Mode**. It continuously monitors safety sensors regardless of the active mode.

### 1. Safety System (Always Active)
* **Gas Sensor Detection:** A gas sensor is constantly monitored. If a leak is detected, an alarm buzzer is immediately triggered.

### 2. Auto Mode (Default)
In Auto Mode, the system intelligently controls the environment based on sensor readings:
* **Temperature Control:** Uses an analog temperature sensor. If the room gets too hot (ADC reading > 2200), the cooling fan automatically turns on at full speed.
* **Smart Lighting:** Uses an LDR (Light Dependent Resistor) to measure ambient light. The room LED brightness dynamically and smoothly adjusts based on the darkness of the room using PWM. 
  * Pitch dark = Fully ON
  * Bright light = Fully OFF

### 3. Manual Mode (Bluetooth Controlled)
Users can take manual control of the smart home using a smartphone Bluetooth application.
* Send `M` to toggle between Auto and Manual modes.
* While in Manual Mode, use the following commands:
  * `F` : Turn Fan ON
  * `f` : Turn Fan OFF
  * `L` : Turn Light ON
  * `l` : Turn Light OFF

## 🔌 Hardware Pinout

* **PA0 (ADC1_IN0):** Temperature Sensor Input
* **PA1 (ADC1_IN1):** LDR (Light Sensor) Input
* **PA4 (GPIO Input):** Gas Sensor Input (Active Low)
* **PA6 (TIM3_CH1 PWM):** Fan Control output
* **PA7 (TIM3_CH2 PWM):** LED Lighting Control output
* **Buzzer:** GPIO Output (Configured via CubeMX)
* **USART1:** Bluetooth Module (HC-05/HC-06)

## 🛠️ Software Requirements
* STM32CubeIDE
* STM32CubeMX (optional, for device configuration changes)

## 🚀 How to Build & Run
1. Clone this repository.
2. Open STM32CubeIDE and go to `File` -> `Import` -> `Existing Projects into Workspace`.
3. Select the `SmartHome` folder.
4. Build the project using `Project` -> `Build Project` (or click the hammer icon).
5. Connect your STM32 Nucleo board and flash the microcontroller using `Run` -> `Debug` or `Run` -> `Run`.
