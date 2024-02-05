# Lab 1: Software Configuration

2.12/2.120 Intro to Robotics  
Spring 2024[^1]

## Table of Contents
- [Lab 1: Software Configuration](#lab-1-software-configuration)
  - [Table of Contents](#table-of-contents)
  - [0 Pre-Lab: Set Up Environment](#0-pre-lab-set-up-environment)
    - [0.1 Visual Studio Code](#01-visual-studio-code)
    - [0.2 PlatformIO](#02-platformio)
    - [0.3 Python](#03-python)
    - [0.4 GitHub Desktop](#04-github-desktop)
  - [1 Set Up Hardware](#1-set-up-hardware)
    - [1.1 Validate Microcontroller](#11-validate-microcontroller)
    - [1.2 Validate Motor](#12-validate-motor)
    - [1.3 Validate Encoder](#13-validate-encoder)
  - [X Optional](#x-optional)
    - [X.1 Git through VSCode Source Control](#x1-git-through-vscode-source-control)

## 0 Pre-Lab: Set Up Environment
Please install the following software.

If you run into any bugs or encounter issues during the installation process, feel free to contact the lab staff via Piazza! We can also resolve issues during the first lab, but having these installed in advance will make the lab experience run smoother.


### 0.1 Visual Studio Code (VSCode)


1. Download VSCode here: https://code.visualstudio.com/Download.

<details>
<summary><i> FAQs </i></summary>

- **What version of VSCode do I need?**  
Any version should work. If you are installing for the first time, please use the latest stable build.  
- **Can I use a different code editor?**  
We prefer VSCode since we will use the [PlatformIO plug-in](#02-platformio).
</details>


### 0.2 PlatformIO

PlatformIO is an open-source ecosystem for IoT development with support for various microcontroller platforms. The PlatformIO extension in VSCode provides a seamless environment for embedded systems programming. We will be using the Arduino ecosystem in PlatformIO, so if you are familiar with programming microcontrollers using the Arduino IDE, the code will look familiar.

1. Open the VSCode application.
2. Go to the Extensions view by clicking on the Extensions icon in the Activity Bar on the side of the window and search for "PlatformIO IDE" in the search bar.
3. Find the PlatformIO IDE extension in the search results and click "Install".
  
### 0.3 Python

1. Download Python here: https://www.python.org/downloads/.
2. Make sure to check "Add python.exe to PATH".
![](./.images/Python_install.png)
3. Click "Install Now" and finish the installation.

<details>
<summary><i> FAQs </i></summary>

- **What version of Python do I need?**  
We recommend at least 3.8 to ensure compatibility with the packages we will use in this class. If you already have Python, you should be able to check its version by entering the command `python --version` in your terminal. 

- **How do I check that I installed Python correctly?**  
Entering the command `python` in your terminal should return `Python X.X (tags...`. If it instead returns `python is not recognized as an internal or external command, operable program, or batch file` or `python: command not found`, you may have forgotten to add Python to PATH during installation. You can fix this using the following instructions: [How to Add Python to PATH](https://realpython.com/add-python-to-path/).

- **I already have Miniconda/Anaconda Python. Do I need to get vanilla Python?**  
We recommend getting vanilla Python. The staff may not be able to help troubleshoot issues relating to `conda`.
</details>

### 0.4 GitHub Desktop

GitHub Desktop provides a simplified user interface for Git, a distributed version control system that allows for efficient collaboration and tracking changes in code. We will use Git to manage our code repositories. 

1. Download GitHub Desktop here: https://desktop.github.com/.
2. Click "Sign in to GitHub Enterprise".
![](./.images/Github_Desktop.png)
3. Enter "https://github.mit.edu" and sign in using your MIT Kerberos credentials.
![](./.images/Github_Desktop_2.png)

## 1 Set Up Hardware

For today's lab, you'll need the following parts:
- Motor setup (which we have already assembled for you)
- ESP32-S3 microcontroller (https://esp32s3.com/)
- Breadboard
- USB-C cable

### 1.1 Validate Microcontroller
1. Clone (make a local copy) this GitHub repository.
    1. Open the GitHub Desktop application.
    2. Click "Clone a repository from the Internet..."
    ![](./.images/clone1.png)  
    3. Click the "URL" tab and enter "mit212/lab1_2024" under Repository URL. For Local path, click "Choose" to specify where you want the files to be saved on your local machine.
    ![](./.images/clone2.png)  
    4. Click "Clone".

2. Switch the robot environment:
   1. Click on the `Default(lab1_2024)` button at the bottom of the screen:  
  ![](./.images/robot_env1.png)  
   2. Click on the `env:robot` that appears in the dropdown at the top of the screen. This will change the settings to compile anything in the `src/robot` folder:  
  ![](./.images/robot_env2.png)  
3. Rearrange the files within `src/` directory such that `blink_test.cpp` is in `src/robot/` and all the other `.cpp` files are in `src/test_code/`:  
  ![](./.images/blink_test.png)  
4. Put the microcontroller into download mode by holding `[BOOT]`, clicking `[RESET]` and then releasing `[BOOT]`. Depending on your operating system, you may have to do you this every time you want to upload code to your microcontroller.
5. Upload code to the microcontroller:  
  ![](./.images/upload.png)  
6. Run your code by pressing `[RESET]`. You should see the onboard LED blink.

### 1.2 Validate Motor
1. Rearrange the files within the `src/` directory such that `motor_drive_test.cpp` is in `src/robot/` and all other `.cpp` files are in `src/test_code/`.
4. use the two buttons on the microcontroller

2. Put the microcontroller into download mode, upload the code, and reset the microcontroller.
3. Proper function will result in the wheel moving back and forth a varying speeds.
use code to make it spin


### 1.3 Validate Encoder
1. Plug the microcontroller into the breadboard.
2. Open `include/pinout.h` and connect the wires from the motor to the corresponding pins on the microcontroller.
3. Ensure that the motor driver is powered off. Do this by unplugging the power cable at the emergency stop.
4. Connect the microcontroller to your computer using a USB-C cable.
5. Rearrange the files within the `src/` directory such that `encoder_test.cpp` is in `src/robot/` and all other `.cpp` files are in `src/test_code/`.
6. Put the microcontroller into download mode, upload the code, and reset the microcontroller.
7. Open the Serial Monitor:
  ![](./.images/serial_monitor.png)  
8. Rotate the wheel. You should observe that counter clock-wise motion increases each encoder's count, while clockwise motion decreases them.


| :white_check_mark: CHECKOFF 1 :white_check_mark:   |
|:---------------------------------------------------|
| Demonstrate `motor_drive_test.cpp` to an TA or LA. |


## X Optional 

### X.1 Git through VSCode Source Control

An alternative to GitHub Desktop is VSCode's built-in Source Control. You can access it by clicking the Source Control icon in the Activity Bar on the left. 

![](./.images/vscode_source_control.png)

Since it relies on your local machine's installation of Git, you will need to install Git in addition to GitHub Desktop. You will also need to set up an SSH key in order to commit changes to GitHub repositories.

1. Download Git here: https://git-scm.com/downloads.
2. If you don't have one yet, create an account on [GitHub.com](https://github.com/join/).
3. Generate a new SSH key using the following instructions: [Generating a new SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key).
4. Add the SSH key to the ssh-agent using the following instructions: [Adding your SSH key to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#adding-your-ssh-key-to-the-ssh-agent).
5. Add the SSH key to your GitHub account using the following instructions: [Adding a new SSH key to your GitHub account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account). Stop once you reach the section "Generating a new SSH key for a hardware security key."

Unfortunately, VSCode Source Control has no native method for cloning GitHub repositories. However, you might find its interface more intuitive for other Git commands we will introduce in future labs!

[^1]: Version 1 - 2024: Joseph Ntaimo, Josh Sohn, Jinger Chong
