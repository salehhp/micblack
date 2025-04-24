# micblack
Rainstick: Rapid Development  of an Environmental Sensor Node ver_1_0
Project Name: Rapid Development of an Environmental Sensor Node
Company: Raintstick
Author: Saleh
Date: 24/4/2025
Version: 1.0

////Project Overview:
This project involved the design and development of a configurable environmental sensor node based on
the ESP32 microcontroller. The sensor node measures ambient light, temperature, and humidity, publishing
the data as JSON over Wi-Fi at hourly intervals. The goal was to create a functional prototype that 
integrates hardware design, firmware development, version control, and AI-assisted workflows, all within
a constrained timeline of three working hours.

////Firmware Overview:
The firmware was developed in Arduino C++ and is structured modularly to enhance readability and maintainability. 
To begin the development of the environmental sensor node, the following steps were taken to set up the required software environment in the Arduino IDE:

1. Installing the ESP32 Board Support
First, we installed the ESP32 board support by Espressif Systems. This allows us to program the ESP32 microcontroller effectively. The specific steps include:

Open the Arduino IDE.
Navigate to File > Preferences.
In the  Additional Board Manager URLs  field, add the following URL: https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json.
Click OK to close the Preferences window.
Open the Boards Manager by navigating to Tools > Board > Boards Manager.
Search for  ESP32 by Espressif Systems  and select version 3.2.0.
Click on the Install button to download and install the selected version.
2. Installing the Required Libraries
Next, we installed the necessary libraries to support the functionality of the DHT11 temperature and humidity sensor and the BH1750 light sensor. The libraries used are:

DHT Sensor Library by Adafruit (version 1.4.6):

Open the Library Manager by navigating to Sketch > Include Library > Manage Libraries.
In the Library Manager, search for "DHT sensor library by Adafruit".
Locate version 1.4.6 and click on the Install button.
BH1750 Library by Christofer Laws (version 1.3.0):

While still in the Library Manager, search for "BH1750 by Christofer Laws".
Find version 1.3.0 and click on the Install button.
