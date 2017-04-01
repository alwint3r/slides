<template lang='pug'>
#MyFirstSlideshow
  .eg-slideshow
    slide(enter='fadeIn')
      h2.center-title Arduino Day 2017

    slide(leave='fadeOut')
      h2.center-title Arduino Day 2017
      h4.center Programming Arduino 101 with Arduino Shields

    slide(enter='fadeIn' leave='fadeOut')
      h4.center-title First of all, Happy birthday Arduino!

    slide(enter='fadeIn')
      h3 Agenda
      ul.agenda-list
        li Talk about programming Arduino in general
        li Demo: Accessing Adafruit TFT Screen shield for Arduino

    slide(enter='fadeIn' leave='fadeOut')
      h3.center Oh, Hi...

      h4(style='margin-top:150px').center Alwin Arrasyid
      h5(style='margin-top:-30px').center Software Engineer, DycodeX

    slide(enter='fadeIn' leave='fadeOut')
      h3 Programming Arduino
      p.
        Programming Arduino is easy. Really.
      p.
        Even easier if you have programming experience, especially with C/C++.
      p.
        Arduino IDE is way to go (though not the only way!)

    slide(enter='fadeIn' leave='fadeOut')
      h4 Did you say Arduino IDE?
      p Yes, Arduino is NOT only about boards.
      p Arduino is an open-source electronics platform based on easy-to-use hardware and software.
      h4 Did you say it's not the only way?
      p Yes, you can use another IDE like platformio.

    slide(enter='fadeIn' leave='fadeOut')
      h3 Arduino Boards
      div.img-wrapper
        img(src='https://www.elprocus.com/wp-content/uploads/2016/09/Types-Of-Arduino-Boards.png')

    slide(enter='fadeIn' leave='fadeOut')
      h3 Arduino UNO
      p.center What we have here
      div.img-wrapper
        img(src='https://www.arduino.cc/en/uploads/Products/Uno_SMD_F.jpg')

    slide(enter='fadeIn' leave='fadeOut')
      h3 Arduino IDE
      p Text editor, toolchain, serial monitor, libraries and boards manager in one place.
      p Has simple and neat UI, so it's easy for any of us to start using it.

    slide(enter='fadeIn' leave='fadeOut')
      h3 Arduino Framework
      p The language is derived from Wiring.
      p Wiring offers high-level abstraction.
      p Reading from / writing to connected components is as easy as typing:
      pre.code.
        digitalWrite(8, HIGH);

        digitalRead(8);

        analogRead(A0);

    slide(enter='fadeIn' leave='fadeOut')
      h3 Arduino Framework
      p You only need to write your "main" code inside these two functions
      pre.code.
        void setup() {
          // your code here
        }

        void loop() {
          // your code here
        }

    slide(enter='fadeIn' leave='fadeOut')
      h3 Arduino Framework
      p Is also available for non-arduino boards!
      p You can also use Arduino Framework with another IDE like platformio!

    slide(enter='fadeIn' leave='fadeOut')
      h3 How to get started?
      p Confused on how to write code for Arduino or still wondering about the code structure? Take a look at the examples!

      p It's accessible from the File > Examples menu on your Arduino IDE.
      p Also, there are a lot of learning resources on the internet, all you have to do is acively search for it.

    slide(enter='fadeIn' leave='fadeOut')
      h3 Let's try blinking
      p.
        Source can be easily found at the Examples > 01.Basics under the name of Blink.

      p.
        I'll include it on this slide anyway. So, here it is:

      pre.code(style='font-size:16pt').
        void setup() {
          pinMode(LED_BUILTIN, OUTPUT);
        }

        void loop() {
          digitalWrite(LED_BUILTIN, HIGH);
          delay(1000);
          digitalWrite(LED_BUILTIN, LOW);
          delay(1000);
        }
    slide(enter='fadeIn' leave='fadeOut')
      h4.center Using Third Party Hardware
      p Most of Arduino boards compatible hardware companies provides library and manual for its usage.
      p The library can be installed in 3 ways:
      ul.agenda-list
        li Using Arduino IDE library manager
        li Importing a-zipped file from Arduino IDE
        li Manually copy the library source to the Arduino sketch directory

    slide(enter='fadeIn' leave='fadeOut')
      h4.center Adafruit 2.8" TFT Touch Shield

      div.img-wrapper
        img(src='https://cdn-learn.adafruit.com/assets/assets/000/013/421/medium800/adafruit_products_1651bottom_LRG.jpg?1388700106')

    slide(enter='fadeIn' leave='fadeOut')
      h4.center Adafruit 2.8" TFT Touch Shield
      p No wiring, no soldering, just connect the headers. It just sorta.... works.

    slide(enter='fadeIn' leave='fadeOut')
      h3 TFT Screen Pins
      p These pins is for Arduino Boards (UNO, Leonardo/Mega).
      ul.agenda-list
        li Digital #13 -> ICSP SCLK
        li Digital #12 -> ICSP MISO
        li Digital #11 -> ICSP MOSI
        li Digital #10 -> TFT CS
        li Digital #9 -> TFT DC

    slide(enter='fadeIn' leave='fadeOut')
      h3 TFT Resistive Touch Pins
      p These pins is for Arduino Boards (UNO, Leonardo/Mega).
      ul.agenda-list
        li Digital #13 -> ICSP SCLK
        li Digital #12 -> ICSP MISO
        li Digital #11 -> ICSP MOSI
        li Digital #8 -> SMTPE610 CS

    slide(enter='fadeIn' leave='fadeOut')
      h3 Before We Code...
      p We need to install these libraries:
      ul.agenda-list
        li
          a(href='https://github.com/adafruit/Adafruit_ILI9341/archive/master.zip').
            Adafruit ILI9341 Library
        li
          a(href='https://github.com/adafruit/Adafruit-GFX-Library/archive/master.zip').
            Adafruit GFX Library
      p We just need to simply import them from our Arduino IDE.

    slide(enter='fadeIn' leave='fadeOut')
      h3 Coordinate System
      div.img-wrapper
        img(src='https://cdn-learn.adafruit.com/assets/assets/000/001/264/medium800/lcds___displays_coordsys.png?1396770439')

    slide(enter='fadeIn' leave='fadeOut')
      h3 Colors
      p Each color is represented by a 16 unsigned bit integers.
      div.img-wrapper
        img(src='https://cdn-learn.adafruit.com/assets/assets/000/001/265/medium800/lcds___displays_colorpack.png?1396770449')

    slide(enter='fadeIn' leave='fadeOut')
      h3 Colors
      pre.code.
        #define BLACK    0x0000
        #define BLUE     0x001F
        #define RED      0xF800
        #define GREEN    0x07E0
        #define CYAN     0x07FF
        #define MAGENTA  0xF81F
        #define YELLOW   0xFFE0
        #define WHITE    0xFFFF

    slide(enter='fadeIn' leave='fadeOut')
      h4 Drawing Pixel and Lines

      pre.code(style='font-size:12pt').
        void drawPixel(uint16_t x, uint16_t y, uint16_t colors);

        void drawLine(
          uint16_t x0,
          uint16_t y0,
          uint16_t x1,
          uint16_t y1
          uint16_t color
        );

        void drawFastVLine(
          uint16_t x0,
          uint16_t y0,
          uint16_t length,
          uint16_t color
        );

        void drawFastHLine(
          uint8_t x0,
          uint8_t y0,
          uint8_t length,
          uint16_t color
        );

    slide(enter='fadeIn' leave='fadeOut')
      h4 Drawing Rectangles

      pre.code(style='font-size:12pt').
        void drawRect(
          uint16_t x0,
          uint16_t y0,
          uint16_t w,
          uint16_t h,
          uint16_t color
        );

        void fillRect(
          uint16_t x0,
          uint16_t y0,
          uint16_t w,
          uint16_t h,
          uint16_t color
        );

    slide(enter='fadeIn' leave='fadeOut')
      h4 Drawing Circles

      pre.code(style='font-size:12pt').
        void drawCircle(
          uint16_t x0,
          uint16_t y0,
          uint16_t r,
          uint16_t color
        );

        void fillCircle(
          uint16_t x0,
          uint16_t y0,
          uint16_t r,
          uint16_t color
        );

    slide(enter='fadeIn' leave='fadeOut')
      h4 Drawing Rounded Rectangles

      pre.code(style='font-size:12pt').
        void drawRoundRect(
          uint16_t x0,
          uint16_t y0,
          uint16_t w,
          uint16_t h,
          uint16_t radius,
          uint16_t color
        );

        void fillRoundRect(
          uint16_t x0,
          uint16_t y0,
          uint16_t w,
          uint16_t h,
          uint16_t radius,
          uint16_t color
        );

    slide(enter='fadeIn' leave='fadeOut')
      h4 Drawing Triangles

      pre.code(style='font-size:12pt').
        void drawTriangle(
          uint16_t x0,
          uint16_t y0,
          uint16_t x1,
          uint16_t y1,
          uint16_t x2,
          uint16_t y2,
          uint16_t color
        );

        void fillTriangle(
          uint16_t x0,
          uint16_t y0,
          uint16_t x1,
          uint16_t y1,
          uint16_t x2,
          uint16_t y2,
          uint16_t color
        );

    slide(enter='fadeIn' leave='fadeOut')
      h4 Drawing Characters

      pre.code(style='font-size:12pt').
        void drawChar(
          uint16_t x,
          uint16_t y,
          char c,
          uint16_t color,
          uint16_t bg,
          uint8_t size
        );

    slide(enter='fadeIn' leave='fadeOut')
      h4 Drawing Text

      pre.code(style='font-size:12pt').
        void drawChar(
          uint16_t x,
          uint16_t y,
          char c,
          uint16_t color,
          uint16_t bg,
          uint8_t size
        );

    slide(enter='fadeIn' leave='fadeOut')
      h3.center-title Enough talking, let's code!

    slide(enter='fadeIn' leave='fadeOut')
      h3.center-title Thank You!

    slide(enter='fadeIn' leave='fadeOut')
      p.center-title Cool and hackable slideshow by Eagle.js

    slide(enter='fadeIn' leave='fadeOut')
      p.center-title Awesome shield and learning resource from Adafruit

    slide(enter='fadeIn' leave='fadeOut')
      h3 Find Me
      ul.contact-list.center
        li Github (github.com/alwint3r)
        li Twitter (@alwin_wint3r)
        li Mail (alwin.ridd@gmail.com)

    slide(enter='fadeIn' leave='fadeOut')
      p.center-title Today's code
      a(href='https://github.com/alwint3r/ArduinoDay2017Bdg_Code' style='text-align:center; margin-left: 40px') github.com/alwint3r/ArduinoDay2017Bdg_Code



</template>

<script>
import eagle from 'eagle.js'
export default {
  mixins: [ eagle.slideshow ],
  infos: {
    title: 'Arduino Day 2017 - Programming Arduino Boards 101 with Shields',
    description: 'Programming Arduino boards using Arduino IDE with shields',
    path: 'arduino-2017'
  }
}
</script>

<style lang='scss'>
@import url(https://fonts.googleapis.com/css?family=Raleway);
#MyFirstSlideshow{
  .eg-slideshow{
    font-family: 'Raleway';
    background-color: #fff;
    .eg-slide{
      .eg-slide-content{
        width: 25em;
        max-width: 80%;
        margin: 0 auto;
      }
    }
  }
  .eg-slide-content{
    width: 25em;
    max-width: 80%;
    margin: 0 auto;
  }
  .center-title {
    margin-top:40%;
    text-align: center;
  }
  .center {
    text-align: center;
  }
  .img-wrapper {
    text-align: center;
    margin-top: 20px;
  }
  .agenda-list li {
    padding-top: 10px;
  }

  .contact-list li {
    padding-top: 10px;
    list-style: none;
  }
}
</style>
