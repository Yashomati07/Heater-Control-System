
# Heater Control System

A basic heater control system implemented using an Arduino Uno and DS18B20 temperature sensor. This project demonstrates real-time temperature monitoring, heater state control via a state machine, and safety features like overheat protection.

## Hardware Used

- **Arduino Uno**
- **DS18B20 Digital Temperature Sensor**
- **LED (optional)** – Overheat visual indicator
- **Resistor (4.7kΩ)** – Pull-up resistor for DS18B20 data line

## Wiring Diagram

| Component      | Arduino Pin |
|----------------|-------------|
| DS18B20 Data   | D4          |
| DS18B20 VCC    | 5V          |
| DS18B20 GND    | GND         |
| Heater (Simulated with LED) | D5 |
| Overheat LED   | D6          |

> Don't forget the 4.7kΩ pull-up resistor between DS18B20 data and VCC.

## Libraries Required

Install the following Arduino libraries via the Library Manager:
- `OneWire`
- `DallasTemperature`

## System Behavior

- **IDLE**: Heater off, waiting for temperature to drop.
- **HEATING**: Heater on until target temperature is reached.
- **STABILIZING**: Heater off, temperature stabilizing.
- **TARGET_REACHED**: Target temperature reached and stable.
- **OVERHEAT**: Safety condition – heater forcibly turned off.

## Temperature Thresholds

| State              | Trigger Condition       |
|--------------------|-------------------------|
| Start Heating      | Temp < 35°C             |
| Stop Heating       | Temp ≥ 65°C             |
| Overheat           | Temp ≥ 75°C             |

## Features

- Real-time temperature monitoring
- Heater control via GPIO
- LED indication for overheat state
- Serial logging for debugging
- Structured state machine logic

## How to Use

1. **Connect all components** as per the wiring diagram.
2. **Upload the sketch** (`.ino` file) to Arduino Uno via Arduino IDE.
3. **Open Serial Monitor** at 9600 baud to observe temperature readings and state transitions.

## Future Improvements

- Add support for **multiple heating profiles** (e.g., simmer, boil, keep warm).
- Implement **PID control** for precise temperature regulation.
- Upgrade to **ESP32** for **BLE app control** and **cloud sync**.
- Add **second sensor** or **thermal fuse** for enhanced safety.


## License

This project is for educational purposes and is licensed under the MIT License.
