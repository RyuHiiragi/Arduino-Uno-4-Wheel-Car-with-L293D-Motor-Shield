# Arduino Uno 4-Wheel Car with L293D Motor Shield

This project demonstrates how to control a 4-wheel car powered by 4 DC motors using an Arduino Uno and an L293D motor shield. The car is designed to be controlled via serial commands (for example, using a Bluetooth module) to move forward, backward, left, and right.

## Table of Contents

- [Overview](#overview)
- [Hardware Requirements](#hardware-requirements)
- [Software Requirements](#software-requirements)
- [Circuit Diagram](#circuit-diagram)
- [Code Explanation](#code-explanation)
- [Usage](#usage)
- [Arduino Code](#arduino-code)

## Overview

The Arduino code uses the `AFMotor` library to control 4 DC motors connected to an L293D motor shield. The serial interface listens for commands:
- **F**: Move Forward
- **B**: Move Backward
- **L**: Turn Left
- **R**: Turn Right

When a command is received, the car stops all motors first (to prevent conflicting movements) and then executes the corresponding movement command.

## Hardware Requirements

- **Arduino Uno**
- **L293D Motor Shield**
- **4 DC Motors** (one for each wheel)
- **Bluetooth Module** (optional, for wireless control via serial commands)
- **Wheels and Chassis**

## Software Requirements

- **Arduino IDE**
- **AFMotor Library** (can be installed via the Arduino Library Manager)

## Circuit Diagram

While the exact wiring may vary depending on your specific setup, here is a general overview:

- **Motors 1 & 2** are connected to outputs corresponding to `MOTOR12_1KHZ` on the motor shield.
- **Motors 3 & 4** are connected to outputs corresponding to `MOTOR34_1KHZ`.
- **Bluetooth Module** (if used) should be connected to the Arduino's serial pins.

Refer to the L293D motor shield documentation for the correct pin connections.

## Code Explanation

- **Initialization:**  
  The motors are initialized with the `AFMotor` library. Each motor is assigned to a port on the motor shield.

- **Setup:**  
  The `Serial.begin(9600);` sets up the serial communication with the desired baud rate (make sure it matches your Bluetooth module's baud rate if used).

- **Main Loop:**  
  The program continuously checks if a command is available via the serial interface. When a command is received, it stops all motors and then uses a `switch` statement to execute the corresponding function for moving forward, backward, left, or right.

- **Movement Functions:**  
  Each movement function sets the speed of the motors to maximum (255) and then runs them in the appropriate direction. For turning, the motors on each side run in opposite directions.

- **Stop Function:**  
  This function stops all the motors by setting their speed to 0 and releasing them.

## Usage

1. **Connect your hardware** according to the circuit diagram and ensure that all connections are secure.
2. **Install the AFMotor library** in your Arduino IDE.
3. **Upload the code** to your Arduino Uno.
4. **Open the Serial Monitor** (or connect via a Bluetooth terminal) and send commands:
   - **F**: Move forward
   - **B**: Move backward
   - **L**: Turn left
   - **R**: Turn right
