# 💧 Automatic Water Level Monitoring and Control System

---

## 📌 Goal

The main goal of this project is to design and implement an automated system that continuously monitors the water level in a tank and controls a water pump to maintain optimal water levels without human intervention.

---

## 🎯 Detailed Objectives

- Measure the distance between the sensor and water surface using an ultrasonic sensor  
- Convert the measured distance into water level data  
- Process the sensor data using a microcontroller  
- Define threshold levels (minimum and maximum)  
- Automatically control a pump using a relay module  
- Display system data via Serial Monitor for debugging and monitoring  

---

## 🌍 Application Areas

- Household water tanks  
- Agricultural irrigation systems  
- Industrial water storage  
- Wells and reservoirs  

---

## ⚠️ Problem Statement

Manual monitoring of water levels is inefficient and can lead to:

- Water overflow  
- Pump damage due to dry running  
- Waste of electricity and water  

✅ This system solves these problems by providing automation and real-time response.

---

## 🧩 Components

### 1. Arduino Uno
- Microcontroller board based on ATmega328P  
- Processes data from sensors and controls outputs  

### 2. Ultrasonic Sensor (HC-SR04)
- Measures distance using sound waves  
- Sends a pulse and calculates time for echo return  
- Used to determine water level  

### 3. Relay Module
- Acts as a switch  
- Allows Arduino to control high-voltage devices like a pump  

### 4. Water Pump
- Moves water into the tank  
- Controlled automatically via relay  

### 5. Jumper Wires
- Used for electrical connections between components  

### 6. Resistors
- Protect components from excessive current  

### 7. Power Supply
- Provides energy for Arduino and external devices  

---

## 🔌 Connection Diagram

### Ultrasonic Sensor Connections

| Component Pin | Arduino Connection |
|--------------|------------------|
| VCC          | 5V               |
| GND          | GND              |
| TRIG         | Digital Pin 9    |
| ECHO         | Digital Pin 10   |

### Relay Module Connections

| Component Pin | Arduino Connection |
|--------------|------------------|
| IN           | Digital Pin 7     |
| VCC          | 5V                |
| GND          | GND               |

### Pump Connection

- Connected through relay terminals:
  - **COM (Common)**
  - **NO (Normally Open)**  

👉 When relay is activated → circuit closes → pump turns **ON**

---

## ⚙️ Program Structure

### 1. Pin Definitions
Pins are assigned for sensor and relay control.

### 2. Setup Function
- Initializes pin modes  
- Starts serial communication  

### 3. Loop Function
Runs continuously:
- Sends ultrasonic signal  
- Receives echo signal  
- Calculates distance  
- Compares with thresholds  
- Controls pump accordingly  

---

## 💻 Code

```cpp
#define TRIG_PIN 9
#define ECHO_PIN 10
#define RELAY_PIN 7

long duration;
int distance;

// threshold levels
int minLevel = 20; // low water level
int maxLevel = 5;  // high water level

void setup() {
  pinMode(TRIG_PIN, OUTPUT);
  pinMode(ECHO_PIN, INPUT);
  pinMode(RELAY_PIN, OUTPUT);

  Serial.begin(9600);
}

void loop() {
  // send ultrasonic pulse
  digitalWrite(TRIG_PIN, LOW);
  delayMicroseconds(2);
  digitalWrite(TRIG_PIN, HIGH);
  delayMicroseconds(10);
  digitalWrite(TRIG_PIN, LOW);

  // read echo signal
  duration = pulseIn(ECHO_PIN, HIGH);

  // calculate distance 
  distance = duration * 0.034 / 2;

  // print data
  Serial.print("Distance: ");
  Serial.println(distance);

  // control logic
  if (distance > minLevel) {
    // Low water level → turn pump ON
    digitalWrite(RELAY_PIN, LOW);
    Serial.println("Pump ON");
  } 
  else if (distance < maxLevel) {
    // High water level → turn pump OFF
    digitalWrite(RELAY_PIN, HIGH);
    Serial.println("Pump OFF");
  }

  delay(1000);
}

