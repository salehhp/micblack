# micblack
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

////Main Code Section Description:
The main section of the code for the environmental sensor node encompasses several critical components, as outlined below:

1. Required Libraries and Variables
Lines 8 to 34 of the code include all the necessary libraries and variables needed for the project. These libraries facilitate communication with the sensors and Wi-Fi connectivity. Additionally, key variables are defined to store sensor readings and configuration settings.

2. Refresh Rate
A variable named refresh determines the duration (in seconds) for which the web page displaying sensor data will update. This ensures that users receive real-time information from the sensors.

3. Wi-Fi Connection Details
To connect the ESP32 board to the Wi-Fi network, the SSID (Wi-Fi name) and password must be correctly specified in:

Line 33: Input the Wi-Fi network name.
Line 34: Input the corresponding Wi-Fi password.
4. Sensor Data Display Function
The sendTemp function, coded from lines 39 to 89, is responsible for presenting the sensor readings on a web page when a user connects to the ESP32 board s IP address. Notably, the HTML code used to generate the web page is encapsulated within this function, allowing user-friendly access to real-time sensor data.

5. Setup Function
In the setup function, several critical initializations take place:

The I2C protocol is initialized to establish communication with the BH1750 sensor.
The DHT11 sensor library is invoked on line 123 to ensure proper communication with the ESP32 board.
On lines 126 and 127, the Wi-Fi module is activated to connect to the specified Wi-Fi network.
Line 140 outputs the ESP32 s Wi-Fi IP address to the serial monitor upon successful connection, allowing for easy access to the web page.
6. Used Wi-Fi IP Address
For this project, the Wi-Fi module is assigned the IP address 192.168.122.58. This address is used for accessing the web page that displays the sensor data.

7. Main Loop
Within the main loop of the program, line 156 is where the sensor data and HTML code are handled by the Wi-Fi module. In lines 157 to 159, the data from the sensors is read and stored in their respective variables.

Additionally, lines 170 to 181 implement serial monitoring functionality, allowing the sensor data to be displayed through the serial monitor when properly connected.

The PCB design for the environmental sensor node includes the following components:

ESP32 Dev Kit (38-pin module)
DHT11 Temperature and Humidity Sensor
BH1750 Light Sensor
Enclosure Design
The designed PCB will be housed in a waterproof enclosure that has one matte side and one transparent side, which can be purchased from the store Jaycar. Due to the need for waterproofing, the BH1750 sensor will be positioned towards the transparent plastic side of the enclosure.

Sensor Connections
The BH1750 sensor module features five pins, of which four are connected according to the schematic:

Ground (GND)
VCC
SDA (Serial Data Line)
SCL (Serial Clock Line)
These connections will be made on the PCB as specified in the design.

To power the board, a small cutout insulated with silicone adhesive will be created at the USB connector side of the ESP32 board to allow connection via a USB cable.

DHT11 Sensor Setup
The DHT11 sensor must be exposed to the ambient air to accurately measure temperature and humidity. Therefore, it will be connected with a connector and insulated wire, sealed with silicone adhesive, and routed outside the main enclosure. The DHT11 sensor will be housed in an insulated casing to ensure that only the sensor portion is accessible, while its electronic components are completely covered by the enclosure.

Connection Details
The BH1750 sensor is connected to the following pins on the ESP32:

Pin 19: Ground (GND)
Pin 20: Power (3.3V)
Pin 22: SDA
Pin 24: SCL
The DHT11 sensor is connected to:

Pin 19: Ground (GND)
Pin 20: Power (3.3V)
Pin 5: Digital pin on the ESP32

////Device Operation
When the device is powered on via the USB cable connected to the ESP32 board, the light, temperature, and humidity sensors are also activated.
Upon successful connection of the ESP32 Wi-Fi module to the Wi-Fi network, the temperature, humidity, and light (lux) values become accessible at the local IP address 192.168.122.58.
An example of the data display can be found in the project files.

////Suggestions for Project Improvement
To enhance the quality of this project, the following upgrades could be considered:

Upgrade Sensors:

Implement higher-quality temperature and humidity sensors, such as the AM2315C, which may provide more accurate and reliable readings.
Use a more advanced light intensity sensor to improve measurement accuracy and response time.
Data Hosting:

Expand the programming capabilities to make sensor data accessible over the internet by purchasing a web hosting service. This will allow users to monitor data remotely
rather than being confined to local access.
Threshold Alerts:

Establish specific threshold values for each measured parameter (temperature, humidity, and light levels). By doing so, the system could send email alerts
to users when these values exceed or fall below the defined thresholds.
This feature should be prioritized for implementation in future software versions.
By implementing these suggestions, the overall functionality and user experience of the environmental sensor node can be significantly improved, making it a more sophisticated and useful tool for monitoring environmental conditions.

