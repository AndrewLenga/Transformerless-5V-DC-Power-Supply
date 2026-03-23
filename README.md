⚡ Transformerless 5V DC Power Supply
This repository contains the schematic and design for a Transformerless Linear Power Supply. This circuit uses a Capacitive Dropper instead of a bulky transformer to step down mains voltage, resulting in an extremely compact and lightweight footprint.

⚠️ DANGER: NO GALVANIC ISOLATION ⚠️
This circuit is NOT isolated from the AC mains.
Live Potential: Every component in this circuit, including the DC output terminals, must be considered "Live" at 110V/230V AC.
Safety: Never touch any part of the circuit while it is plugged in. The device must be housed in a fully insulated, non-conductive (plastic) enclosure.
Testing: Use an Isolation Transformer during development to prevent electric shock or damage to your oscilloscope/multimeter.

🔍 Circuit Overview
The design replaces the traditional magnetic transformer with the reactance of a high-voltage capacitor. By using a capacitive voltage divider, the circuit limits the current flowing from the AC mains before rectifying and regulating it.
Key Specifications
Input: 110V/230V AC Mains.
Output: Regulated +5V DC.
Current Capability: Low-current (typically <100mA), determined by the value of C3.
Applications: IoT sensors, LED night lights, and low-power microcontrollers in sealed environments.

🛠️ How It Works
1. The Capacitive Dropper (C3 & R1)
C3 (Reactance): This X2-rated capacitor acts as the "dropper." It provides a high impedance to the 50/60Hz AC signal, effectively stepping down the voltage without the heat generation associated with power resistors.
R1 (Bleeder): A high-value resistor (470kΩ+) connected in parallel to C3. It ensures that when the device is unplugged, the charge stored in C3 is safely discharged.
2. Full-Wave Rectification (D1–D4)
Four 1N4007 diodes arranged in a bridge configuration convert the stepped-down AC into pulsating DC.
3. Filtering & Zener Clamping (C1, D5/D6)
C1 (Filter): Smooths the pulsating DC into a steadier voltage.
D5 & D6 (Zener Diodes): These act as a safety clamp. They prevent the voltage at the input of the regulator from spiking too high, which could happen if the circuit is powered on without a load.
4. Linear Regulation (U1, C2, D8)
U1 (LM7805): Standard linear regulator that provides a precise 5V DC output.
C2 (Stability): A small output capacitor that improves transient response and prevents oscillation.
D8 (Indicator): An LED with a current-limiting resistor (R4) to signal that the power is active.

📊 Component List & Recommendations
Component	Identifier	Recommended Value	Requirement
Dropper Cap	C3	0.47µF - 1µF	X2-Rated (Safety Type)
Bleeder Resistor	R1	470kΩ - 1MΩ	0.5W or higher
Bridge Diodes	D1–D4	1N4007	1A, 1000V Standard
Zener Diodes	D5, D6	12V - 15V	1W Power Rating
Main Regulator	U1	LM7805	TO-220 Package
Filter Cap	C1	470µF - 1000µF	25V or higher
