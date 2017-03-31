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
        li Demo: Accessing environmental sensors from Alora Kit shield.

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
        Arduino IDE is way to go (though not the only one!)

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
      h3 Programming Arduino

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

  .first-slide {
    background-image: url('assets/front.png');
  }
}
</style>
