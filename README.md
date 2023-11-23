## Top
# Welcome to Seryalda Electronics - Your Partner in DIY Electronics and IoT Projects! 👋

- 👀 We are passionate about electronics, DIY projects, and IoT innovations.
- 🌱 Constantly learning and exploring new ideas to develop PCB boards for DIYers and electronic hobbyists.
- 🤝 We're open to collaboration on exciting projects and contributions from the community.

## Check Out Our RAIL DIN Boards:

🔌 **Relay Drivers:** 
  - AC Relay Driver Board ([DAWG](https://github.com/seryalda/dawg))
  - DC Relay Driver Board ([MARVIN](https://github.com/seryalda/marvin))

🌟 **MCU Mounting Boards:**
  - ESP8266 V2 NodeMCU (Amica)
  - ESP8266 V3 NodeMCU (Lolin) ([FOGHORN](https://github.com/seryalda/foghorn))
  - ESP32 (DevKit)
  - Arduino Uno R3 (Clone)

🔋 **Mini POWER Hub Boards:**
  - DC Supply Hub ([WILE](https://github.com/seryalda/wile))
  - AC Supply Hub ([SYLVESTER](https://github.com/seryalda/sylvester))

## Other Boards:

🔗 [Up](#top)

<!--

https://forum.arduino.cc/t/communication-between-arduino-and-esp8266-01/1145678/19
---------------------------------------------------------------------
very simple test program
ESP-01S reads characters from serial U0RXD (GPIO3) and echo back to U0TXD (GPIO1)
//  ESP-01 blink LED and read characters from serial U0RXD  and echo back to U0TXD

void setup() {
  Serial.begin(38400);
  delay(1000);
  Serial.println();
  Serial.println("\n\nESP-01 blinking LED and read characters from serial U0RXD  and echo back to U0TXD ");
  Serial.print("LED blinking pin ");
  Serial.println(LED_BUILTIN);
  // initialize digital pin LED_BUILTIN as an output.
  pinMode(LED_BUILTIN, OUTPUT);
}

void loop() {
  static long timer = millis();
  if (millis() - timer > 500) {
    timer = millis();
    digitalWrite(LED_BUILTIN, !digitalRead(LED_BUILTIN));
  }
  // read serial U0RXD and echo it back to U0TXD
  while (Serial.available() > 0) {
    char ch = Serial.read();
    Serial.write(ch);
  }
}



---------------------------------------------------------------------
this UNO program reads on pins 8and transmis on pin 9

// UNO - ESP-01 AltSoftSerial test - ESP-01 loopsback - character transmitted to it are echoed back
//  requires program ESP-01_Serial_loopback loaded in to ESP-01 and serial connections (see below)
//  note that at baudrates above 38400 some echoed characters are corrupted

#include <AltSoftSerial.h>

// load program ESP-01_Serial_loopback in to ESP-01
// ESP-01 U0TXD to UNO RX pin 8
// ESP-01 U0RXD to UNO TX pin 9
// ESP-01 GPIO0 and GPIO2 need to have pull-up resistors connected to ensure the module starts up correctly
// The ESP-01S has 12K resistors on the board for GPIO0, RST and CH_PD 

AltSoftSerial espSerial;

void setup() {
  Serial.begin(115200);
  Serial.println("AltSoftSerial test");
  //Begin serial communication with Arduino and SIM800L
  espSerial.begin(38400);
  Serial.println("ESP-01 serial intialized");
  Serial.println("load ESP-01_Serial_loopback in to ESP-01");
  Serial.println("ESP-01 U0TXD to UNO RX pin 8");
  Serial.println("ESP-01 U0RXD to UNO TX pin 9");
}

void loop() {
  if (Serial.available()) {
    char command = Serial.read();
    //Serial.println(command);
    espSerial.print(command);
  }
  while (espSerial.available()) {
    char reponse = espSerial.read();
    Serial.print(reponse);
  }
}

connect as diagram in post 4, e.g.

ESP-01 pin GPIO1 U0TXD to UNO pin 8 RX
ESP-01 pin GPIO3 U0RXD to UNO pin 9 TX
text entered on the UNO serial monitor to transmitted to the ESP-01 which echoes it back and displayed on the serial monitor

as @jremington stated in post 18 the UNO software serial does not work well at high baudrates
the above UNO code uses AltSoftSerial at 38400baud


https://www.hackster.io/ROBINTHOMAS/esp8266-esp-01-webserver-7248ca
https://www.instructables.com/Serial-Communication-Between-Arduino-and-ESP-01/


-->
