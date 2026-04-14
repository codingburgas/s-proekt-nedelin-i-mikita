# Раздробете проектът си на малки стъпки и ги опишете в план.
**Week 1: Planning and Preparation**
**Goal:** Purchase components

**Both:**

* Understand how the system works
* Divide the tasks
* Make a list of required parts

**Person 1 (Hardware):**

* Chooses a sensor (ultrasonic or waterproof)
* Researches how to connect it to ESP32

**Person 2 (Software):**

* Researches:

  * how ESP32 sends data (WiFi)
  * platform

---

**Week 2: Initial Testing**
**Goal:** ESP32 + sensor are working

**Person 1:**

* Connects ESP32 to the sensor
* Tests whether it measures distance

**Person 2:**

* Writes simple code to read data
* Displays the result in Serial Monitor

---

**Week 3: Data Processing**
**Goal:** Convert distance into water level

**Person 1:**

* Measures a real container (tank/box)
* Assists with testing

**Person 2:**

* Converts distance into percentage (0–100%)
* Adds logic:

  * minimum level
  * maximum level

---

**Week 4: Pump Control**
**Goal:** Automation

**Person 1:**

* Connects a relay module
* Connects the pump safely

**Person 2:**

* Adds logic:

  * if level is low → turn on pump
  * if level is high → turn off pump

---

**Week 5: Web Visualization**
**Goal:** Data visible online

**Person 1:**

* Tests hardware stability

**Person 2:**

* Creates:

  * a graph (level over time)
  * display of current level

---

**Week 6: Finalization and Presentation**
**Goal:** Completed project

**Person 1:**

* Places everything in a box
* Organizes the wiring

**Person 2:**

* Prepares presentation:

  * how the system works
  * photos/video
  * demonstration

**Both:**

* Test the entire project
* Rehearse the presentation
