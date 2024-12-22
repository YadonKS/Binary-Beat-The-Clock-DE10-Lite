# Binary-Beat-The-Clock-DE10-Lite
Designed to be implemented on the Intel DE10 Lite FPGA Board, this game is  beat the clock simulator, but the questions are numbers and the answers are the numbers in their binary versions!

# Overview
This project is an FPGA based program that is designed to work as a digital two player game called the Beat the Clock Binary using both combinational and sequential logic. The game has a time-limit and players take turns guessing randomly generated 5-bit binary numbers. The project contains several modules in Verilog, the primary code and features. The 5-bit binary values are generated using a **random number generator**, and edge detection logic is added to make sure that the button presses are reactive for reset and pause functions. The player timers are represented by two 5-bit counters and are decremented in real-time with a **1 Hz clock** that is extracted by a **clock divider**. The game checks which timers are active, updates random numbers, and resets values as required, providing seamless gameplay. The game also employs multiple 7-segment displays to display the timers and generates random numbers after each correct guess.
 
# Requireements

## Hardware
**Intel MAX DE-10 Lite FPGA Board**: The physical (hardware) inputs (10 switches and a button) and outputs (6 seven-segment-displays) of the game are all on this board. It can be purchased from multiple places like here for example.
![image](https://github.com/user-attachments/assets/dc030d5e-4bfc-4428-99ae-86ea2d07b3c7)
credit: Mouser Electronics: mouser.ca

**FPGA Board to PC connector**: It should come with the FPGA board. This is how it looks just incase:
![image](https://github.com/user-attachments/assets/3d74443c-6a9b-442f-8394-fe36eabc7aee)

## Software

**Quartus**: I used Quartus Prime 23.1 std. You can find the appropriate version for your device here: https://www.intel.com/content/www/us/en/collections/products/fpga/software/downloads.html

Note: If you are a Mac user with an Intel processor, you will have to run Quartus on a virtual machine isntead. Here is how you can do it using the free virtual machine VirtualBox: https://siytek.com/quartus-mac-virtualbox-ubuntu/#google_vignette

# How to Launch

1. Once you have installed Quartus, open it and Select the New Project Wizard.
2. Name the project: "BeatTheClockBinary" and choose the directory that you want to keep the project in.
3. Download all the verilog files (extension .v) and the pin assignment file (extension .qsf) as well as all other files from this repository (except README.md) and add them to the directory chosen in the previous step.
4. Select Empty Project then click Next.
5. Add all the files that were saved in your chosen directory to the project then click Next.
6. Select "Board" at the top of the page and from the "Family" drop down, choose MAX 10. Select MAX 10 DE10-Lite from "Available Boards"
7. Click Next, then click "Finish".
8. Click the dropdown at the top left corner and sleect Files if it is not already on files. You will see a file named "DE10_Lite_Golden_Top.v". Since this file is not needed, right click on it and select “Remove file from project”.
9. Right click on the file named BeatTheClockBinary.v and set it to be the "top-level entity" (this means that only that file has direct access to the board).
10. On the bottom left side, you will see the "Task" window. Double click on the blue triangle next to "Compile Design". The files will be compiled.
11. At the bottom of the "Tasks" window (scroll down if you have to), right click on “Program Device (Open Programmer)” then select "Open".
12. Plug your board into a USB port on your computer.
13. Click "Hardware Setup..." in the Programmer window.
14. Under the "Hardware Settings" tab, you should see a list of "available hardware items" (e.g., "USB-Blaster").
15. In the "Currently selected hardware" dropdown, select "USB-Blaster".
16. Close the Hardware Setup window to complete the setup.
17. You should now see a single line representing your output file, along with checkboxes for "Program/Configure", "Verify", etc.
18. Right-click on this line and select "Change file".
19. Navigate to the "output_files" directory and select "Lab1.sof".
20. Ensure the "Program/Configure" checkbox is checked.
21. Click "Start" to begin the programming process and start the game by clicking one of the two buttons on the board after it has been programmed. You can restart rounds by clicking on the button again without having to re-program the board.
