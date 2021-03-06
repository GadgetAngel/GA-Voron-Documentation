---
nav_exclude: true
---
# Raspberry Pi

## Power
* The Octopus is capable of providing 5V power to run your Raspberry Pi.  To take advantage of this feature, connect the wires as shown below, from the pi header of the Octopus, to the GPIO header of the Pi.
* Use at least 24awg wire for this connection.  It may be tempting to use the common "Dupont" jumpers found in many electronics kits, however these jumpers typically use very small gauge wire, and will not carry enough current to run the Pi.
* Tie all the DC 0V (typically labelled V-) lines for all the DC power supplies together to ensure that all power supplies have the same voltage reference.

###### ![](./images/octopus11_pi_onlyPWR.png) {#octopus11_pi_onlyPWR_1}

## Connection Using Separate Power Supply
* To reduce the current load on the 5V rail of the Octopus board, the Raspberry Pi can be powered by an independent power supply.
* Use at least 24awg wire for V+ and GND connections to the Pi's power supply
* Tie all the DC 0V (typically labelled V-) lines for all the DC power supplies together to ensure that all power supplies have the same voltage reference.
* The below diagram, shows the connections for both the "Separate Power Supply" connections and "UART serial" connections.  If "Separate Power Supply" connection is wanted and "UART serial" connection is not wanted, then only use the 5V and GND connections from the diagram below (i.e. the TX and RX lines are not needed).

###### ![](./images/octopus11_to_Pi_UART.png) {#octopus11_to_PI_UART_1}

## Control

* Voron Design recommends using USB to control the Octopus, which simply requires connecting a USB-A to USB-C cable between the Octopus and Pi.
* The option also exists to use a UART serial connection from the Pi header, in place of the USB.  If you prefer this option, please see the wiring diagram located above in [Connection Using Separate Power Supply](#connection-using-separate-power-supply) and use the instructions below on the Raspberry Pi.  You will want to perform the instructions below **after Mailsail/Fluidd is installed on the Raspberry Pi.**

###### ![](./images/ConnectPitoMCU-Instructions.png) {#ConnectPitoOctopus-Instructions_1}