# Keypad-Interfacing

##  AIM:
To interface the matrix keypad and display the keypad value in seven segment display using Arduino UNO controller.

## Software required:
Arduino IDE </br>
Proteous

## PROCEDURE:
### Arduino IDE
Step1:Open the Arduino IDE </br>
Step2: Go to file and select new file option </br>
Step3:Type the program </br>
Step4:Go to file and select save option to save the program </br>
Step5:Go to sketch and select verify or compile options </br>
Step6:If no error Hex file will be generated in the temporary folder </br>
### Proteus
Step7:Open the Proteus software </br>
Step8:Go to file select new design and click ok button </br>
Step9:Select component mode and click pick devices from the library </br>
Step10:Type the component name in the keyword to select the components and click ok button </br>
Step11:Design the circuit as per the diagram </br>
Step12:Double click the Arduino controller and upload the hex file generated by Arduino IDE </br>
Step13:Click start button and check the output

## THEORY:
The buttons on a keypad are arranged in rows and columns. A 3X4 keypad has 4 rows and 3 columns, and a 4X4 keypad has 4 rows and 4 columns:

Arduino Keypad Tutorial - 3X4 and 4X4 Keypads
Beneath each key is a membrane switch. Each switch in a row is connected to the other switches in the row by a conductive trace underneath the pad. Each switch in a column is connected the same way – one side of the switch is connected to all of the other switches in that column by a conductive trace. Each row and column is brought out to a single pin, for a total of 8 pins on a 4X4 keypad:

How to Set Up a Keypad on an Arduino - Back Side of Keypad
Pressing a button closes the switch between a column and a row trace, allowing current to flow between a column pin and a row pin.

The schematic for a 4X4 keypad shows how the rows and columns are connected:

Arduino Keypad Tutorial - 4X4 Keypad Schematic
The Arduino detects which button is pressed by detecting the row and column pin that’s connected to the button.

This happens in four steps:

1. First, when no buttons are pressed, all of the column pins are held HIGH, and all of the row pins are held LOW:

Arduino Keypad Tutorial - How the Keypad Works STEP 1
2. When a button is pressed, the column pin is pulled LOW since the current from the HIGH column flows to the LOW row pin:

Arduino Keypad Tutorial - How the Keypad Works STEP 2
3. The Arduino now knows which column the button is in, so now it just needs to find the row the button is in. It does this by switching each one of the row pins HIGH, and at the same time reading all of the column pins to detect which column pin returns to HIGH:

Arduino Keypad Tutorial - How the Keypad Works STEP 3
4. When the column pin goes HIGH again, the Arduino has found the row pin that is connected to the button:

Arduino Keypad Tutorial - How the Keypad Works STEP 4
From the diagram above, you can see that the combination of row 2 and column 2 could only mean that the number 5 button was pressed.

CONNECT THE KEYPAD TO THE ARDUINO
The pin layout for most membrane keypads will look like this:

Arduino Keypad Tutorial - 4X4 and 3X4 Keypad Pin Diagram
Follow the diagrams below to connect the keypad to an Arduino Uno, depending on whether you have a 3X4 or 4X4 keypad:

Arduino Keypad Tutorial - 4X4 and 3X4 Keypad Connection Diagram
HOW TO FIND THE PINOUT OF YOUR KEYPAD
If your keypad’s pin layout doesn’t match the ones above, you can probe the pins to figure it out. You’ll need to build a test circuit by connecting an LED and a current limiting resistor to the Arduino (or any 5V power source) like this:

Arduino Keypad Tutorial - Finding the Pinout
First, find out which keypad pins are connected to the button rows. Insert the ground (black) wire into the first pin on the left. Press any button in row 1 and hold it down. Now insert the positive (red) wire into each one of the other pins. If the LED lights up at one of the pins, press and hold another button in row 1, then insert the positive wire into each one of the other pins again. If the LED lights up on a different pin, it means the ground wire is inserted into the row 1 pin. If none of the buttons in row 1 make the LED light up, the ground wire is not connected to row 1. Now move the ground wire over to the next pin, press a button in a different row, and repeat the process above until you’ve found the pin for each row.

To figure out which pins the columns are connected to, insert the ground wire into the pin you know is row 1. Now press and hold any one of the buttons in that row. Now insert the positive wire into each one of the remaining pins. The pin that makes the LED light up is the pin that’s connected to that button’s column. Now press down another button in the same row, and insert the positive wire into each one of the other pins. Repeat this process for each one of the other columns until you have each one mapped out.

## PROGRAM:
#include<Keypad.h>

const byte ROWS =4;//four rows
const byte COLS =4;//four columns
</br>
char keys[ROWS][COLS]={</br>
   {'7','8','9','A'},</br>
   {'4','5','6','B'},</br>
   {'1','2','3','C'},</br>
   {'*','0','#','D'}</br>
};

byte rowPins[ROWS] ={2,3,4,5};//connect to the row pinouts of the keypad</br>
byte colPins[COLS] ={6,7,8,9};//connect to the column pinouts of the keypad</br></br>


Keypad keypad = Keypad( makeKeymap(keys), rowPins, colPins, ROWS , COLS);</br>

void setup() {</br></br>
   Serial.begin(9600);</br>
}</br>

void loop() {</br>
  char key = keypad.getKey();</br>

  if(key){</br>
    Serial.println(key);</br>
  }</br>
}</br>
## CIRCUIT DIAGRAM:
![keyboard interface in](https://github.com/Jeganvjk/Keypad-Interfacing/assets/132189820/3589fef6-4b01-4b76-ace1-6e3a66c48c9b)

##OUTPUT:

![keypad out](https://github.com/Jeganvjk/Keypad-Interfacing/assets/132189820/4fae3f0b-f36a-4f02-bad9-91d5d8fa105e)


## RESULT:
Thus the matrix keypad and seven segment display was interfaced with Arduino UNO controller to display the keypad value in seven segment display
