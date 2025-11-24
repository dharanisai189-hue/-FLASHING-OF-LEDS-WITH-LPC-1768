# FLASHING-OF-LEDS-WITH-LPC-1768

# AIM: 
   To interface and toggle the led with ARM LPC 1768 microprocessor           
           
# COMPONENTS REQUIRED:
##  HARDWARE:
ARM LPC1768
LED
## SOFTWARE:
KEIL MICRO VISION 4.0 IDE

# PROCEDURE:


⮚	Open the Keil software and select the New uvision project from Project Menu as shown below.
⮚	Browse to your project folder and provide the project name and click on save.
⮚	Once the project is saved a new pop up “Select Device for Target” opens, Select the controller (NXP: LPC1768) from NXP (founded by philips) and click on OK.
⮚	Select the controller (NXP: LPC1768) and click on OK.
⮚	As LPC1768 needs the startup code, click on Yes option to include the LPC17xx Startup file.
⮚	Create a new file by file → new to write the program.
⮚	Type the code.
⮚	After typing the code save the file as main.c eg. (abc.c).
⮚	Right click target and Add the suitable files to source group1 and header for the project.
⮚	Add the main.c along with system_LPC17xx.c.
⮚	Build the project and fix the compiler errors/warnings if any.
⮚	Code is compiled with no errors. The .bin file is still not generated.
⮚	Right Click on Target Options to select the option for generating .bin file.
⮚	Set IROM1 start address as 0x2000. Bootloader will be stored from 0x0000- 0x2000 so application should start from 0x2000
⮚	Write	the	command	to	generate	the .bin file	from
.axf file
Command: fromelf --bin projectname.axf --output filename.bin
⮚	in c/c++ → include paths → desktop (00-libfiles).
⮚	.Bin file is generated after a rebuild.
⮚	Check the project folder for the generated .Bin file.

# ADD FILES:
Target1:
Source group1:
Startuplpc17xx.s, main.c (t), delay.c (t), systemlpc17xx.c (t), gpio.c (t)
Header:
Delay.h, stdutils.h, gpioi.h

# PIN DIAGRAM :
<img width="486" height="336" alt="image" src="https://github.com/user-attachments/assets/a2fe4b7a-df4c-4f92-9d9c-1bc05dd0059a" />

 

# CIRCUIT DIAGRAM:
<img width="797" height="429" alt="image" src="https://github.com/user-attachments/assets/3c89a1bc-7a6c-4782-920c-0cc1c46d77f8" />

 
 
# PROGRAM:
```#include <lpc17xx.h> 
#include "delay.h" //User defined library which conatins the delay routines 
#include "gpio.h" 
#define LED P1_29 // Led is connected to P1.29 
/* start the main program */ 
int main() 
{ 
 SystemInit(); //Clock and PLL configuration 
 GPIO_PinFunction(LED,PINSEL_FUNC_0); // Configure Pin for Gpio 
 GPIO_PinDirection(LED,OUTPUT); // Configure the pin as OUTPUT 
 GPIO_PinWrite(LED,LOW); 
 while(1) 
 { 
   /* Turn On all the leds and wait for 100ms */ 
   GPIO_PinWrite(LED,HIGH); // Make all the Port pin as high 
   DELAY_ms(100); 
 
   GPIO_PinWrite(LED,LOW); // Make all the Port pin as low 
   DELAY_ms(100); 
  } 
}```


 
# Output:
<img width="706" height="527" alt="514700725-45866f99-5741-40c4-a526-fd1b11e9a41f" src="https://github.com/user-attachments/assets/7a6733b5-17f1-4213-8fb8-741315d6d419" />

