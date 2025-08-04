**Specification of Demonstration**

The analog filter demonstrator board will contain an MCU (ESP32), which will control the filter's parameters via input from mobile application GUI. This GUI in the smartphone will be connected to the MCU via its WLAN or BT module. The control parameters are clock frequency (f_CLK), center frequency (⍵0), Quality Factor (Q) and type of filter configuration (Low Pass, High Pass, Band Pass, Band Stop).

The input signal is sent from a Signal Generator to the MAX263 Filter IC from Maxim/AnalogDevices. The output will be viewed on the oscilloscope.

**Specification of the Filter**
The varying degree or scaling of clock frequency can be realized by Frequency Divider (Division by N). A programmable 4-to-1 analog switch (ADGS1414D) can provide the selection of clock signal as well as the selectivity of different output stages of filter. 

The output is passed through an output buffer in order to provide a proper output with maximum output swing. Output can be rail-to-rail and it should be settled within one clock cycle. Limiting frequency or the dominant pole may be obtained from Switched Capacitor circuitry. The resonance frequency can be adjusted by changing f_CLK according to f_CLK/fc ratio. The level shifting of voltages is achieved by transistor logic and pull up/down resistor.

Shift registers may be utilized for supplying the control parameters of the filter which are: mode selection, ⍵0, Q and clock frequency. Also the MUX select lines. For example, 5 bits can be allocated for choosing ⍵0, 2 bits for mode selection, 1 bit for clock frequency and 7 bits for choosing Q (corresponding to the MAX263).

The dual supply voltage can be implemented with ground in between the voltage levels. We may hard-code to achieve cascading of higher order filters.

Filter has to be offset-free even though Op-Amp adds offset to its inputs.

**Function of Each Block**

7.1. Microcontroller Unit

ESP32 is preliminarily chosen as the target MCU for realizing it. The precise one to use is not finalized it.

7.2 Shift Register
SN74HCT595 Shift Register is used for increasing the number of digital outputs from the MCU. The ‘T’ stands for TTL logic level. Its preference over SN74HC164 is due to the low input threshold to distinguish between high and low. Whereas SN74HC164 requires 3.5V+ to recognize as HIGH, SN74HCT164 requires only 2V+.

[_More to be added later_]
