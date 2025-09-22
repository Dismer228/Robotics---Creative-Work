
---

# 📄 Note / Report (1–2 pages)

### Problem
We want a system that reacts to the presence of an object.  
Example: an automatic fan that turns on when someone approaches, or a conveyor motor that activates when an item comes close.  

---

### Design
- The **HC-SR04 ultrasonic sensor** measures the distance.  
- The **Arduino Uno** processes the distance data.  
- If the object is **closer than 20 cm**, the Arduino sends a signal to the transistor.  
- The **transistor** acts like a switch to safely control the DC motor.  
- A **flyback diode** is added across the motor to protect the circuit from voltage spikes when the motor stops.  

---

### Parts List
- Arduino Uno  
- Ultrasonic Sensor (HC-SR04)  
- DC Motor  
- NPN Transistor (2N2222)  
- 220 Ω resistor  
- 1N4007 diode  
- Breadboard + jumper wires  

---

### Wiring / Schematic
- **Arduino 5V → Ultrasonic VCC**  
- **Arduino GND → Ultrasonic GND, Motor −, and Transistor emitter**  
- **Arduino D9 → Ultrasonic Trig**  
- **Arduino D8 → Ultrasonic Echo**  
- **Arduino D3 → Transistor base (via 220 Ω resistor)**  
- **Motor + → Transistor collector**  
- **Diode across motor (cathode to +, anode to −)**  

---

### What Worked
- The ultrasonic sensor reliably measured distances.  
- Motor correctly turned on/off when the threshold distance was reached.  
- Serial Monitor provided real-time feedback for debugging.  

---

### What Didn’t
- Motor speed could not be finely controlled (only ON/OFF).  
- Distance readings sometimes fluctuated, causing motor to “flicker” near threshold.  
- Simulation motor doesn’t show real RPM changes — only ON/OFF state.  

---

### Future Improvements
- Use **PWM** to vary motor speed smoothly based on distance.  
- Add a **capacitor** for motor stability.  
- Replace motor with a **relay-controlled device** (lamp, fan, pump).  
- Add a **display screen** to show distance clearly.  
- Improve reliability by **averaging multiple distance readings**.  


