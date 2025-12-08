---
title: Block Diagram 
---

![Team block diagram1](Images/EGR310-Block-Diagram1.png)

Since the team's initial conception of our block diagram, we have made changes to the wireless communication aspect, transitioning from MQTT to the ESP-NOW protocol between the microcontroller and the humidity sensor and the thermal imaging camera.

The team had structured the block diagram in such a way that each individual member has their own subsystem to be work on and be responsible for. The block diagram that you see above consists of the designated microcontroller, a buck regulator to step down voltage to the required 3.3V threshold, a thermal camera and a sensor system both running on I2C protocol and a motor driver to add mechanical movement to our device. Our diagram meets the main requirements of having a wireless communication protocol, a serial advanced communication protocol, having atleast one sensor and a motor subsystem and having a fixed power supply.

