# Robotics---Creative-Work

# Distance-Activated Motor (Arduino + Ultrasonic Sensor)

## Overview
This project uses an **HC-SR04 ultrasonic distance sensor** to measure how far an object is.  
If the object is **closer than 50 cm**, the Arduino turns ON a **DC motor**.  
Otherwise, the motor stays OFF.  
The system simulates an **automatic fan** or **distance-triggered machine**.

---

## Features
- Measures distance in cm using ultrasonic sensor.
- Spins motor when object is within threshold range.
- Prints distance readings to the Serial Monitor for debugging.
- Easy to expand with PWM control (motor speed based on distance).

---

## Parts List
- Arduino Uno  
- HC-SR04 Ultrasonic Sensor  
- DC Motor  
- NPN transistor (e.g., 2N2222)  
- 220 Ω resistor (for transistor base)  
- 1N4007 diode (flyback protection)  
- Breadboard & jumper wires  

---

## Wiring Summary
- **Ultrasonic Sensor**  
  - VCC → 5V  
  - GND → GND  
  - Trig → D9  
  - Echo → D8  

- **Motor + Transistor**  
  - Motor + → Collector of NPN transistor  
  - Motor − → GND  
  - Emitter → GND  
  - Base → Arduino D3 (via 220 Ω resistor)  
  - Diode across motor: cathode → Motor +, anode → Motor −  

---

## Code
```cpp
const int trigPin = 9;
const int echoPin = 8;
const int motorPin = 3; 

long duration;
int distance;

void setup() {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(motorPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  // Trigger ultrasonic pulse
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH);

  // Convert to distance (cm)
  distance = duration * 0.034 / 2;
  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");

  // Motor control
  if (distance < 20) {
    digitalWrite(motorPin, HIGH); // turn ON
  } else {
    digitalWrite(motorPin, LOW); // turn OFF
  }

  delay(200);
}
