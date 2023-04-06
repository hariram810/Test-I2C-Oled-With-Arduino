# Test-I2C-Oled-With-Arduino

![Screenshot (1122)](https://user-images.githubusercontent.com/118633170/230158632-143f9891-22f1-41e3-bbd0-c4544e9c0f89.png)


If you have hard-time 3d printing stuff and other materials which i have provided in this project please refer the professionals for the help, [JLCPCB](https://jlcpcb.com/RNA) is one of the best company from shenzhen china they provide, PCB manufacturing, PCBA and 3D printing services to people in need, they provide good quality products in all sectors

[JLCPCB](https://jlcpcb.com/RNA)


Please use the following link to register an account in [JLCPCB](https://jlcpcb.com/RNA)

https://jlcpcb.com/RNA


Pcb Manufacturing

----------

2 layers

4 layers

6 layers

jlcpcb.com/RNA



PCBA Services

[JLCPCB](https://jlcpcb.com/RNA) have 350k+ Components In-stock. You don’t have to worry about parts sourcing, this helps you to save time and hassle, also keeps your costs down.

Moreover, you can pre-order parts and hold the inventory at [JLCPCB](https://jlcpcb.com/RNA), giving you peace-of-mind that you won't run into any last minute part shortages. jlcpcb.com/RNA



3d printing

-------------------

SLA -- MJF --SLM -- FDM -- & SLS. easy order and fast shipping makes [JLCPCB](https://jlcpcb.com/RNA) better companion among other manufactures try out [JLCPCB](https://jlcpcb.com/RNA) 3D Printing servies

[JLCPCB](https://jlcpcb.com/RNA) 3D Printing starts at $1 &Get $54 Coupons for new users

![Screenshot (1123)](https://user-images.githubusercontent.com/118633170/230259502-42386108-8b07-41e3-add3-06e2b9d7acda.png)

he organic light-emitting diode (OLED) display that we’ll use in this tutorial is the SSD1306 model: a monocolor, 0.96-inch display with 128×64 pixels as shown in the following figure.

The OLED display doesn’t require backlight, which results in a very nice contrast in dark environments. Additionally, its pixels consume energy only when they are on, so the OLED display consumes less power when compared with other displays.

The model we’re using here has only four pins and communicates with the Arduino using I2C communication protocol. There are models that come with an extra RESET pin. There are also other OLED displays that communicate using SPI communication.

![Screenshot (1125)](https://user-images.githubusercontent.com/118633170/230259542-2eeb4770-e6a5-4c7f-9312-62592bfd56ad.png)
![Screenshot (1124)](https://user-images.githubusercontent.com/118633170/230259543-d82a53bc-ab47-4578-a039-325b5426aa48.png)

Pin wiring
Because the OLED display uses I2C communication protocol, wiring is very simple. You just need to connect to the Arduino Uno I2C pins as shown in the table below.

PinWiring to Arduino UnoVin5VGNDGNDSCLA5SDAA4

If you’re using a different Arduino board, make sure you check the correct I2C pins:

Nano: SDA (A4); SCL (A5);
MEGA: SDA (20); SCL (21);
Leonardo: SDA (20); SCL (21);


Libraries
To control the OLED display you need the adafruit_SSD1306.h and the adafruit_GFX.h libraries. Follow the next instructions to install those libraries.

1. Open your Arduino IDE and go to Sketch > Include Library > Manage Libraries. The Library Manager should open.

2. Type “SSD1306” in the search box and install the SSD1306 library from Adafruit.

3. After installing the SSD1306 library from Adafruit, type “GFX” in the search box and install the library.

4. After installing the libraries, restart your Arduino IDE.

Tips for writing text using these libraries
Here’s some functions that will help you handle the OLED display library to write text or draw simple graphics.

display.clearDisplay() – all pixels are off
display.drawPixel(x,y, color) – plot a pixel in the x,y coordinates
display.setTextSize(n) – set the font size, supports sizes from 1 to 8
display.setCursor(x,y) – set the coordinates to start writing text
display.print(“message”) – print the characters at location x,y
display.display() – call this method for the changes to make effect
Testing the OLED Display
After wiring the OLED display to the Arduino and installing all required libraries, you can use one example from the library to see if everything is working properly.

In your Arduino IDE, go to File > Examples > Adafruit SSD1306 and select the example for the display you’re using.

![Screenshot (1127)](https://user-images.githubusercontent.com/118633170/230259590-e40f61c7-b681-40c4-9f6e-4fa3a956956c.png)
![Screenshot (1126)](https://user-images.githubusercontent.com/118633170/230259601-673994f7-882c-4093-893d-607883a37de6.png)

If your OLED doesn’t have a RESET pin, you should set the OLED_RESET variable to -1 as shown below:

#define OLED_RESET -1 // Reset pin # (or -1 if sharing Arduino reset pin)

Upload the code to your Arduino board. Don’t forget to select the right board and COM port in the Tools menu.

If your OLED display is not showing anything:

Check that the OLED display is properly wired to the Arduino
Double-check the OLED display I2C address: with the OLED connected to the Arduino, upload this code and check the I2C address in the Serial Monitor
You should change the OLED address in the following line, if necessary. In our case, the address is 0x3C.

if(!display.begin(SSD1306_SWITCHCAPVCC, 0x3C)) { 
Write Text – OLED Display
The Adafruit library for the OLED display comes with several functions to write text. In this section, you’ll learn how to write and scroll text using the library functions.

“Hello, world!” OLED Display

![Screenshot (1130)](https://user-images.githubusercontent.com/118633170/230259646-8fe7ff65-d154-4186-9a6d-660313282a2e.png)
![Screenshot (1128)](https://user-images.githubusercontent.com/118633170/230259656-a2b617ac-dc2f-4c6c-bce6-05eb0ab4f01f.png)

Importing libraries
First, you need to import the necessary libraries. The Wire library to use I2C and the Adafruit libraries to write to the display: Adafruit_GFX and Adafruit_SSD1306.

#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>
Initialize the OLED display
Then, you define your OLED width and height. In this example, we’re using a 128×64 OLED display. If you’re using other sizes, you can change that in the SCREEN_WIDTH, and SCREEN_HEIGHT variables.

#define SCREEN_WIDTH 128 // OLED display width, in pixels
#define SCREEN_HEIGHT 64 // OLED display height, in pixels
Then, initialize a display object with the width and height defined earlier with I2C communication protocol (&Wire).

Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, -1);
The (-1) parameter means that your OLED display doesn’t have a RESET pin. If your OLED display does have a RESET pin, it should be connected to a GPIO. In that case, you should pass the GPIO number as a parameter.

![Screenshot (1134)](https://user-images.githubusercontent.com/118633170/230259677-dde194a6-e020-4d02-b947-86186186a61a.png)
![Screenshot (1132)](https://user-images.githubusercontent.com/118633170/230259683-22752817-c738-4765-a6f2-1728d801ac2b.png)
![Screenshot (1133)](https://user-images.githubusercontent.com/118633170/230259686-1ca4b4d5-d2f9-49ad-94a3-c2133d076540.png)

In the setup(), initialize the Serial Monitor at a baud raute of 115200 for debugging purposes.

Serial.begin(115200);
Initialize the OLED display with the begin() method as follows:

if(!display.begin(SSD1306_SWITCHCAPVCC, 0x3C)) { 
  Serial.println("SSD1306 allocation failed");
  for(;;); // Don't proceed, loop forever
}
This snippet also prints a message on the Serial Monitor, in case we’re not able to connect to the display.

Serial.println("SSD1306 allocation failed");
In case you’re using a different OLED display, you may need to change the OLED address. In our case, the address is 0x3C.

if(!display.begin(SSD1306_SWITCHCAPVCC, 0x3C)) { 

Define the position where the text starts using the setCursor(x,y) method. In this case, we’re setting the text to start at the (0,10) coordinates.

![Screenshot (1137)](https://user-images.githubusercontent.com/118633170/230259723-486e2799-9739-494e-946b-b2d7f6458631.png)
![Screenshot (1136)](https://user-images.githubusercontent.com/118633170/230259748-5834c702-4493-49d8-9770-8f237eee14bc.png)

display.setCursor(0,10);             
Finally, you can send the text to the display using the println() method, as follows:

display.println("Hello, world!");
Then, you need to call the display() method to actually display the text on the screen.

display.display();
Scrolling Text
The Adafruit OLED library provides useful methods to easily scroll text.

startscrollright(0x00, 0x0F): scroll text from left to right
startscrollleft(0x00, 0x0F): scroll text from right to left
startscrolldiagright(0x00, 0x07): scroll text from left bottom corner to right upper corner
startscrolldiagleft(0x00, 0x07): scroll text from right bottom corner to left upper corner

The Adafruit GFX library allows us to use some alternate fonts besides the built-in fonts. It allows you to chose between Serif, Sans, and Mono. Each font is available in bold, italic and in different sizes.

The sizes are set by the actual font. So, the setTextSize() method doesn’t work with these fonts. The fonts are available in 9, 12, 18 and 24 point sizes and also contain 7-bit characters (ASCII codes) (described as 7b in the font name).

The fonts that work better with the OLED display are the 9 and 12 points size.

To use one of those fonts, first you need to include it in your sketch, for example:

#include <Fonts/FreeSerif12pt7b.h>
Next, you just need to use the setFont() method and pass as argument, the specified font:

display.setFont(&FreeSerif12pt7b);
After specifying the font, all methods to write text will use that font. To get back to use the original font, you just need to call the setFont() method with no arguments:

display.setFont();

![Screenshot (1142)](https://user-images.githubusercontent.com/118633170/230259799-65bdda74-4769-4b86-a535-7bb2ebcb7d16.png)
![Screenshot (1138)](https://user-images.githubusercontent.com/118633170/230259815-18275fd5-d463-4a29-9f88-4b53ff77f3a1.png)


Note: if you’re using a module with a DHT sensor, it normally comes with only three pins. The pins should be labeled so that you know how to wire them. Additionally, many of these modules already come with an internal pull up resistor, so you don’t need to add one to the circuit.

Installing Libraries
Before proceeding, make sure you have installed the“adafruit_GFX.h” and the “adafruit_SSD1306.h” libraries to control the OLED display.

For this project you also need two aditional libraries to read from the DHT sensor: the DHT library and the Adafruit_Sensor library. Follow the next steps to install those libraries

1. Open your Arduino IDE and go to Sketch > Include Library > Manage Libraries. The Library Manager should open.

2. Search for “DHT” on the Search box and install the DHT library from Adafruit.

3. After installing the DHT library from Adafruit, type “Adafruit Unified Sensor” in the search box. Scroll all the way down to find the library and install it.

4. Restart your Arduino IDE.

In this tutorial, we’ll be using both I2C and SPI 0.96-inch 128×64 OLED displays. Don’t worry if your module is a different size or color;

An OLED display, unlike a character LCD display, does not require a backlight because it generates its own light. This explains the display’s high contrast, extremely wide viewing angle, and ability to display deep black levels. The absence of a backlight reduces power consumption significantly. The display uses about 20mA on average, though this varies depending on how much of the display is lit.

The SSD1306 controller operates at 1.65V to 3.3V, while the OLED panel requires a 7V to 15V supply voltage. All of these various power requirements are fulfilled by internal charge pump circuitry. This makes it possible to connect the display to an Arduino or any other 5V logic microcontroller without requiring a logic level converter.

OLED Memory Map
In order to control the display, it is crucial to understand the memory map of the OLED display.

Regardless of the size of the OLED display, the SSD1306 driver includes a 1KB Graphic Display Data RAM (GDDRAM) that stores the bit pattern to be displayed on the screen. This 1 KB memory area is divided into 8 pages (from 0 to 7). Each page has 128 columns/segments (block 0 to 127). And, each column can store 8 bits of data (from 0 to 7). That certainly proves that we have:

If your DHT sensor fails to get the readings or you get the message “Failed to read from DHT sensor”

If you get the “SSD1306 allocation failed” error or if the OLED is not displaying anything in the screen, it can be one of the following issues:

Wrong I2C address

The I2C address for the OLED display we are using is 0x3C. However, yours may be different. So, make sure you check your display I2C address using an I2C scanner sketch.

![Screenshot (1141)](https://user-images.githubusercontent.com/118633170/230259822-ce6da8ca-ac58-4300-965e-13f75058c5d9.png)

SDA and SCL not connected properly

Please make sure that you have the SDA and SCL pins of the OLED display wired correctly.

One thing they all have in common, however, is that at their core is a powerful single-chip CMOS OLED driver controller – SSD1306, which handles all RAM buffering, requiring very little work from your Arduino.
