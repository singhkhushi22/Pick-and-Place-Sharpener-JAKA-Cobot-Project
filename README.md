# 📄 Pick and Place Sharpener – JAKA Cobot Project

## **Project Overview**

This project demonstrates an **industrial pick-and-place application** using a **JAKA collaborative robot** equipped with a **pneumatic gripper**. The cobot is programmed to pick up a **sharpener** from a fixed position and place it at a designated location.

The motion in this repo is achieved using **joint movement commands (`MoveJ`)**, which are fast and simple but do not guarantee straight-line paths.

---

## **Hardware Used**

* **JAKA Collaborative Robot** (6-axis)
* **Pneumatic Gripper** (for grasping the sharpener)
* **Air Compressor & Pneumatic Circuit**
* **Sharpener** (target object)
* **Work Table & Fixtures**

---

## **Software & Programming**

* **JAKA Programming Environment** (JAKA App / JAKA SDK)
* Programming Commands:

  * **MoveJ** (Joint Movement – used for all motions in this repo)
  * **Set DO** (Digital Output – used for gripper open/close)

---

## **Working Principle**

1. **Initialization & Home Position** – The cobot moves to a safe "home" position.

2. **Approach Position** – The cobot uses **MoveJ** to reach the pre-pick waypoint.

3. **Pick Action** –

   * The cobot moves to the pick position with `MoveJ`.
   * The pneumatic gripper closes to grasp the sharpener.

4. **Transfer Path** – The cobot moves with `MoveJ` to the placement location.

5. **Place Action** –

   * The cobot opens the pneumatic gripper to release the sharpener.
   * Retracts back to the home or standby position.

---

## **Actual Program Flow**

```text
MoveJ → Home
MoveJ → Pre-pick position
MoveJ → Pick position
Set DO (DO1 = On → Gripper Close)
MoveJ → Retract from pick
MoveJ → Pre-place position
MoveJ → Place position
Set DO (DO1 = Off → Gripper Open)
MoveJ → Retract from place
MoveJ → Home
```

📸 **Program Screenshot:**

![Pick and Place Sharpener Program](pickplacesharpner.jpg)

---

## **Motion Commands in Use**

### **MoveJ (Joint Movement)**

* Moves each joint to the target position using the shortest possible path.
* Best for **approach, retract, and non-critical path moves**.
* Faster but not always a straight-line path.

---

## **Pneumatic Gripper Control**

* **Set DO = On** – Closes the gripper (grasps sharpener).
* **Set DO = Off** – Opens the gripper (releases sharpener).
* Actuated via **digital I/O signals** from the cobot’s control panel.

---

## **Safety Considerations**

* Safe approach height before moving down to pick.
* Use of waypoints to avoid collisions.
* Pneumatic pressure adjusted to prevent object damage.

---

## **Applications**

* Stationary object handling
* Assembly line feeding
* Educational robotics demonstration

---

## **Video Demonstration**

*([![Watch the Demo](thumbnail.png)](https://drive.google.com/file/d/1_QK3mkfCwfpWjCR7SRSeIoO2WEfEr6dQ/preview))*









