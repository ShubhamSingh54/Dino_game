Dino Game Bot - Automated Dino Runner Using Python
This project automates the famous offline Google Chrome Dino game using Python. With the help of PyAutoGUI for keyboard automation and Pillow for image processing, the bot detects obstacles (cacti and birds) and simulates appropriate keystrokes to jump or duck.
Overview
When the game detects a cactus or a bird on the screen, the bot performs these actions:

Presses the "UP" key to make the dinosaur jump over the cactus.
Presses the "DOWN" key to make the dinosaur duck under the bird.
This program uses image recognition by taking continuous screenshots of the game screen and analyzing pixel intensity values.
Setup and Installation
Python Environment
Make sure you have Python installed. You can download it from the official Python website.

Install Required Packages
Open your terminal/command prompt and run the following commands:
pip install pyautogui
pip install pillow

Clone the Repository
Clone this project to your local machine using:
git clone <repository-url>
cd <project-folder>

How It Works
The program captures screenshots of the game and processes the image in grayscale mode.

Cactus Detection: If a cactus is detected within a specific pixel range, the bot presses the "UP" key to make the Dino jump.
Bird Detection: If a bird is detected within the pixel range, it presses the "DOWN" key to make the Dino duck.
Code Explanation
Import Necessary Modules
Code Explanation
Import Necessary Modules
Simulate Keystrokes
def hit(key):
    pyautogui.keyDown(key)  # Press the specified key

Detect Obstacles
def isCollide(data):
    # Check for birds in a specific pixel range
    for i in range(300, 415):
        for j in range(410, 563):
            if data[i, j] < 100:  # If obstacle detected, duck
                hit("down")
                return

    # Check for cacti in a specific pixel range
    for i in range(300, 415):
        for j in range(563, 650):
            if data[i, j] < 100:  # If cactus detected, jump
                hit("up")
                return
Main Execution
if __name__ == "__main__":
    print("Hey.. Dino game about to start in 3 seconds")
    time.sleep(2)  # Wait for the user to switch to the game window

    while True:
        # Capture the screen in grayscale
        image = ImageGrab.grab().convert('L')
        data = image.load()

        # Check for obstacles and take action
        isCollide(data)
How to Use
Start the Chrome Dino Game
Disconnect the internet or open chrome://dino in your browser to access the offline Dino game.

Run the Script
Switch to your terminal/command prompt and run:
python dino_bot.py

Switch to the Dino Game Window
You have 3 seconds to switch to the game window after running the script. The bot will start playing automatically.
Notes
This bot assumes that the game screen stays in the same location. If you change the position of the game window, you may need to adjust the pixel ranges in the code.
The bot may not work perfectly on every screen resolution. If needed, adjust the pixel ranges for bird and cactus detection.
Disclaimer
This project is for practice purposes only. Using automated bots can be against the terms of service for some games or services.

📚 Resources
PyAutoGUI Documentation: https://pyautogui.readthedocs.io
Pillow Documentation: https://pillow.readthedocs.io
