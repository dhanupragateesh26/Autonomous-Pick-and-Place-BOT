# 🤖 Autonomous Pick and Place Line Following Robot

An **autonomous mobile robot** capable of **line following, color detection, and automated pick-and-place operations**.

The robot navigates through a **line-based path with intersections**, identifies colored objects using a **TCS34725 color sensor**, picks the correct object using a **servo-based gripper**, and delivers it to the designated drop zone.

This project combines **robotics control, embedded systems, sensor fusion, and PID control**.

---

# 🚀 Features

* High-speed **PID-based line following**
* **Intersection detection and navigation**
* **Color-based object identification**
* Autonomous **pick and place mechanism**
* Servo-based **robotic gripper**
* **IR object detection**
* Adaptive **mission mode switching**
* Motor ramping for smooth acceleration
* Robust **intersection handling algorithm**

---

# 🧠 System Overview

The robot performs the following tasks:

1. Calibrates the **QTR line sensors**
2. Starts line following using **PID control**
3. Detects objects using **IR sensor**
4. Identifies object color using **TCS34725**
5. Counts color occurrences
6. Enters **hunting mode**
7. Picks the correct box
8. Navigates to the **drop zone**
9. Drops the object using a servo gripper

---

# 🧩 Hardware Components

| Component                    | Purpose                    |
| ---------------------------- | -------------------------- |
| Arduino (Uno / Nano / Mega)  | Main controller            |
| QTR Reflectance Sensor Array | Line detection             |
| TB6612FNG Motor Driver       | Motor control              |
| DC Motors                    | Robot movement             |
| TCS34725 Color Sensor        | Object color detection     |
| IR Sensor                    | Object presence detection  |
| Servo Motors                 | Gripper and lift mechanism |
| LiPo Battery                 | Power supply               |

---

# ⚙️ Software Architecture

Main subsystems:

**1. Line Following**

Uses PID control to keep the robot centered on the line.

**2. Intersection Detection**

Edge sensors detect intersection patterns and determine:

* Left turn
* Right turn
* Full intersection

**3. Object Detection**

IR sensor detects when an object is present.

**4. Color Identification**

TCS34725 sensor reads RGB values and determines object color.

**5. Pick and Place**

Two servo motors control:

* Lift mechanism
* Gripper

---

# 🧮 PID Control

The robot uses PID control for smooth line following.

```
MotorSpeed = P*Kp + I*Ki + D*Kd
```

Where:

* **P** = position error
* **I** = accumulated error
* **D** = rate of error change

Example parameters:

```
Kp = 0.09
Ki = 0.0001
Kd = 0.33
```

---

# 🔀 Intersection Handling

A special algorithm detects intersections reliably even when the robot approaches at an angle.

Steps:

1. Detect extreme left/right sensor trigger
2. Move forward slightly
3. Re-check sensors
4. Confirm full intersection or turn
5. Execute navigation decision

This reduces **false intersection detection**.

---

# 🦾 Pick and Place Mechanism

Two servos control the manipulator:

**Lift Servo**

* Raises and lowers the arm

**Gripper Servo**

* Opens and closes the claw

Sequence:

1. Lower arm
2. Close gripper
3. Lift arm
4. Navigate to drop zone
5. Release object

---

# 📂 Firmware

```
firmware/
│
├── phase1_pick_place.ino
└── phase2_pick_place.ino
```

These contain the robot's full control logic including:

* PID control
* sensor reading
* navigation
* object detection
* pick and place operations

---

# 🧪 Calibration

Before starting the robot:

1. Press the **calibration button**
2. Robot spins and calibrates QTR sensors
3. Wait for "Calibration Done" in serial monitor

---

# ▶️ Running the Robot

1. Upload firmware to Arduino
2. Open Serial Monitor
3. Send:

```
S
```

to start the mission.

Send:

```
s
```

to stop and reset the mission.

---



