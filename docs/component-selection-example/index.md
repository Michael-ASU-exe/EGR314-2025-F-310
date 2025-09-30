---
title: Component Selection
---

# Major Hardware Selection

<div class="full-bleed">
  <div class="inner">

<details>
<summary><h2>Microcontroller Selection</h2></summary>

<table>
  <thead>
    <tr>
      <th>Component</th>
      <th>Image</th>
      <th>Advantages</th>
      <th>Disadvantages</th>
      <th>Link</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>ESP32-WROOM</strong></td>
      <td><img src="../Images/ESP32.png" width="130"/></td>
      <td>
        Familiar toolchain (MPLAB X + MCC Melody)<br/>
        Plenty of docs/examples<br/>
        Good peripherals for class labs
      </td>
      <td>
        8-bit CPU limits vs. 32-bit MCUs<br/>
        Lower library ecosystem than ARM
      </td>
      <td><a href="https://www.digikey.com/en/products/detail/espressif-systems/ESP32-DEVKITC-32UE/12091813">Datasheet</a></td>
    </tr>
    <tr>
      <td><strong>Raspberry Pi Pico</strong></td>
      <td><img src="../Images/Raspberry.png" width="130"/></td>
      <td>
        Write a few pros
      </td>
      <td>
        Write a few cons
      </td>
      <td><a href="insert url here"> Datasheet</a></td>
    <tr>    
    <tr>
      <td><strong>Another alternatice to ESP32</strong></td>
      <td><img src="../Images/Raspberry.png" width="130"/></td>
      <td>
        Write a few pros
      </td>
      <td>
        Write a few cons
      </td>
      <td><a href="insert url here"> Datasheet</a></td>
    <tr>    
  </tbody>
</table>

</details>




<details>
<summary><h2>Power Regulator Selection</h2></summary>

| Component | Image | Advantages | Disadvantages | Link |
|---|---:|---|---|:--:|
| **LM2596S-3.3V** | ![lm2596](../Images/lm2596.png){ width="130" } |
<ul>
<li>Up to 3 A, efficient buck</li>
<li>Great for higher Vin → 3.3 V</li>
</ul> |
<ul>
<li>Needs external inductor/diode/caps</li>
<li>Can introduce switching noise</li>
</ul> | [Product](https://www.ti.com/product/LM2596) |

</details>

<details>
<summary><h2>Sensor Selection</h2></summary>

| Component | Image | Advantages | Disadvantages | Link |
|---|---:|---|---|:--:|
| **TC74A4-3.3V** | ![tc74](../Images/tc74.png){ width="130" } |
<ul>
<li>I²C temperature sensor, simple</li>
<li>Low parts count</li>
</ul> |
<ul>
<li>±2 °C typ accuracy</li>
</ul> | [Datasheet](https://www.microchip.com/en-us/product/TC74) |

</details>

<details>
<summary><h2>Motor Driver Selection</h2></summary>

| Component | Image | Advantages | Disadvantages | Link |
|---|---:|---|---|:--:|
| **DRV8825** | ![drv8825](../Images/drv8825.png){ width="130" } |
<ul>
<li>Stepper driver, microstepping</li>
<li>Common, lots of examples</li>
</ul> |
<ul>
<li>Needs careful current/thermal setup</li>
</ul> | [Datasheet](https://www.ti.com/product/DRV8825) |

</details>

<details>
<summary><h2>Motor Selection</h2></summary>

| Component | Image | Advantages | Disadvantages | Link |
|---|---:|---|---|:--:|
| **NEMA-17 Stepper** | ![nema17](../Images/nema17.png){ width="130" } |
<ul>
<li>Widely available, predictable torque</li>
</ul> |
<ul>
<li>Lower top speed than DC motors</li>
</ul> | [Example](https://www.pololu.com/) |

</details>

  </div>
</div>
