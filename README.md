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
<img width="1919" height="1077" alt="Screenshot 2025-10-29 115230" src="https://github.com/user-attachments/assets/61fab3d0-c750-452e-beaa-d381e4e631fa" />


2. Click **File → New STM32 Project**.
   ![WhatsApp Image 2025-10-25 at 15 32 18_b5b0d503](https://github.com/user-attachments/assets/2a16804f-409a-4256-92a2-dc0dd1169f2c)
   ![WhatsApp Image 2025-10-25 at 15 59 54_577f33ad](https://github.com/user-attachments/assets/05d7ce2a-d2e7-4cc8-8ee3-f4fe80e5fed3)
   
3.Select the target microcontroller or board and click Next.
<img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/8643abe9-0f4b-4e5f-bba1-ab539eb290c8" />

4. Name the project.
![WhatsApp Image 2025-10-29 at 10 23 40 AM](https://github.com/user-attachments/assets/76a8dd88-622d-41f2-8391-b2efd8bcbf9d)


5. Select the **target microcontroller** or board and click **Next**.
<img width="1919" height="1016" alt="image" src="https://github.com/user-attachments/assets/69d5bf1e-e5d5-4e73-ad35-9f37365160f7" />



6. The corresponding `.ioc` file will be generated automatically.
<img width="1919" height="1016" alt="image" src="https://github.com/user-attachments/assets/081a2994-c5fb-4071-b57f-f47156b21bfa" />


7. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/22c1fabd-eb3c-4c01-af01-7439a104ce17" />


8. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
<img width="1919" height="977" alt="Screenshot 2025-10-29 114406" src="https://github.com/user-attachments/assets/bb1edaf6-2d2c-40ed-9fc2-9aaf68d7e1c9" />


 
9. Edit the generated main program as required.
<img width="1919" height="1079" alt="Screenshot 2025-10-29 111830" src="https://github.com/user-attachments/assets/809ffcb6-a7e6-43ac-b5b7-a6957dc155ea" />


10. Click **Project → Build All**.
<img width="843" height="495" alt="Screenshot 2025-10-29 112807" src="https://github.com/user-attachments/assets/7018dbb9-8167-4429-8038-e4d1bd8c0b3a" />


11. Link the **HEX file** using the post-build process.
<img width="430" height="401" alt="Screenshot 2025-10-29 112055" src="https://github.com/user-attachments/assets/cd68615e-8d56-4e34-bcd3-c2bddcc40ddd" />



12. Click **Debug** and connect the **STM Nucleo Board**.
<img width="1429" height="981" alt="Screenshot 2025-10-29 112121" src="https://github.com/user-attachments/assets/d1613aeb-8d0e-4615-bd2a-5a6e09effc8b" />


13. Click **Run** to execute the program.
 
### 💻 **Program**
```
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
### OUTPUT
CASE 1: LED ON 
![WhatsApp Image 2025-10-27 at 20 12 54_b43d1f17](https://github.com/user-attachments/assets/e0c3f403-c6ee-44ff-a111-06814bfc53a2)


CASE 2: LED OFF
![WhatsApp Image 2025-10-27 at 20 12 54_15886613](https://github.com/user-attachments/assets/45947529-b89c-4d5a-ba28-9ec93989710d)



---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
