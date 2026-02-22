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
   <img width="1938" height="1065" alt="image" src="https://github.com/user-attachments/assets/b303b25c-71ea-47ac-b0b3-6747f088c78b" />

 
 🔹 Voting Time Validation 

- Whenever a voter card is detected by the RFID reader, the system first checks the database (EEPROM) to see if the voter ID exists.
- If the ID is valid, the system then performs the following checks:
- Voting time: Verifies the current time from the RTC to ensure it is within the allowed voting period.
- Voting authorization: Confirms that the officer has enabled the voting authority flag.
- If all checks are valid (voter ID exists, within allowed time, voting authority enabled):
  The voter is allowed to vote by entering their respective PIN on the keypad.
  Alternatively, the voter may choose to:
- Edit PIN
- Exit without voting
  <img width="2527" height="1168" alt="image" src="https://github.com/user-attachments/assets/869b65e2-9bfb-45e9-bba0-6510c87fd8a2" />


if any of the validation checks fail (invalid ID, outside allowed voting time, or voting not authorized), the system displays an appropriate message on the LCD based on the failure reason:
- Voter ID does not exist → “Voter ID not found in database”
- Voting has not started yet → “Voting has not started”
- Voting period has ended → “Voting time over”
- Voting not authorized by officer → “Voting not enabled by officer”

🔹 Voting Process

- Voter selects an option and enters the Pin (hidden using *).
- If the pin is correct:
- Party selection menu is displayed.
- <img width="2048" height="1168" alt="image" src="https://github.com/user-attachments/assets/8b481f69-28ae-485c-a159-6760c3e84de7" />

- After the voter casts the vote using the keypad, the system displays the message: ‘Vote Casted Successfully’, as shown in the figure.
  <img width="2044" height="1170" alt="image" src="https://github.com/user-attachments/assets/11809f94-3051-4b24-8cfe-bfceff65b073" />

- The selected party’s vote count is incremented and stored in EEPROM.
- Buzzer turns ON.
  
- If the password is incorrect:
- Red LED turns ON.
- Error message is displayed on the LCD.
   

  


 
