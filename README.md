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
- Buzzer turns ON for a short duration.
  
- If the password is incorrect:
- Red LED turns ON.
- Error message is displayed on the LCD.
- And again, the system will display 'Waiting for card' to record the next vote.
- this is how the system works.

🧑‍💼 𝐄𝐋𝐄𝐂𝐓𝐈𝐎𝐍 𝐎𝐅𝐅𝐈𝐂𝐄𝐑 𝐌𝐎𝐃𝐄

- A separate RFID card is assigned to the Election Officer.
- The Officer Mode is activated through an external interrupt.
- Whenever the interrupt is triggered, the system enters officer mode request.

Once activated:
- The LCD displays "Waiting for Officer Card".
  <img width="1943" height="1170" alt="image" src="https://github.com/user-attachments/assets/92c747c9-2964-4a7e-aa31-f1a672a08b62" />

- All voter cards are ignored during this process.
- When a valid officer card is detected:
- The system prompts the officer to enter the PIN for authentication.
  After successful verification:
- The Officer Menu is displayed on the LCD as follows,
<img width="1500" height="1125" alt="image" src="https://github.com/user-attachments/assets/a00b2f0f-320a-4df8-b398-f556708abaaf" />


  Due to the limited display capacity of the LCD module, the menu items are designed to be concise while maintaining clarity and functionality.
1. SET VOTING TIME
2. START VOTING
3. STOP VOTING
4. VIEW RESULT
5. RESET VOTING
6. RTC EDIT
7. EXIT

- SET VOTING TIME – Allows the officer to configure the start and end time of voting, which is stored in EEPROM for validation.

- START VOTING – Enables the voting process by setting the voting flag in EEPROM after successful password authentication.

- STOP VOTING – Disables the voting process by clearing the voting flag in EEPROM after verifying the officer password.

- VIEW RESULT – Displays the current vote count of all parties by reading stored data from EEPROM after password verification.

- RESET VOTING – Clears all vote counts and resets the voting status in EEPROM after successful officer authentication.

- RTC EDIT – Allows the officer to update the current date and time in the RTC module using the keypad.

- EXIT – Returns the system from officer menu back to the waiting-for-card state.

- These all above operations are performed using keypad...


  💻 SOFTWARE REQUIREMENTS

➤ Embedded C
➤ Keil IDE
➤ Proteus (Optional – for simulation)
➤ Flashing Tool (Programmer)

🚀 ADVANTAGES

✔ Secure Authentication using RFID
✔ Interrupt-Driven Officer Control
✔ Efficient and Fast Voting Process
✔ Reduced Human Interaction
✔ Compact and Optimized Embedded Design
✔ User-Friendly Interface

📌 APPLICATIONS

➤ College Elections
➤ Government Polling Systems
➤ Smart Polling Booths

  
 
 
  
   
   

  


 
