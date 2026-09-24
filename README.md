# ADC-UART
Analyse timer and UART operation by toggling an LED at one-second intervals using a timer interrupt and displaying “Hello World” through PuTTY using the UART API. Further, transmit the ADC register value and its corresponding voltage through UART. 

---

## Apparatus Required

| S. No. | Apparatus / Software | Specification |
|:---:|---|---|
| 1 | Microcontroller Development Board | **NXP S32K144 Development Board** |
| 2 | IDE | **S32 Design Studio** |
| 3 | Programming Language | **Embedded C** |
| 4 | SDK | **S32K144 SDK** |
| 5 | LED | On-board LED / External LED |
| 6 | Programmer / Debugger | On-board Debugger / OpenSDA |
| 7 | USB Cable | For programming and power supply |

---
## Procedure
1. Connect the S32K144 Development Board to the computer using a USB cable.
2. Open S32 Design Studio.
3. Create a new project for the S32K144 microcontroller.
4. Select and configure the appropriate S32K144 SDK for the project.
5. Identify the GPIO pin connected to the LED on the S32K144 development board.
6. Configure the selected GPIO pin/Drivers as a Digital Output/input.
7. Initialize the required GPIO peripheral using the GPIO initialization functions provided by the S32K144 SDK.
8. Write the Embedded C program to control the LED using the GPIO Toggle-Pin API.
9. Insert a one-second delay between successive GPIO toggle operations.
10. The program should continuously execute the following sequence.
11. Build the project in S32 Design Studio.
12. Verify that the project is compiled successfully without errors.
13. Connect the debugger/programmer to the S32K144 Development Board.
14. Download the generated program to the S32K144 microcontroller.
15. Run the program on the S32K144 board.

---
## Program
```
#include "sdk_project_config.h"
#include<stdio.h>
int main(void){
	CLOCK_DRV_Init(&clockMan1_InitConfig0);
	PINS_DRV_Init(NUM_OF_CONFIGURED_PINS0, g_pin_mux_InitConfigArr0);
	static char txBuff[64];
	LPUART_DRV_Init(INST_LPUART_1, &lpUartState0, &lpuart_0_InitConfig0);
	uint8_t len=(uint8_t)sprintf(txBuff, "Hello World");
	LPUART_DRV_SendData(INST_LPUART_1, (const uint8_t *)txBuff, (uint8_t)len);
}

```
## OUTPUT
<img width="1915" height="1198" alt="image" src="https://github.com/user-attachments/assets/2a5b43d5-17a4-4132-a25b-6b033bb1bc19" />


---
## Result

The **Timer and UART operation** was successfully analyzed and implemented. The LED was toggled at **one-second intervals using a timer interrupt**, and the message **"Hello World"** was successfully displayed on **PuTTY** through the UART API. The **ADC register value and its corresponding voltage** were also transmitted and displayed through UART, confirming the successful operation of the timer, ADC, and UART peripherals.
