# Lab 1: Software Configuration

2.12/2.120 Intro to Robotics  
Spring 2024[^1]

## Table of Contents
- [0 Pre-Lab: Set Up Environment](#0-pre-lab-set-up-environment)
  - [0.1 Visual Studio Code](#01-visual-studio-code)
  - [0.2 Python](#02-python)
  - [0.3 Git](#03-git)
  - [0.4 PlatformIO](#04-platformio)
- [1 Set Up Hardware](#1-set-up-hardware)
  - [1.1 Validate Microcontroller](#11-validate-microcontroller)
  - [1.2 Validate Encoder](#12-validate-encoder)
  - [1.3 Validate Motor](#13-validate-motor)

## 0 Pre-Lab: Set Up Environment
Please install the following software to ensure a smooth experience during our lab sessions. If you have already installed any of the following software, you can feel free to skip the corresponding section.

If you run into any bugs or encounter issues during the installation process, don't waste too much time trying to debug the problem. Setting up a development environment for the first time can often be frustrating. Feel free to bring any issues to your lab section, and we will help you resolve them.

### 0.1 Visual Studio Code (VSCode)

Visual Studio Code is a popular and lightweight code editor that provides a user-friendly interface for coding. We will be using Visual Studio Code extensively throughout this class to program and communicate with the hardware.

You can download it here: https://code.visualstudio.com/Download. 

<details>
<summary><i> FAQs </i></summary>

- **What version of VSCode do I need?**  
Any version should work. If you are installing for the first time, please use the latest stable build.  
- **Can I use a different code editor?**  
We prefer VSCode since we will use the [PlatformIO plug-in](#04-platformio).
</details>

### 0.2 Python

Python is a versatile and widely-used programming language. We will use Python for writing and executing code in this class.

You can download it here: https://www.python.org/downloads/. Make sure to check the box that says "Add Python X.X to PATH" during installation.

<details>
<summary><i> FAQs </i></summary>

- **What version of Python do I need?**  
We recommend at least 3.8 to ensure compatibility with the packages we will use in this class. If you already have Python, you should be able to check its version by entering the command `python --version` in your terminal. 

- **How do I check that I installed Python correctly?**  
Entering the command `python` in your terminal should return `Python X.X ...`. If it instead returns `python is not recognized as an internal or external command, operable program, or batch file` or `python: command not found`, you may have forgotten to check the box that says "Add Python X.X to PATH" during installation. You can fix this using the following instructions: [How to Add Python to PATH](https://realpython.com/add-python-to-path/).

- **I already have Miniconda/Anaconda Python. Do I need to get vanilla Python?**  
We recommend getting vanilla Python. The staff may not be able to help troubleshoot issues relating to `conda`.
</details>


### 0.3 Git

Git is a distributed version control system that allows for efficient collaboration and tracking changes in code. We will use Git to manage our code repositories.

You can download it here: https://git-scm.com/downloads.

In order to clone a GitHub repository using the terminal through SSH, you also need to set up an SSH key:
1. Generate a new SSH key using the following instructions: [Generating a new SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key).
2. Add the SSH key to the ssh-agent using the following instructions: [Adding your SSH key to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#adding-your-ssh-key-to-the-ssh-agent).
3. Add the SSH key to the GitHub account using the following instructions: [Adding a new SSH key to your GitHub account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account). Stop once you reach the section "Generating a new SSH key for a hardware security key."

<details>
<summary><i> FAQs </i></summary>

- **What version of Git do I need?**  
Any version should work. If you are installing for the first time, please use the latest stable build.

- **How do I use Git?**  
If you aren't very familiar with Git, don't worry! We will teach the basics throughout the semester. If you are feeling particularly passionate about learning Git, we recommend reading the first few chapters of [Pro Git](https://git-scm.com/book/en/v2).
</details>

### 0.4 PlatformIO

PlatformIO is an open-source ecosystem for IoT development with support for various microcontroller platforms. The PlatformIO extension in VSCode provides a seamless environment for embedded systems programming.

1. Open the VSCode application.
2. Go to the Extensions view by clicking on the Extensions icon in the Activity Bar on the side of the window and search for "PlatformIO IDE" in the search bar.
3. Find the PlatformIO IDE extension in the search results and click the "Install" button.

## 1 Set Up Hardware

For today's lab, you'll need the following parts:
- Motor setup (which we have already assembled for you)
- ESP32-S3 microcontroller (https://esp32s3.com/)
- Breadboard
- USB-C cable

### 1.1 Validate Microcontroller
1. Clone this git repo by running the following command in your terminal: 
```
git clone git@github.com:mit212/lab1_2024.git
```
2. Switch the robot environment:
   1. Click on the `Default(lab1_2024)` button at the bottom of the screen:  
  ![](./.images/robot_env1.png)  
   2. Click on the `env:robot` that appears in the dropdown at the top of the screen. This will change the settings to compile anything in the src/robot folder:  
  ![](./.images/robot_env2.png)  
3. Rearrange the files within `src/` directory such that `blink_test.cpp` is in `src/robot/` and all the other `.cpp` files are in `src/test_code/`:  
  ![](./.images/blink_test.png)  
4. Put the microcontroller into download mode by holding `[BOOT]`, clicking `[RESET]` and then releasing `[BOOT]`. Depending on your operating system, you may have to do you this every time you want to upload code to your microcontroller.
5. Upload code to the microcontroller:  
  ![](./.images/upload.png)  
1. Run your code by pressing `[RESET]`.

### 1.2 Validate Encoder
1. Plug the microcontroller into the breadboard.
2. Open `include/pinout.h` and connect the wires from the motor to the corresponding pins on the microcontroller.
3. Ensure that the motor driver is powered off. Do this by unplugging the power cable at the emergency stop.
4. Connect the microcontroller to your computer using a USB-C cable.
5. Rearrange the files within the `src/` directory such that `encoder_test.cpp` is in `src/robot/` and all other `.cpp` files are in `src/test_code/`.
6. Put the microcontroller into download mode, upload the code, and reset the microcontroller.
7. Open the Serial Monitor:
  ![](./.images/serial_monitor.png)  
8. Rotate the wheel. You should observe that counter clock-wise motion increases each encoder's count, while clockwise motion decreases them.

### 1.3 Validate Motor
1. Rearrange the files within the `src/` directory such that `motor_drive_test.cpp` is in `src/robot/` and all other `.cpp` files are in `src/test_code/`.
2. Put the microcontroller into download mode, upload the code, and reset the microcontroller.
3. Proper function will result in the wheel moving back and forth a varying speeds.

| :white_check_mark: CHECKOFF 1 :white_check_mark:   |
|:---------------------------------------------------|
| Demonstrate `motor_drive_test.cpp` to an TA or LA. |

[^1]: Version 1 - 2024: Josh Sohn and Jinger Chong
