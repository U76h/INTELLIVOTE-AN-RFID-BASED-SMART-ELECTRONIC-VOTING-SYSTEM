# INTELLIVOTE-AN-RFID-BASED-SMART-ELECTRONIC-VOTING-SYSTEM

🧑‍💻 Project Overview:

This project presents a secure and efficient RFID-based voting system developed using embedded systems. The main objective of this system is to ensure that only authorized voters can cast their vote within a defined time period, while maintaining data integrity and security.

The system integrates multiple hardware modules such as RFID reader, RTC, EEPROM, LCD, and keypad to create a real-time voting environment. It also includes a separate control mechanism for the election officer to manage voting operations like start, stop, result viewing, and system reset.


 
🛠️ Hardware Requirements:

The following components are used in this project:
- Microcontroller (LPC2148)
- RFID Reader Module
- RFID Tags (for voters and officer)
- LCD Display (20x4)
- Matrix Keypad (4x4)
- I2C EEPROM (AT24C256)
- RTC Module (Real Time Clock)
- LEDs (Red & Green)
- Buzzer (Optional)
- Power Supply Unit

  

⚙️ Working Principle :

🔹 System Initialization
When the system is powered ON:
- All peripherals (LCD, Keypad, UART, EEPROM, I2C, RTC) are initialized
- Project title is displayed on LCD
- The system reads the current date and time from the RTC to ensure that the clock is functioning properly,as shown in the image below
  
![IMG_0020](https://github.com/user-attachments/assets/8bae88e4-bb1f-4cd0-9ea3-6fc5a4517e41)
![IMG_9926 (1)](https://github.com/user-attachments/assets/09a82baa-6bd9-4ae3-b5c2-5c8207fa811c)



🔹 Idle State
 - The system remains idle, continuously waiting for a voter’s RFID card and displays ‘Waiting for Card…’ on the LCD.
 <img width="1500" height="1125" alt="image" src="https://github.com/user-attachments/assets/b61fcec8-d66a-4178-9a51-095ce1e54763" />




 
