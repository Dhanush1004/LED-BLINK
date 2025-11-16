# Experiment 01 – Interfacing a Digital Output (LED) with ARM Development Board

### **Aim**
To interface a digital output (LED) to an ARM development board and write a blink code.

---

### **Components Required**
- STM32CubeIDE  
- NUCLEO ARM Development Board  

---

### **Theory**

**ARM (Advanced RISC Machine)** is a 32-bit processor architecture developed by ARM Holdings. It is widely used in embedded systems and SoC (System-on-Chip) products. Many semiconductor companies like Samsung, Atmel, and Texas Instruments license ARM architecture to design their own SoCs.
###  **What is an ARM7 Processor?**
The **ARM7 processor** is commonly used in embedded system applications. It provides a balance between the classic ARM architecture and the newer Cortex series, offering an excellent platform for both hardware and software development.
###  **LPC2148 Microcontroller**
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

###  **Procedure**

1. Open **STM32CubeIDE**.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e1a37b0a-9391-4a88-9014-9211bc67bb6e" />


2. Click **File → New STM32 Project**.
   ![WhatsApp Image 2025-10-25 at 15 32 18_b5b0d503](https://github.com/user-attachments/assets/2a16804f-409a-4256-92a2-dc0dd1169f2c)
   ![WhatsApp Image 2025-10-25 at 15 59 54_577f33ad](https://github.com/user-attachments/assets/05d7ce2a-d2e7-4cc8-8ee3-f4fe80e5fed3)
   
3.Select the target microcontroller or board and click Next.
<img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/8643abe9-0f4b-4e5f-bba1-ab539eb290c8" />

4. Name the project.
![mpmc1](https://github.com/user-attachments/assets/d322215a-811f-4212-87ea-4c282a16ec2f)


5. Select the **target microcontroller** or board and click **Next**.
   <img width="1110" height="624" alt="image" src="https://github.com/user-attachments/assets/f93d88b6-cd7f-49db-84de-351f9b116488" />



6. The corresponding `.ioc` file will be generated automatically.
![WhatsApp Image 2025-11-16 at 20 09 48_169f80ef](https://github.com/user-attachments/assets/b2e39174-a514-4bf3-b365-9d4fd5a9db53)


7. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
![mpmc6](https://github.com/user-attachments/assets/f5eeed98-d96a-444a-83ef-60f05883011a)


8. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
![mpmc3](https://github.com/user-attachments/assets/70c1a8cd-3984-463e-98d2-6414d44d5e0e)


 
9. Edit the generated main program as required.
![mpmc4](https://github.com/user-attachments/assets/a32ab459-c2e9-4b56-af9c-701695ad2b33)


10. Click **Project → Build All**.
![mpmc5](https://github.com/user-attachments/assets/a21e66f7-f01a-42b3-9ae3-58d56037a9e4)


11. Link the **HEX file** using the post-build process.
![mpmc5](https://github.com/user-attachments/assets/772f3acd-bdc2-452c-a0fb-8761bac37f41)



12. Click **Debug** and connect the **STM Nucleo Board**.
![WhatsApp Image 2025-10-27 at 19 48 08_68cb60ed](https://github.com/user-attachments/assets/84dfd6a8-c7b6-4780-aa02-a3bae895814b)


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
