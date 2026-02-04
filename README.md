# Activity 3: Environmental Sensors

**Course:** CS 304 - Robotic Agents  
**Due Date:** Thursday, February 6th at 11:00 AM

---

## Overview

In this activity, you will wire and experiment with **three types of environmental sensors**: a temperature sensor (TMP36), a soil moisture sensor, and a photoresistor light sensor. You'll document your experiments with each sensor and explore how they respond to different environmental conditions.


## Requirements

1. **Wire all three sensors** correctly to Arduino Uno
2. **Show all sensors working** with Serial Monitor output
3. **Conduct at least 2 experiments per sensor** (see experiments.md for suggestions)
4. **Document your findings** in experiments.md
5. **Demonstrate working sensors** to the instructor

### Important Note on Sensor Behavior

**Some sensors may give unexpected or inaccurate readings** due to loose connections, calibration issues, or sensor defects. This is normal in real-world robotics! If your sensor values seem off:

- **Document what you observe** - explain the issue in experiments.md
- **Try troubleshooting** - check wiring, try different pins, re-seat connections
- **Conduct experiments anyway** - even if absolute values are wrong, you can still test relative changes (hot vs. cold, wet vs. dry, bright vs. dark)
- **Explain your findings** - part of this activity is learning to work with imperfect hardware

You will **not be penalized** for sensor hardware issues as long as you document your troubleshooting efforts and explain what you observed.

---

## Sensor 1: Temperature Sensor (TMP36)

### Wiring

| TMP36 Pin | Arduino Pin |
|-----------|-------------|
| Left (Vs) | 5V          |
| Middle (Vout - yellow cable) | Any analog pin (e.g., A0) |
| Right (GND) | GND       |

**Note:** You can use any analog pin (A0-A5) for Vout. Update the code accordingly.

### Sample Code

```cpp
void setup() {
  Serial.begin(9600);
}

void loop() {
  int reading = analogRead(A0);
  float voltage = reading * 5.0 / 1024.0;
  float tempC = (voltage - 0.5) * 100.0;
  
  Serial.print("Temperature: ");
  Serial.print(tempC);
  Serial.println("°C");
  
  delay(3000);
}
```

---

## Sensor 2: Soil Moisture Sensor

### Wiring

| Moisture Sensor Pin | Arduino Pin |
|---------------------|-------------|
| VCC                 | 5V          |
| AOUT (Analog Out)   | Any analog pin (e.g., A1) |
| GND                 | GND         |

**Note:** You can use any analog pin (A0-A5) for AOUT. Update the code accordingly.

### Sample Code

```cpp
void setup() {
  Serial.begin(9600);
}

void loop() {
  int moisture = analogRead(A1);
  
  Serial.print("Moisture: ");
  Serial.println(moisture);
  
  delay(3000);
}
```

**Note:** Values range from 0-1023. You will need to determine what ranges indicate wet vs. dry.

---

## Sensor 3: Photoresistor Light Sensor Module

### Wiring

| Light Sensor Pin | Arduino Pin |
|------------------|-------------|
| VCC              | 5V          |
| GND              | GND         |
| AO (Analog Out)  | Any analog pin (e.g., A2) |
| DO (Digital Out) | Not used    |

**Note:** You can use any analog pin (A0-A5) for AO. Update the code accordingly. We are using the analog output (AO) for this activity, not the digital output (DO).

### Sample Code

```cpp
void setup() {
  Serial.begin(9600);
}

void loop() {
  int lightLevel = analogRead(A2);
  
  Serial.print("Light level: ");
  Serial.println(lightLevel);
  
  delay(500);
}
```

**Note:** Values range from 0-1023. You will need to determine threshold ranges for light vs. dark.

---

## Submission

- Push your completed experiments.md with all documentation to your GitHub repository
- Be prepared to demonstrate your working sensors to the instructor
- Show your Serial Monitor output for all three sensors
