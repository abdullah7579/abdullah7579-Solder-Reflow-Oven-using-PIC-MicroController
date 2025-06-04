Solder Reflow Oven using PIC18F458
This project presents the design and implementation of a cost-effective solder reflow oven system based on the PIC18F458 microcontroller and the MAX6675 thermocouple sensor. It uses a software-implemented SPI interface for temperature sensing and dynamically controls heating and cooling via a single PWM output. The control logic follows a standard temperature-time reflow profile and switches between heating and cooling using logic gates and IRF540N MOSFETs.

Temperature data is transmitted via UART and visualized in real-time using a Python script. The project demonstrates core embedded system principles, including interrupt-driven control, actuator management, and UART-based monitoring, making it ideal for educational or prototyping applications.
