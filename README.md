# LED-BLINK
# 💡 Experiment 01 – Interfacing a Digital Output (LED) with ARM Development Board

### 🎯 **Aim**
To interface a digital output (LED) to an ARM development board and write a blink code.

---

### ⚙️ **Components Required**
- STM32CubeIDE  
- NUCLEO ARM Development Board  

---

### 🧠 **Theory**

**ARM (Advanced RISC Machine)** is a 32-bit processor architecture developed by ARM Holdings. It is widely used in embedded systems and SoC (System-on-Chip) products. Many semiconductor companies like Samsung, Atmel, and Texas Instruments license ARM architecture to design their own SoCs.
### 🧩 **What is an ARM7 Processor?**
The **ARM7 processor** is commonly used in embedded system applications. It provides a balance between the classic ARM architecture and the newer Cortex series, offering an excellent platform for both hardware and software development.
### 🔍 **LPC2148 Microcontroller**
The **LPC2148**, developed by NXP Semiconductors (Philips), is a 16/32-bit ARM7-based microcontroller featuring a wide range of peripherals.
#### **Key Features**
- 16/32-bit ARM7TDMI-S core in LQFP64 package  
- On-chip **Flash memory**: 32 KB – 512 KB  
- On-chip **SRAM**: 8 KB – 40 KB  
- **ISP/IAP** via on-chip bootloader  
- **Embedded ICE-RT** and **Real Monitor** for real-time debugging  
- **USB 2.0** full-speed device controller with 2 KB endpoint RAM  
- **10-bit ADC** (6 or 14 channels, 2.44 μs conversion time)  
- **10-bit DAC** for analog output  
- **Timers:** Two 32-bit timers, watchdog, and PWM unit  
- **RTC** with 32 kHz clock input  
- **UARTs (2x), I²C (2x)** up to 400 kbit/s  
- **5V-tolerant GPIOs**, 21 external interrupt pins  
- **Max CPU Clock:** 60 MHz using on-chip PLL (lock time 100 µs)  
- **Crystal Frequency:** 1 MHz – 25 MHz  
- **Power modes:** Idle and Power-down with peripheral clock scaling  

---

### 🧭 **Procedure**

1. Open **STM32CubeIDE**.
<img width="1011" height="604" alt="Screenshot 2025-11-11 204057" src="https://github.com/user-attachments/assets/9e78349f-9504-4ee2-8f82-9908ad7e99a1" />


2. Click **File → New STM32 Project**.
  <img width="1028" height="605" alt="Screenshot 2025-11-11 204106" src="https://github.com/user-attachments/assets/95f9023f-c87d-4da6-9cfa-65f82d8ae22f" />

3. Select the **target microcontroller** or board and click **Next**.
   <img width="899" height="624" alt="Screenshot 2025-11-11 204113" src="https://github.com/user-attachments/assets/bcc13715-e11d-41e9-a22b-4f26b13f1903" />


4. Name the project.
 <img width="480" height="349" alt="Screenshot 2025-11-11 204124" src="https://github.com/user-attachments/assets/6231b37d-6242-4646-b5c0-487ebd18d64e" />

5. The corresponding `.ioc` file will be generated automatically.
  <img width="563" height="419" alt="Screenshot 2025-11-11 204141" src="https://github.com/user-attachments/assets/81ace282-33f7-415a-ba36-a16a15d063db" />


6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
  <img width="830" height="526" alt="Screenshot 2025-11-11 204158" src="https://github.com/user-attachments/assets/6d4753a3-c016-45fc-8696-0f86b9ab259c" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
  <img width="996" height="559" alt="Screenshot 2025-11-11 204213" src="https://github.com/user-attachments/assets/6a020288-c327-4eed-8c77-ab45b0e884aa" />

 
8. Edit the generated main program as required.
  <img width="579" height="436" alt="Screenshot 2025-10-29 233359" src="https://github.com/user-attachments/assets/f9ea1120-5b3c-454f-a299-f2423cc307e6" />
 <img width="1169" height="696" alt="Screenshot 2025-11-11 204455" src="https://github.com/user-attachments/assets/91b617a5-d759-464e-95b8-a01e2657cf06" />

9. Click **Project → Build All**.
    <img width="972" height="592" alt="Screenshot 2025-11-11 204514" src="https://github.com/user-attachments/assets/89362add-1c98-4b18-9169-ab403ccefdb7" />

10. Link the **HEX file** using the post-build process.
    <img width="676" height="449" alt="Screenshot 2025-11-11 204527" src="https://github.com/user-attachments/assets/0564e8a7-6e8a-47e8-b768-8aea4fa3f6b3" />

11. Click **Debug** and connect the **STM Nucleo Board**.
    <img width="860" height="581" alt="Screenshot 2025-11-11 204539" src="https://github.com/user-attachments/assets/11e9ce8f-d9fa-4008-a311-fc366d4572c5" />


13. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
        HAL_Delay(1000);
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
        HAL_Delay(1000);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 
<img width="1041" height="696" alt="Screenshot 2025-11-11 205336" src="https://github.com/user-attachments/assets/ff2ce9fb-b84c-4cf3-a7f2-2640c289dd7e" />


CASE 2: LED OFF

<img width="670" height="307" alt="Screenshot 2025-10-29 234651" src="https://github.com/user-attachments/assets/2a405699-98c2-4fac-bf68-a754245f195f" />

---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
