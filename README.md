# Desk contRoller
> June 2024

> This README and request originate from my [fork](https://github.com/TechN3o/OnBoard/tree/main/projects%2FDesk%20contRoller) for the OnBoard program by Hack Club. The tutorial I referenced during development can be found [here](https://youtu.be/utBQqcuOt9U?si=lmBRnGBFkrFfYdLz).

## About the Project

Desk contRoller is a custom device designed to be embedded into a teacher's desk. It replaces and consolidates two separate infrared (IR) controllers used for the projector and projection screen in our new IT specialization classroom, where the projector is utilized constantly.

### Key Features

* **Device Control:** Operates the projector and projection screen using integrated touch buttons.
* **Information Display:** Shows the current time, the time remaining until the end of the class, custom text, and other relevant data.
* **Remote Time Adjustment:** Allows for easy time manipulation via an IoT interface (e.g., reducing time during a test or extending it during a lesson). I am currently evaluating whether to implement the control interface as a local webpage hosted on the ESP, a school server-hosted webpage utilizing an Arduino API, or a dedicated Arduino IoT Remote mobile application.
* **Network Connectivity:** Features Wi-Fi control and synchronizes the current time via an NTP server.
* **Professional Appeal:** Demonstrates our technical capabilities to the teaching staff, building trust and establishing a positive reputation for our specialization.
* **Expandability:** Leaves room for future feature implementations.

### Hardware Components

* 3D-printed chassis
* XIAO ESP32C3 development board
* 5× touch buttons (designated for projector power, screen power, and one programmable function)
* 128×32px OLED I2C display
* 2× 5mm IR LEDs
* PCF8574 I2C GPIO expander (pre-assembled on the PCB)
* 2× 0805 green LEDs for status indication
* MP2307DN (MINI360) DC-DC step-down converter for power supply
* 2× 10kOhm resistors connecting 3.3V to the I2C bus (pre-assembled on the PCB)
* Optional: 2× NPN transistors and 1× LE12CZ voltage regulator (1.2V). Because their final implementation is uncertain, six 0-ohm resistor pads are included on the board to either bypass or connect them as needed.

## Project Cost

The design was optimized to minimize expenses appropriately for the project's scope. The current cost breakdown is as follows:

* 5 assembled PCBs: $28.07
* Customs & taxes: $8.81
* Shipping (economy): $13.84
* **Total:** $50.72

## Background and Design Process

The initial problem was the presence of two separate IR controllers on the classroom desk, one of which was unreliable, making daily use impractical. I noticed an unused 6cm cable routing hole in the corner of the desk, which sparked the idea to design a device that would fit directly into that space.

The planned specifications included five touch buttons, a 128x32 OLED display, two 0805 status LEDs, and two IR LEDs to transmit signals to the hardware. The system was intended to be powered by an ESP32C3 SuperMini development board. Design-wise, the 3D-printed chassis was 6mm high and featured transparent plexiglass to showcase the internal components. The desk mount would also house a DC regulator for the buttons, and all components were to be connected using fine copper wire.

The project name, "Desk contRoller," is a tribute to my class teacher, Mr. V. Roller.

### Challenges with Version 1 (v1)

The first version was designed in Fusion 360 and 3D printed, but it encountered several critical failures:

* The design was unnecessarily small (110x50x6mm), making assembly and soldering extremely difficult.
* The point-to-point wiring was unreliable. Difficult material combinations led to poor solder joints, and two voltage supply circuits failed to function properly.
* The ESP32C3 board turned out to be defective.
* The IR LEDs malfunctioned and several burned out because their maximum forward voltage is only 1.4V. I purchased specific regulators to address this, though they may not be used in future iterations.

Ultimately, v1 was non-functional. I was left with an empty chassis, no glass cover, and no working electronics.

<table>
  <tr>
    <td width="50%"><img src="photos/v1look.png" alt="Obrázek 1"  width="100%"></td>
    <td width="50%"><img src="photos/v1look2.jpg" alt="Obrázek 2" width="100%"></td>
  </tr>
  <tr>
    <td width="50%"><img src="photos/v1look3.jpg" alt="Obrázek 3" width="100%"></td>
    <td width="50%"><img src="photos/v1look4.jpg" alt="Obrázek 4" width="100%"></td>
  </tr>
</table>

### Transition to Version 2.1 (v2.1)

After the failure of v1, I was initially discouraged until I discovered the OnBoard program. This motivated me to resume work. Using EasyEDA and online tutorials, I completely redesigned the schematic and transitioned the project to a custom printed circuit board (PCB). I also added a few necessary components to improve system reliability and am now hoping for better results.

<table>
  <tr>
    <td width="50%"><img src="photos/IMG_20240604_215652.jpg" width="100%"></td>
    <td width="50%"><img src="photos/ContRoller2.1_2024-Jun-30_10-08-46AM-000_CustomizedView2113466326.png" width="100%"></td>
  </tr>
   <tr>
    <td width="50%"><img src="photos/IMG_20240605_075407.jpg" width="100%"></td>
    <td width="50%"><img src="photos/IMG_20240628_191524.jpg" width="100%"></td>
  </tr>
   <tr>
    <td width="50%"><img src="photos/IMG_20240628_191534.jpg" width="100%"></td>
    <td width="50%"><img src="photos/IMG_20240628_191600.jpg" width="100%"></td>
  </tr>
   <tr>
    <td width="50%"><img src="photos/IMG_20240628_191627.jpg" width="100%"></td>
  </tr>
</table>
