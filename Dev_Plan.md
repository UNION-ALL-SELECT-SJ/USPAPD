# Requirements

The USPAPD is intended to be a portable, compact communication protocol debugging tool, aimed at being able to identify information flowing through electronic channels in real time.

It’s primary usage environment is an electronics workshop and will assist developers in analysing various activities around the exposed electronics of an embedded device.

The USPAPD is aimed at debugging the hardware of embedded devices, microcomputers, robots and simple automotive/industrial equipment.

Considering this it will need to be able to intake and interpret data from the following protocols:

- SPI, I2C, UART
    - Common serial protocols in many embedded devices and microcomputers. These are straightforward to handle and are natively implemented on nearly every MCU in existence.
- FDCAN
    - Automobiles and industry are a bit out of scope, though variants of CAN are not uncommon in larger robots and hobby vehicles, particularly with the prevalence of CANopen.
    - interoperable with BxCAN and Classical CAN, ideally supporting up to 8Mbit/s though 2Mbit/s is the most realistic baseline
    - Specific CANopen support highly preferable
- USB (as device)
    - Despite USB’s prevalence in consumer computer peripherals, this will be by far the most niche function of the USPAPD considering its lack of ability to reply to messages. (Since USB is request-response driven). USB hosts that simply dump data in one direction are the exception, not the norm.
    - Host support is clearly not appropriate as this would need the USPAPD to have drivers installed for every distinct USB device. This task is thus better suited to a PC which already has extensive USB support.
- Parallel: 8, 16 or 32 bit bus
    - Internal/external clock synchronous or edge-driven configurable
    - Although clock synchronised parallel buses are commonplace in microcomputers, the ability to probe into such a bus is questionable. The USPAPD will nonetheless include this for any prototype microcomputers incomplete enough to have an exposed bus.
    - Exposed edge-driven buses are unlikely to be encountered in consumer electronics, considering they are often buried in the micro-wiring of an IC. Though this may come in handy if one were building their own combinational circuits on a larger board.
- Analog
    - Analog data is commonplace in many simpler sensors used in the hobby market (often designed to measure simple scalars such as temperature), common also in audio and signalling. The USPAPD will incorporate the ability to read from analog data sources as the MCU will likely come with several ADC’s regardless. Interestingly, the ADC in conjunction with the real-time graphing system transforms the USPAPD into some kind of ***Low-resolution single channel digital quasi-oscilloscope.***
    - Disclaimer: Generally aimed at lower sampling rate 12-bit ADC territory. USPAPD will not aim to be a mixed signal, audio nor DSP oriented device, nor will it try to fulfil the role of a traditional oscilloscope.

To provide the best user experience and the most utility possible, the USPAPD will incorporate several UI elements to best assist with interpreting it’s data:

- Configurable display formats
    - Decimal, hexadecimal integers
    - Single and double precision floating point
    - UTF-8 text, with text-wrapping
- Historical data
    - Stores a large quantity of bytes which can be readily browsed through in specified format
- Real-time graphing
    - Graphs numerical data with options for scaling

In-order to accommodate communication protocols, the USPAPD will need to incorporate several controls:

- External/internal clock toggle
    - Configurable baud rate for internal clock
    - This is needed for all synchronous communications
- Data history browsing
- Graph sizing
    - Zoom/Scaling
    - Options for Linear, Logarithmic (dB) etc.

## Example Use Cases

# Order of Operations

This project will use a agile-like development methodology, with individual features being independently developed and added to the main tech-stack when they are ready for integration. 

Considering the great variance of difficulty in many features, the project will be divided into 2 separate stages with each stage containing features of similar complexity and difficulty.

Since this is generally a hardware oriented project, formal rollouts of a viable PCB-based prototype will happen at the end of each stage, with proper polish (such as a device casing, UX improvements and user documentation) being implemented at the very end of the final stage.

Here is the general flow of events:

## Stage 1

- [ ]  Determine and acquire basic hardware
    - [ ]  Controls
    - [ ]  display
    - [ ]  Development board
    - [ ]  Peripherals, ICs, Utilities etc.
- [ ]  Basic numerical and text interface
    - [ ]  Decimal and Hex Integers
    - [ ]  Floating point
    - [ ]  UTF-8
- [ ]  configurable Clock/Baud rate settings
    - [ ]  External Clock
    - [ ]  Configurable internal Clock with controls
- [ ]  Basic Serial data intake
    - [ ]  SPI
    - [ ]  I2C
    - [ ]  UART
- [ ]  Parallel data intake
- [ ]  Analog data intake
- [ ]  Storage, history and navigation
- [ ]  PCB prototype

See Stage 1 Journal for Specifics

## Stage 2

- [ ]  CAN integration
    - [ ]  FDCAN
    - [ ]  Classical CAN (2.0) compatibility
    - [ ]  BxCAN compatibility
    - [ ]  CANopen functionality
- [ ]  USB as device integration
- [ ]  Real-Time Graphing
    - [ ]  Graph engine
    - [ ]  Scaling/format controls
- [ ]  Polished UTF-8 Pager system
- [ ]  Final PCB
- [ ]  Final Polish
    - [ ]  UX/UI improvements pass
    - [ ]  Device Housing
    - [ ]  Battery and Charger
    - [ ]  User documentation
    - [ ]  Fancy Logo and Start-up screen?

See Stage 2 Journal for Specifics
