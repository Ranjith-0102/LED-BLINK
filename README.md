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
<img width="1918" height="1079" alt="image" src="https://github.com/user-attachments/assets/e280790f-559d-4d37-bebe-ba4772218d59" />

2. Click **File → New STM32 Project**.
 <img width="1919" height="1018" alt="image" src="https://github.com/user-attachments/assets/2f4dfcb0-2b37-459b-a674-6ff0a29f7a34" />
 
3. Select the **target microcontroller** or board and click **Next**.
   <img width="1110" height="624" alt="image" src="https://github.com/user-attachments/assets/f93d88b6-cd7f-49db-84de-351f9b116488" />



4. Name the project.
<img width="533" height="588" alt="image" src="https://github.com/user-attachments/assets/9b6e51e9-5ff9-4ae6-9581-a5e2b85f9629" />

5. The corresponding `.ioc` file will be generated automatically.
  <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/8900847c-6745-43e2-9ecf-2e66877fdc49" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
   <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/acc4f1c4-5e33-431b-8a76-3b102016baa6" />
<img width="1110" height="624" alt="image" src="https://github.com/user-attachments/assets/b7abcd80-797d-451f-a7c3-23f303822423" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/dbf4b205-5db9-4e9b-8150-94f441c8b116" />
 
8. Edit the generated main program as required.
  <img width="1919" height="1023" alt="image" src="https://github.com/user-attachments/assets/047f0f0e-6872-42eb-8f98-7c44832bb36f" />
<img width="1919" height="1012" alt="image" src="https://github.com/user-attachments/assets/181462f7-da73-43b1-bcc4-d9259ec00c66" />


9. Click **Project → Build All**.
    <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/264cd0a8-3e96-4668-822e-838ecfafc527" />

10. Link the **HEX file** using the post-build process.
    <img width="1053" height="465" alt="image" src="https://github.com/user-attachments/assets/478187a0-0ee6-4c50-9cac-c3b5ee18521b" />

11. Click **Debug** and connect the **STM Nucleo Board**.
<img width="1919" height="1015" alt="image" src="https://github.com/user-attachments/assets/75e503a9-cdf8-4c66-a083-f7e29c4ad440" />

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
<img width="1280" height="576" alt="image" src="https://github.com/user-attachments/assets/53dd2294-edd2-440e-9d4d-8d0adb27b794" />

CASE 2: LED OFF
<img width="1280" height="576" alt="image" src="https://github.com/user-attachments/assets/46ee2048-8570-46fa-9522-afa0797216c2" />

---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
