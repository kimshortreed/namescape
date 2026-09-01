---
layout: page
title: Tech tips
subtitle: Some tech approaches to making interactive maps
---


This page looks at some of the technology choices we made while making the _Untitled ṮEṮÁĆES_ map. 

## Sound tech: Flyrontech’s FN-M2A vs. Arduino

<figure style="text-align:center;">
  <img src="{{ 'assets/img/tech-01.png' | relative_url }}" alt="Flyrontech’s FN-M2A PIR Motion Sensor Activated Audio Player (left), and the Arduino Uno R3 microcontroller board (right)">
  <figcaption>Flyrontech’s FN-M2A PIR Motion Sensor Activated Audio Player \[L\], and the Arduino Uno R3 microcontroller board \[R\]</figcaption>
</figure>

The first haptic-map prototype, the _Untitled ṮEṮÁĆES_ map is, in part, a language-learning installation, so it requires clear audio of spoken place names in SENĆOŦEN and English. Moving the map’s various islands activates passive infrared (PIR) sensors embedded in them. When the PIR sensors detect motion, MP3 audio files play through a speaker hidden in the body of the islands. This set-up all seems simple enough until you have multiple people playing with multiple islands at once.

It is unrealistic, and little comic, to force people to use the map one at a time, or ask them to move only one island at a time. It should be possible for multiple people to interact with the map simultaneously. This goal comes with specific technology requirements. I chose an off-the-shelf solution for the _Untitled ṮEṮÁĆES_ map: Flyrontech’s FN-M2A PIR Motion Sensor, instead of using other possible technological solutions, like Arduino or Raspberry Pi, and here are some reasons why.

#### Why not Arduino?

<figure style="text-align:center;">
  <img src="{{ 'assets/img/tech-02.png' | relative_url }}" alt="Arduino Uno R3 microcontroller board">
  <figcaption>Arduino Uno R3 microcontroller board.</figcaption>
</figure>

Arduino defines itself, on its [introduction page](https://www.arduino.cc/en/Guide/Introduction), as “an open-source electronics platform based on easy-to-use hardware and software.” While this description is fair in that mastering Arduino is easier than learning to code or building a device from scratch, it does take significant reading, practice, and financial investments that could deter folks like me, who want to make something as technologically basic as the _Untitled ṮEṮÁĆES_ map.

I like Arduino; and their website’s content is well written and easy enough to follow, and their community is very helpful and friendly. I might use Arduino for future projects, but a helpful workshop at [UVic’s Digital Scholarship Commons](https://onlineacademiccommunity.uvic.ca/dsc/workshops/introduction-to-electronics-with-arduino/) reiterated for me that Arduino works more like a switch than a computer. The Arduino introduction page writes that Arduino is able “to read inputs,” such as “light on a sensor, a finger on a button, or a Twitter message,” and turn these inputs into outputs like “activating a motor, turning on an LED, publishing something online,” but it is not ideal for multiple, simultaneous, input events through one board—the _Untitled ṮEṮÁĆES_ map, for example, would require that multiple motion-sensors triggering multiple audio events to play simultaneously through an external speaker. Arduino might be able to play these one after the other, but not simultaneously, so I had to find other solutions.

For the “[makers](https://en.wikipedia.org/wiki/Maker_culture#Computers)” reading this, I can hear you screaming “what about [Raspberry Pi](https://www.raspberrypi.com/)?” This is a valid question because Raspberry Pi is, essentially, [a fully functional, programmable computer](https://www.raspberrypi.org/help/what-%20is-a-raspberry-pi/). With that in mind, a guiding principle of any haptic map is that others should be able to imitate its functionality without having to know how to code, so I consider Raspberry Pi a little too costly in terms of time and money, at least for our first prototype.

Instead of Arduino or Raspberry Pi, I chose Flyrontech’s FN-M2A PIR Motion Sensor because it plugs into a USB port of any computer, regardless of operating system—e.g., Windows, Apple, or Linux—and you transfer audio files to it as you would for any other external drive, like a [USB flash drive](https://en.wikipedia.org/wiki/USB_flash_drive), or data stick/key.

#### Introducing Flyrontech’s FN-M2A Motion-Sensor Activated Audio Player

<figure style="text-align:center;">
  <img src="{{ 'assets/img/tech-03.png' | relative_url }}" alt="Flyrontech’s FN-M2A PIR Motion Sensor Activated Audio Player">
  <figcaption>Margaret Pearce and the <a href="https://www.flyrontech.com/en/download/m2a.html">Flyrontech’s FN-M2A PIR Motion Sensor Activated Audio Player</a>.</figcaption>
</figure>

As a collection of parts, the FN-M2A is about as close as I could get to something I would custom-build for the _Untitled ṮEṮÁĆES_ map. It has a motion-sensor, a processing board, and a 3W speaker. You can load files onto the FN-M2A by connecting it to any computer with the [micro-USB port](https://en.wikipedia.org/wiki/USB_hardware), or you can load files onto a [micro-SD card](https://simple.wikipedia.org/wiki/MicroSD) and insert it into the micro-SD slot.

<figure style="text-align:center;">
  <img src="{{ 'assets/img/tech-04.png' | relative_url }}" alt="An image from the FN-M2A manual">
  <figcaption>An image from the FN-M2A manual.</figcaption>
</figure>

The FN-M2A has 4MB of onboard storage, which is not much. For the _Untitled ṮEṮÁĆES_ map’s demands, however, 4MB of storage is enough. If you need more than the onboard storage for your project, then you could load your files onto a micro-SD card and insert it into the micro-SD slot. The FN-M2A is programmed such that even if you have loaded files onto the onboard storage, the SD card will override them once inserted. I store only two, short audio clips on each of the six FN-M2A units—that is, one in SENĆOŦEN and one in English, so the 4MB storage is plenty.

The audio files you load onto the FN-M2A, either using onboard storage or with an SD card, will play in either numeric or alphabetical sort order, depending on how you name your files. For example, a file named “ardvark-sings.mp3” will play before a file named “baboon-opera.mp3.” So, if you wanted one file to play one before the other, you would have to change their names. For example, I would rename “baboon-opera.mp3.” to “01-baboon-opera.mp3” and change “ardvark-sings.mp3” to “02-ardvark-sings.mp3” to swap their playing order.

If you load more than one file onto FN-M2A, either onboard or micro-SD storage, it is programmed to play one file after the other, following each sensor activation. If you loaded two files, for example, then motioning once will play the first file and motioning again will play the next file, and so on with each additional file.

#### FN-M2A power options

<figure style="text-align:center;">
  <img src="{{ 'assets/img/tech-05.png' | relative_url }}" alt="An example of the 3.7 volt battery case">
  <figcaption>An example of the <a href="https://www.aliexpress.com/item/32580480645.html">3.7V battery case</a> used to power the FN-M2A unit.</figcaption>
</figure>

The FN-M2A has two power options. The first option is to power it through the onboard micro-USB port, using a phone-charger cable and adapter plugged into a household wall outlet (15 Amp, AC). Make sure that your power adapter provides 5V and 1A of power. I used an old phone charger and cable and it worked perfectly. The second option is to power the FN-M2A with batteries, but this option requires some soldering and the purchase of a battery case and appropriate batteries—see the [FN-M2A’s manual](https://www.flyrontech.com/en/download/m2a.html) for appropriate voltage ranges. TEMOSEṈ and I wanted the _Untitled ṮEṮÁĆES_ map to be able to work without having to be near a wall-plug power outlet, so I soldered on [3.7V AA-battery cases](https://www.aliexpress.com/item/32580480645.html) to each FN-M2A unit.

So far, we are happy with the FN-M2A’s performance and ease of use. Each unit costs around $20 CDN on the [AliExpress website](https://www.aliexpress.com/item/4000357949120.html?spm=a2g0s.9042311.0.0.4af24c4dzR3TLQ).
