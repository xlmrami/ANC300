# ANC300 MATLAB Controller

This repository provides a MATLAB class and GUI interface for controlling the **ANC300 Piezo Controller** via RS232 (or USB-serial) communication. It enables you to set frequencies and voltages, move individual axes, and configure operation modes directly from MATLAB.

## 📦 Features

- Set/get stepping **frequency** and **voltage** per axis
- Move piezo **up/down** in discrete steps
- Configure **axis modes**: `gnd`, `cap`, `stp`
- **Stop motion** command for any axis
- Compatible **MATLAB GUI** for manual control

## 🔧 Requirements

- ANC300 connected via RS232 or USB
- Correct **COM port** (check Device Manager under "Ports (COM & LPT)")
- MATLAB R2019b or later

## 📁 Class: `ANC300.m`

### Initialization
```matlab
controller = ANC300('COM3'); % Replace COM3 with actual port
```

### Main Methods

| Method            | Description                            |
|------------------|----------------------------------------|
| `set_frequency(Hz, axis)` | Set stepping frequency in Hz    |
| `get_frequency(axis)`     | Get current frequency            |
| `set_voltage(V, axis)`    | Set voltage for given axis       |
| `get_voltage(axis)`       | Get current voltage              |
| `stepup(steps, axis)`     | Step piezo up                    |
| `stepdown(steps, axis)`   | Step piezo down                  |
| `stop(axis)`              | Stop movement                    |
| `set_mode(mode, axis)`    | Set mode: `gnd`, `cap`, `stp`    |

## 💡 Example Usage

```matlab
controller = ANC300('COM3');          % Connect to device
controller.set_frequency(500, 1);     % Set 500 Hz on axis 1
controller.stepup(100, 1);            % Move axis 1 up 100 steps
[~, voltage, ~] = controller.get_voltage(1);
disp(['Voltage on axis 1: ', voltage]);
```

## 🖥️ GUI: `ANC300_GUI.mlapp`

### To Launch:

```matlab
clear; clc;
app = ANC300_GUI('COM3');  % Launch with correct COM port
```

- Use dropdown to select mode (`gnd`, `cap`, `stp`)
- Set voltage and frequency, then press **Update**
- Use **Step Up** / **Step Down** buttons to move the piezo

> Note: Place both `ANC300.m` and `ANC300_GUI.mlapp` in the same directory for proper functionality.

## 📬 Contact

Developed by **Rami Lameche**  
📧 xlmrami@gmail.com
