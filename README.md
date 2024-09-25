# Remote-Keylogger
Creating a remote keylogger in Python and disguising it in a phishing email.

Abstract. This project involves the development and deployment of a Python-based remote keylogger, designed to capture and transmit keystroke data from a target machine. The keylogger was implemented using Python libraries pynput for keyboard monitoring and smptlib for transferring of captured data via email. The script was compiled into an executable file for ease of distribution and stealth operation. The executable was embedded into a phishing email and sent to the victim, where it was activated upon execution. Once installed on the target machine, the keylogger ran in the background, recording keystrokes and periodically sending the captured data to a specified email address. The report details the keylogger's design, functionality, and the attack vector used to distribute the malware.

# Part I: Code

# Imports

tkinter: for creating a GUI popup on screen

pynput.keyboard: for capturing keystrokes

logging: for creating logs files

os: for interacting with the host OS (Windows)

getpass/uuid/socket: get host information

threading: executing processes in unique threads

subprocess: running system commands

![Screenshot 2024-09-24 211424](https://github.com/user-attachments/assets/e80b61fc-b053-440d-8793-a5277e8a5e93)

_Figure 1.1: Imports from python libraries_

# Setup

This section of code configures the SMTP email service, along with the temporary file to write all the logs to. The temporary file created is disguised to blend with Windows files as “license_win64_details.txt”. Using Gmail’s SMTP service, I will be able to send emails to remotely extract information.

![Screenshot 2024-09-24 211424 (1)](https://github.com/user-attachments/assets/01547902-9521-45d9-b61d-77b165ba6396)
_Figure 1.2: SMTP email service and temporary file to write logs to_

# Host Info & Wifi Profiles

These functions will run in the beginning of execution and will collect host information about the machine it's running on.

![Screenshot 2024-09-24 211452](https://github.com/user-attachments/assets/52185468-5fbe-4b53-bc2b-1be71a84c35e)
![Screenshot 2024-09-24 211508](https://github.com/user-attachments/assets/c99068cc-f84a-4b01-82dc-da5019c9a198)
_Figure 1.3: hostname, IP, username, saved wifi profiles, MAC address, and username_

# Main Functions & Loop

The program will begin listening for keystrokes and writing them to a temporary file that will automatically send the data incrementally when the file size reaches 500 bytes and on program termination. The program works by creating threads for listening and execution, infinitely logging all keystrokes, writing them to a file, and emailing the file. By default there is a safety key (right ctrl) which terminates the program. Pressing the safety key will stop the program and delete the temporary files.

![Screenshot 2024-09-24 211521](https://github.com/user-attachments/assets/803a582a-8183-4f01-a714-15c3ec7138cd)
![Screenshot 2024-09-24 211531](https://github.com/user-attachments/assets/4b3e3c3c-c432-4b40-848a-b8d5ca9c1927)

_Figure 1.4: Main functions and loop_

# Part II: Executable compile

The program was compiled into a standalone executable through the command line using Pyinstaller. Saving the python file as “.pyw” extension will run the program “without console”. The program will run without popping up command prompts or new windows to help stay undetected.

![Screenshot 2024-09-25 103308](https://github.com/user-attachments/assets/5d6b116f-e1ba-4ef1-ab53-c38b1c00e2c2)
_Figure 2.1: command to create executable_

![Screenshot 2024-09-25 095441](https://github.com/user-attachments/assets/3b99a693-6dc1-4818-ac3e-e4506b4fda8d)
_Figure 2.2: renaming .exe file to “ClaimRewardsHere” to avoid suspicion_

# Part III: Demo

After compiling the code and making it into an executable, I created a phishing email. The executable will be embedded in the phishing email. This email will be sent to the victim and once the executable is downloaded and run, a keylogger will be running in the background undetected.

![Screenshot 2024-09-18 134918](https://github.com/user-attachments/assets/b5d9ec18-2c45-4753-a9a7-df3631323ac5)
_Figure 3.1: Phishing email to disguise executable_

![Screenshot 2024-09-17 200155](https://github.com/user-attachments/assets/d3c3702f-b56a-43fc-8b5e-225de39daebd)
<img width="1188" alt="Screenshot 2024-09-25 at 12 18 54 PM" src="https://github.com/user-attachments/assets/06da254d-bef8-4730-a934-efd17a100481">
_Figure 3.2: Email received and opened by victim_

![Screenshot 2024-09-25 102118](https://github.com/user-attachments/assets/82ce534d-a936-40a4-820b-0eb1842a058d)
![Screenshot 2024-09-25 102135](https://github.com/user-attachments/assets/fb3de24f-5bdf-4917-bf26-02abffebe750)
_Figure 3.3: click “here” redirected to download page, executable ran_

Now the executable is installed and successfully running on the victim machine. The keylogger is running in the background, recording keystrokes and periodically sending the captured data to a specified email address.

<img width="1202" alt="Screenshot 2024-09-25 at 10 10 49 AM" src="https://github.com/user-attachments/assets/d678106c-b387-4101-b64f-ee1fc29f3d2d">
_Figure 3.4: host information_

![Screenshot 2024-09-25 100742](https://github.com/user-attachments/assets/b8e01c3c-8053-4caf-b348-bdb74f11fab8)
<img width="1206" alt="Screenshot 2024-09-25 at 10 11 22 AM" src="https://github.com/user-attachments/assets/5d62febd-926b-4cf4-baa7-6fc662b9ab3f">
_Figure 3.5: “how to make the perfect steak” was searched, keystrokes logged and sent it email_

![Screenshot 2024-09-25 100730](https://github.com/user-attachments/assets/49d59b7a-a58e-472b-a907-cde9aec6ea31)
<img width="1206" alt="Screenshot 2024-09-25 at 10 12 36 AM" src="https://github.com/user-attachments/assets/f54bef71-edd2-4a2c-ab8b-805a2f017278">
_Figure 3.6: “how many days until Halloween” was searched, keystrokes logged and sent it email_

![Screenshot 2024-09-25 113912 (1)](https://github.com/user-attachments/assets/cf8faa1a-130a-4221-b224-4a39b153bf8a)
_Figure 3.7: right ctrl key was pressed, programed successfully terminated_









