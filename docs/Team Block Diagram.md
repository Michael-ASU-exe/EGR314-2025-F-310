---
title: Block Diagram 
---

![Team block diagram1](Images/EGR310-Block-Diagram1.png)

Since the team's initial conception of our block diagram, we have made changes to the wireless communication aspect, transitioning from MQTT to the ESP-NOW protocol between the microcontroller and the humidity sensor and the thermal imaging camera.

The team had structured the block diagram in such a way that each individual member has their own subsystem to be work on and be responsible for. The block diagram that you see above consists of the designated microcontroller, a buck regulator to step down voltage to the required 3.3V threshold, a thermal camera and a sensor system both running on I2C protocol and a motor driver to add mechanical movement to our device. Our diagram meets the main requirements of having a wireless communication protocol, a serial advanced communication protocol, having atleast one sensor and a motor subsystem and having a fixed power supply.

![Team 310 Sequence Diagram](<Images/Team 310 Sequence Diagram.png>)

The sequence diagram above demonstrates how the overall system behavior achieves the intended functionality of collecting environmental data and reacting through controlled motor movement. The user needs a system that continuously monitors humidity and temperature conditions while adjusting motor positioning in response to changing environmental conditions.
The sequence diagram satisfies these needs by showing the ESP32 initiating all communication and retrieving data from both the humidity sensor and the thermal camera using their appropriate digital interfaces. The return messages from the sensors ensure that the ESP32 receives complete and up-to-date environmental information. The diagram then shows the ESP32 interpreting this data and issuing motor control signals to the motor driver. This flow ensures that sensor readings directly influence mechanical output, meeting the requirement for responsive actuation.
Furthermore, the sequential order makes the timing and dependencies clear: power must be applied, interfaces must initialize, sensor data must be collected, and processing must occur before any motor movement. This strict operational sequence ensures safe, predictable, and requirement-compliant system behavior.

# Decision Making Process

The team designed the message structure around clarity, modularity, and protocol consistency. Because the ESP32 serves as the controller, the team agreed that it should always initiate communication with each subsystem. This eliminated unnecessary complexity and ensured that all messages followed a predictable request-and-response pattern.
For the sensors, the team followed the manufacturer communication standards—using I²C for the humidity sensor and digital communication for the thermal camera. This ensured compatibility and minimized software overhead. Each message contains a clear purpose: the ESP32 sends a command, the device returns data, and the ESP32 acknowledges or uses that data immediately.
For the motor driver, the message structure was intentionally kept simple, consisting of step and direction control signals rather than complex data packets. This decision increases reliability and aligns with standard stepper motor driver interfaces.
Through this structured approach, the team ensured that message handling remained deterministic, easy to debug, and fully aligned with the functional requirements of synchronized sensing and actuation.

# Top 5 Biggest Changes To Our Software Design Since Initial Proposal

## 1. Migration of the Thermal Camera Subsystem from MicroPython to CircuitPython

Originally, the team planned to program all subsystems—including the thermal imaging camera—using MicroPython for consistency and simplified integration. However, during implementation, the team discovered that no functional or stable MicroPython library existed for the selected thermal camera module. After extensive testing and library searches, the team determined that CircuitPython was the only platform providing a reliable, well-supported driver. This required rewriting the thermal camera codebase, adapting communication routines, and restructuring the ESP32 interface to handle data processed externally through CircuitPython. This change represented the most significant deviation from the initial proposal, as it required modifying the software architecture and planning for interpreter-specific behavior.

## 2. Clear Separation of Sensor Request and Response Handling

Originally, the software proposal grouped sensor reads together in a single function call. As the design evolved, the team realized that each sensor needed dedicated request-and-response steps for reliability and timing control. The sequence diagram reflects this by showing explicit commands and return messages for humidity and thermal data. This resolved issues with inconsistent sensor timing and improved modularity.

## 3. Adoption of ESP32-Initiated Communication Structure

The initial design allowed for potential sensor-initiated interrupts. The team later removed this complexity after determining that the ESP32 should remain the sole initiator of all communication to simplify scheduling and improve determinism. This change is visible in the sequence diagram, where every data exchange begins with an ESP32 command.

## 4. Removal of Unnecessary Power-Up Dependencies

The original software design attempted to sequence subsystem startup artificially. After refining the hardware understanding, the team simplified the logic so that only the ESP32 requires an explicit software initialization stage, while the sensors naturally become ready as soon as they receive regulated voltage. This adjustment reduces code complexity and aligns with typical embedded design practices. The diagram now shows power being distributed without software-controlled sequencing.

## 5. Explicit Initialization Phase Added to System Startup

The proposal did not include a dedicated initialization stage. During development, the team recognized the need for proper interface setup—such as I²C configuration and GPIO assignment—before any data exchange. The current sequence diagram includes an “Initialize interfaces” step, solving issues related to unstable startup behavior.

