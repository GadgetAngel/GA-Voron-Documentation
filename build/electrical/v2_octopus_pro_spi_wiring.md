
# BTT Octopus Pro V1.0 in SPI Mode

## Initial Removal of Jumpers for SPI Mode

Remove **all <span class="color-blind-yellow">YELLOW</span>** on-board jumpers, located at the positions shown below.

<div>

<!--
To be able to supply the Voron user and Voron Helper staff with an easy access LINK for all diagrams, I tested
a couple of different methods.  I found one method that allowed the user to left-click on the diagram
and it would open the diagram up in the web browser. I choose to not use this method because ther would be
a lot of Voron users who probably would activate this by accident and then not beable to get themselves back.

The method I choose was one that will display the LINK symbol to the left of the diagram and without adding
any title text. I ended up using header 6 with a blank title and then I use a Kramdown Syntax for specifying
a Header ID.

If I use the GFM Parser for creating a header anchor with an empty title the static web page produced
DOES NOT show the LINK symbol to the left of the diagram. The Link is setup but only I can use it in the 
web page code. An outside Voron Helper could not access the Link Address.  The GFM Parser syntax for "header anchors" forces you to use a text in the title.  If you use a title text then the LINK symbol will be generated.

But with further reading I found that Kramdown Parser does allow a "title text of empty" which produces the LINK symbol to the left of the diagram and generates the LINK address that Voron Users and Voron Helpers can access by right-clicking on the LINK symbol. The documentation for this can be found at https://kramdown.gettalong.org/syntax.html#headers ; look for "Specifying a Header ID"
-->

</div>

###### ![](./images/Octopus_Pro_PREP-Removal_150.png) {#Octopus_Pro_PREP-Removal_SPI}
{:.no_toc}

[Go Back to the Table of Contents](v2_octopus_pro_uartspi_wiring.html#table-of-contents)

## Initial Preparation for SPI Mode - Set Jumpers

* Ensure the jumpers of "DIAG Jumper Block" are all removed to avoid the influence of TMC2209 DIAG on the endstop.

* Ensure the removal of the USB 5V power supply jumper ("Power Selection Jumper") which avoids the interaction between the USB 5V of Raspberry Pi and the DC-DC 5V of the motherboard.

* Set the on-board jumpers, located at the positions as shown by the **<span class="color-blind-green">GREEN</span>** jumpers in the diagram below:

###### ![](./images/Octopus_Pro_F446_SPI_Mode_for_Prep_150.png) {#Octopus_Pro_F446_SPI_Mode_for_Prep}
{:.no_toc}

[Go Back to the Table of Contents](v2_octopus_pro_uartspi_wiring.html#table-of-contents)

### (FAN & MOTOR POWER & PROBE) Voltage Selection Headers
{:.no_toc}

* In the diagram below, the **COLORED BOXES** indicate the headers with **<span class="color-blind-green">GREEN</span>** jumpers which are set for 24VDC.

* In the diagram below, the **<span class="color-blind-blue">BLUE box</span>** indicates the "fan voltage selection headers" with **<span class="color-blind-green">GREEN</span>** jumpers which are set for 24VDC.

    * __<span class="underline-double-trouble color-blind-red">IMPORTANT:</span>__ **If fans that use 5VDC or 12VDC are used, please take <span class="color-blind-red">NOTE</span> of these "fan voltage selection headers" and set the jumpers to the appropriate jumper position so that the correct fan voltage will be produced to run the 5VDC or 12VC fan.  If the fan voltage selection jumper is set for 24VDC and a 5VDC/12VDC fan is connected to it, the Octopus Pro board will be damaged.**

* In the diagram below, the **<span class="color-blind-orange">ORANGE box</span>** indicates the "probe voltage selection header" with a **<span class="color-blind-green">GREEN</span>** jumper which is set for 24VDC. If a PROBE voltage of 5VDC or 12VDC is desired, this jumper needs to be changed. If the voltage required by the PROBE device does not match the voltage selected by the "probe voltage selection Jumper" then the Octopus Pro board could be damaged.

* In the diagram below, the **<span class="color-blind-orange">ORANGE box made with a dash line</span>** indicates the PT100/PT1000 DIP switches. The default setting of all the DIP switches is set to OFF. This default setting is undefined.  Therefore, **before you install the Octopus Pro board, a valid setting must be chosen.  Choose between a 2-wire or 4-wire arrangement: ([2-wire: 7, 11] or [4-wire: 4, 8])**

* In the diagram below, the **<span class="color-blind-yellow">YELLOW box</span>** indicates the motor power selection headers with **<span class="color-blind-green">GREEN</span>** jumpers which are set for 24VDC.  Each stepper motor driver has this header so that each individual socket can be set to either 24VDC (V<sub>in</sub>) or MOTOR_POWER voltage.

    * __<span class="underline-double-trouble color-blind-red">IMPORTANT:</span>__ **If the motor power selection headers DO NOT match the voltage being supplied to the stepper driver, the Octopus Pro board will be damaged along with the stepper motor driver.  Set each of the motor power selection jumpers to the appropriate position so that the stepper driver _voltage needed, matches the PSU voltage selected_ by the motor power selection jumper. For example, If the stepper motor driver voltage is set for 48VDC and the actual stepper motor driver runs at 12VDC, the Octopus Pro board and the stepper motor driver will be damaged.**

* __<span class="underline-double-trouble color-blind-red">IMPORTANT:</span>__ **Double check all the** __<span class="color-blind-green">GREEN</span>__ **jumpers are set appropriately, especially the jumpers called out by the _COLORED BOXES_, BEFORE the power supply is connected.**

[Go Back to the Table of Contents](v2_octopus_pro_uartspi_wiring.html#table-of-contents)

### (FAN & MOTOR POWER & PROBE) Voltage Selection Diagram
{:.no_toc}

###### ![](./images/Octopus_Pro_F446_SPI_VoltageSelect_150.png) {#Octopus_Pro_F446_SPI_VoltageSelect}
{:.no_toc}

[Go Back to the Table of Contents](v2_octopus_pro_uartspi_wiring.html#table-of-contents)

## Stepper Motor Drivers
{:.no_toc}
* Inspect the stepper motor drivers for left over rosin, and clean with IPA, if needed
* Install heat sinks on all stepper motor drivers

## MCU Wiring for SPI Mode

* Connect <span class="tshadow-red-MCU-desciption fs_percent_125">24V and GND (V+ and V-)</span> from the PSU to <span class="tshadow-bg-MCU-desciption fs_percent_125">PWR</span> and <span class="tshadow-bg-MCU-desciption fs_percent_125">MOTOR_POWER</span>
* Connect <span class="tshadow-gold-MCU-desciption fs_percent_125">stepper driver</span> for <span class="tshadow-gold-MCU-desciption fs_percent_125">the B Motor (gantry left)</span> into position <span class="tshadow-b-orgn-MCU-desciption fs_percent_125">DRIVER0</span>
* Plug in <span class="tshadow-gold-MCU-desciption fs_percent_125">stepper motor</span> for <span class="tshadow-gold-MCU-desciption fs_percent_125">the B Motor (gantry left)</span> into position <span class="tshadow-b-orgn-MCU-desciption fs_percent_125">MOTOR0</span>
* Connect <span class="tshadow-gold-MCU-desciption fs_percent_125">stepper driver</span> for <span class="tshadow-gold-MCU-desciption fs_percent_125">the A Motor (gantry right)</span> into position <span class="tshadow-lt-blue-MCU-desciption fs_percent_125">DRIVER1</span>
* Plug in <span class="tshadow-gold-MCU-desciption fs_percent_125">stepper motor</span> for <span class="tshadow-gold-MCU-desciption fs_percent_125">the A Motor (gantry right)</span> into position <span class="tshadow-lt-blue-MCU-desciption fs_percent_125">MOTOR1</span>
* Connect <span class="tshadow-gold-MCU-desciption fs_percent_125">stepper driver</span> for <span class="tshadow-gold-MCU-desciption fs_percent_125">the Z</span> into positions <span class="tshadow-dk-purple-MCU-desciption fs_percent_125">DRIVER2</span>
* Plug in <span class="tshadow-gold-MCU-desciption fs_percent_125">stepper motor</span> for <span class="tshadow-gold-MCU-desciption fs_percent_125">the Z</span> into positions <span class="tshadow-dk-purple-MCU-desciption fs_percent_125">MOTOR2_1</span>
* Connect <span class="tshadow-gold-MCU-desciption fs_percent_125">stepper driver</span> for <span class="tshadow-gold-MCU-desciption fs_percent_125">the Z1</span> into positions <span class="tshadow-dk-purple-MCU-desciption fs_percent_125">DRIVER3</span>
* Plug in <span class="tshadow-gold-MCU-desciption fs_percent_125">stepper motor</span> for <span class="tshadow-gold-MCU-desciption fs_percent_125">the Z1</span> into positions <span class="tshadow-dk-purple-MCU-desciption fs_percent_125">MOTOR3</span>
* Connect <span class="tshadow-gold-MCU-desciption fs_percent_125">stepper driver</span> for <span class="tshadow-gold-MCU-desciption fs_percent_125">the Z2</span> into positions <span class="tshadow-dk-purple-MCU-desciption fs_percent_125">DRIVER4</span>
* Plug in <span class="tshadow-gold-MCU-desciption fs_percent_125">stepper motor</span> for <span class="tshadow-gold-MCU-desciption fs_percent_125">the Z2</span> into positions <span class="tshadow-dk-purple-MCU-desciption fs_percent_125">MOTOR4</span>
* Connect <span class="tshadow-gold-MCU-desciption fs_percent_125">stepper driver</span> for <span class="tshadow-gold-MCU-desciption fs_percent_125">the Z3</span> into positions <span class="tshadow-dk-purple-MCU-desciption fs_percent_125">DRIVER5</span>
* Plug in <span class="tshadow-gold-MCU-desciption fs_percent_125">stepper motor</span> for <span class="tshadow-gold-MCU-desciption fs_percent_125">the Z3</span> into positions <span class="tshadow-dk-purple-MCU-desciption fs_percent_125">MOTOR5</span>
* Connect <span class="tshadow-gold-MCU-desciption fs_percent_125">stepper driver</span> for <span class="tshadow-gold-MCU-desciption fs_percent_125">the extruder motor</span> into position <span class="tshadow-neon-grn-MCU-desciption fs_percent_125">DRIVER6</span>
* Plug in <span class="tshadow-gold-MCU-desciption fs_percent_125">stepper motor</span> for <span class="tshadow-gold-MCU-desciption fs_percent_125">the extruder motor</span> into position <span class="tshadow-neon-grn-MCU-desciption fs_percent_125">MOTOR6</span>
* Connect the <span class="tshadow-gold-MCU-desciption fs_percent_125">hot end heater</span> to <span class="tshadow-pink-MCU-desciption fs_percent_125">HE0 (PA2)</span>
* Connect the <span class="tshadow-gold-MCU-desciption fs_percent_125">bed SSR (DC Control Side)</span> to <span class="tshadow-bg-MCU-desciption fs_percent_125">HE1 (PA3)</span>
* Connect the <span class="tshadow-gold-MCU-desciption fs_percent_125">part cooling fan</span> to <span class="tshadow-brown-MCU-desciption fs_percent_125">FAN0 (PA8)</span>
* Connect the <span class="tshadow-gold-MCU-desciption fs_percent_125">hot end fan</span> to <span class="tshadow-brown-MCU-desciption fs_percent_125">FAN1 (PE5)</span>
* Connect the <span class="tshadow-gold-MCU-desciption fs_percent_125">controller fans</span> to <span class="tshadow-brown-MCU-desciption fs_percent_125">FAN2 (PD12)</span>
* Connect the <span class="tshadow-gold-MCU-desciption fs_percent_125">chamber exhaust fan</span> to <span class="tshadow-lt-green-MCU-desciption fs_percent_125">FAN3 (PD13)</span>
* Connect the <span class="tshadow-yellow-MCU-desciption fs_percent_125">hot end thermistor</span> to <span class="tshadow-neon-grn-MCU-desciption fs_percent_125">T0 (PF4)</span>
* Connect the <span class="tshadow-light-purple-MCU-desciption fs_percent_125">bed thermistor</span> to <span class="tshadow-bg-MCU-desciption fs_percent_125">TB (PF3)</span>
* Connect the <span class="tshadow-green-MCU-desciption fs_percent_125">X endstop</span> to <span class="tshadow-green-MCU-desciption fs_percent_125">STOP_0 (PG6)</span>
* Connect the <span class="tshadow-b-orgn-MCU-desciption fs_percent_125">Y endstop</span> to <span class="tshadow-muted-green-MCU-desciption fs_percent_125">STOP_1 (PG9)</span>
* Connect the <span class="tshadow-pink-MCU-desciption fs_percent_125">Z endstop</span> to <span class="tshadow-light-purple-MCU-desciption fs_percent_125">STOP_2 (PG10)</span>
* Connect the <span class="tshadow-bg-MCU-desciption fs_percent_125">signal wire on the PROBE</span> to <span class="tshadow-neon-grn-MCU-desciption fs_percent_125">STOP_7 (PG15)</span>
* Connect the <span class="tshadow-red-MCU-desciption fs_percent_125">V+ an 0V wires on the probe</span> to <span class="tshadow-pink-MCU-desciption fs_percent_125">PROBE</span>
* if using a <span class="tshadow-gold-MCU-desciption fs_percent_125">mini12864 display</span>, connect to <span class="tshadow-lt-blue-MCU-desciption fs_percent_125">EXP1 & EXP2</span>, only after completing the steps <span class="tshadow-pink-MCU-desciption fs_percent_125">shown [below](#mini-12864-display)</span>

[Go Back to the Table of Contents](v2_octopus_pro_uartspi_wiring.html#table-of-contents)

## MCU Wiring Diagram for SPI Mode
<span> <br> </span>

###### ![](./images/Voron2_Wiring_Diagram_Octopus_ProF446_V1_SPI_150.jpg) {#Voron2_Wiring_Diagram_Octopus_ProF446_V1_SPI}
{:.no_toc}

* <span class="tshadow-drop-red-MCU-desciption fs_percent_110">If you want to open the above diagram, in a new tab of your web browser, and have the ability to zoom and download the diagram in JPG format then [click here](./images/Voron2_Wiring_Diagram_Octopus_ProF446_V1_SPI_150.jpg){:target="_blank" rel="noopener"}</span>

[Go Back to the Table of Contents](v2_octopus_pro_uartspi_wiring.html#table-of-contents)

## Please Ensure the Heat Sinks are Installed Before Use
{:.no_toc}
### MCU in SPI Mode with Heat Sinks Installed
{:.no_toc}
<span> <br> </span>

###### ![](./images/Octopus_Pro_SPI_Heatsinks_150.png) {#Octopus_Pro_SPI_Heatsinks}
{:.no_toc}

[Go Back to the Table of Contents](v2_octopus_pro_uartspi_wiring.html#table-of-contents)

## Raspberry Pi
{:.no_toc}
### Power 
{:.no_toc}
* The Octopus Pro is capable of providing 5V power to run your Raspberry Pi.  To take advantage of this feature, connect the wires as shown below, from the pi header of the Octopus Pro, to the GPIO header of the Pi.
* Use at least 24awg wire for this connection.  It may be tempting to use the common "Dupont" jumpers found in many electronics kits, however these jumpers typically use very small gauge wire, and will not carry enough current to run the Pi.
* Tie all the DC 0V (typically labelled V-) lines for all the DC power supplies together to ensure that all power supplies have the same voltage reference.

###### ![](./images/v2_octopus_pro_pi_onlyPWR.png) {#v2_octopus_pro_pi_onlyPWR_2}
{:.no_toc}

[Go Back to the Table of Contents](v2_octopus_pro_uartspi_wiring.html#table-of-contents)

### Connection Using Separate Power Supply
{:.no_toc}
* To reduce the current load on the 5V rail of the Octopus Pro board, the Raspberry Pi can be powered by an independent power supply.
* Use at least 24awg wire for V+ and GND connections to the Pi's power supply
* Tie all the DC 0V (typically labelled V-) lines for all the DC power supplies together to ensure that all power supplies have the same voltage reference.

###### ![](./images/v2_octopus_Pro_to_PI_UART.png) {#v2_octopus_Pro_to_PI_UART_2}
{:.no_toc}

[Go Back to the Table of Contents](v2_octopus_pro_uartspi_wiring.html#table-of-contents)

### Control
{:.no_toc}
* Voron Design recommends using USB to control the Octopus Pro, which simply requires connecting a USB-A to USB-C cable between the Octopus Pro and Pi. 
* The option also exists to use a UART connection from the Pi header, in place of the USB.  If you prefer this option, please see the wiring diagram located above in [Connection Using Separate Power Supply](#connection-using-separate-power-supply) and use the instructions below on the Raspberry Pi.  You will want to perform the instructions below **after Mailsail/Fluidd is installed on the Raspberry Pi.**

###### ![](./images/ConnectPitoMCU-Instructions.png) {#ConnectPitoOctopusPro-Instructions_2}
{:.no_toc}

[Go Back to the Table of Contents](v2_octopus_pro_uartspi_wiring.html#table-of-contents)

## SSR Wiring for SPI Mode

* Wire colors will vary depending on your locale.

###### ![](./images/BTTOctopus_Pro-ssr-SPI-wiring.png) {#BTTOctopus_Pro-ssr-SPI-wiring}
{:.no_toc}

* If you want to open the above diagram, in a new tab of your web browser, and have the ability to zoom and download the diagram in PNG format then [click here](./images/BTTOctopus_Pro-ssr-SPI-wiring.png){:target="_blank" rel="noopener"}

[Go Back to the Table of Contents](v2_octopus_pro_uartspi_wiring.html#table-of-contents)

## mini 12864 Display
{:.no_toc}
* See [the mini12864 guide](./mini12864_klipper_guide.md)

## The Klipper Configuration file for BTT Octopus Pro V1.0 Board 
{:.no_toc}
* The Klipper Configuration file from VoronDesign/Voron-2 GitHub Repo for BTT Octopus Pro 1.0 board is [located here](https://github.com/VoronDesign/Voron-2/blob/Voron2.4/firmware/klipper_configurations/Octopus/Voron2_Octopus_Config.cfg){:target="_blank" rel="noopener"}

[Go Back to the Table of Contents](v2_octopus_pro_uartspi_wiring.html#table-of-contents)

## Color PIN Diagram for BTT Octopus Pro V1.0
{:.no_toc}
For reference, here is the Color PIN diagram for the BTT Octopus Pro V1.0

###### ![](./images/BTT-Octopus-Pro-V1.0-color-PIN-V3.0.jpg) {#BTT-Octopus-Pro-V1.0-color-PIN_2}
{:.no_toc}

* If you want to open the above diagram, in a new tab of your web browser, and have the ability to zoom and download the diagram in PDF format then [click here](./images/BTT-Octopus-Pro-V1.0-Color-PIN-V3.0.pdf){:target="_blank" rel="noopener"}

* If you want to open the above diagram, in a new tab of your web browser, and have the ability to zoom and download the diagram in JPG format then [click here](./images/BTT-Octopus-Pro-V1.0-color-PIN-V3.0.jpg){:target="_blank" rel="noopener"}

[Go Back to the Table of Contents](v2_octopus_pro_uartspi_wiring.html#table-of-contents)

## Original BTT Octopus Pro V1.0 Pinout
{:.no_toc}
For reference, here is the original pinout of the BTT Octopus Pro V1.0

* Note: If you see a conflict between the original pinout and any other source, please refer back to the [BTT Octopus Pro V1.0 schematic diagram](<./images/BIGTREETECH Octopus Pro_SCH.pdf>){:target="_blank" rel="noopener"}

###### ![](./images/BIGTREETECH_Octopus_Pro-PIN-original.jpg) {#BIGTREETECH_Octopus_Pro-PIN-original_2}
{:.no_toc}

* If you want to open the above diagram, in a new tab of your web browser, and have the ability to zoom and download the diagram in PDF format then [click here](<./images/BIGTREETECH Octopus Pro - PIN.pdf>){:target="_blank" rel="noopener"}

[Go Back to the Table of Contents](v2_octopus_pro_uartspi_wiring.html#table-of-contents)

## The BTT's GitHub Repo for the Octopus Pro V1.0 board
{:.no_toc}
* BTT's documentation for Octopus Pro V1.0 board is [located here](https://github.com/bigtreetech/BIGTREETECH-OCTOPUS-Pro){:target="_blank" rel="noopener"}

[Go Back to the Table of Contents](v2_octopus_pro_uartspi_wiring.html#table-of-contents)

## After I have Wired up the MCU Board, What Comes Next?<span> <br> </span>
<span> <br> </span>
{:.no_toc}
![](./images/VoronHex_Number_1_small.png)   Once the MCU board is wired up and wire management has been performed, the next step is to compile and install the Klipper Firmware, please see [The Build ═► Software Installation](../../build/software/index.md#software-installation)

![](./images/VoronHex_Number_2_small.png)   Once the MCU board has the Klipper Firmware Installed, the next step is to edit the Klipper Config file (Voron2_Octopus_Config.cfg) to ensure your Voron build matches your Klipper Config file, please see [The Build ═► Software Configuration](../../build/software/configuration.md#software-configuration).  Please use the Color PIN Diagrams, [displayed above](#color-pin-diagram-for-btt-octopus-pro-v10), as a source of information. 

![](./images/VoronHex_Number_3_small.png)   After editing the Klipper Config file (Voron2_Octopus_Config.cfg), the next step is to check all the Motors and the mechanics of the Voron printer, please see [The Build ═► Initial Startup Checks](../../build/startup/index.md#initial-startup-checks)

[Go Back to the Table of Contents](v2_octopus_pro_uartspi_wiring.html#table-of-contents)
