# Gameboy Printer Sniffer

Sniff packet Communications Between Real Gameboy And Real Gameboy Printer.
This repository contains test vectors in `./RealCapture/` to assist in
emulating a real Gameboy printer.

Written by Brian Khuu, but happy to accept contributions.

Originally part of https://github.com/mofosyne/arduino-gameboy-printer-emulator

## Purpose

This is a tool to help investigate Gameboy behavior by sitting
between a real Gameboy and a real Gameboy printer.

This is a spinoff of the Arduino Gameboy Printer Emulator V2 redesign,
where we were aiming for full support for all games now.

To do this, we needed the ground truth, thus we need to sniff the communication
between a real Gameboy printer and a real Gameboy.

## Telegram Gameboy Camera Chatroom

Got telegram instant messaging and have some questions or need any advice, or just want to share? Invite link below:

https://t.me/GameboyCamera

## Structure

* `./RealCapture/` : Real test vectors contributions from the community
* `./gbp_sniffer/` : Ardunio sketch for capturing packets between a real Gameboy and Gameboy printer.


## Usage of gbp_sniffer (arduino)

gbp_sniffer is an arduino sketch, tested on an ardunio nano. To construct...

Split a cable and locate the GND, Serial Ouput, Serial Input and Clock.

Solder these wires to the arduino using the pinout shown below.

Plug a Gameboy and a printer to both ends of the cable. I've added auto detection
routine so you don't have to worry about which ends to plug it in.

Next download `./gbp_sniffer/gpb_sniffer.ino` to your arduino nano.
After that, open the serial console and set the baud rate to 115200 baud.

You can now send an image over to the real Gameboy and the serial console will
show the desired dump.

This will give you an output similar to those found in `./RealCapture/`.

(To view the content, you can use the raw decoder found here](https://mofosyne.github.io/arduino-gameboy-printer-emulator/GameBoyPrinterDecoderJS/gameboy_printer_js_raw_decoder.html)

### General Pinout

```
Gameboy Original/Color Link Cable Pinout
 ___________
|  6  4  2  |
 \_5__3__1_/   (at cable)
```

| Arduino Pin | Gameboy Link Pin                 |
|-------------|----------------------------------|
|  unused     | Pin 1 : 5.0V                     |
|  D4         | Pin 2 : Serial OUTPUT            |
|  D3         | Pin 3 : Serial INPUT             |
|  unused     | Pin 4 : Serial Data              |
|  D2         | Pin 5 : Serial Clock (Interrupt) |
|  GND        | Pin 6 : GND (Attach to GND Pin)  |



## Thanks

* Raphaël BOICHOT : For supplying real capture data in `./RealCapture/` folder


