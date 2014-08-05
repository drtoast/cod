## Ca$h on Delivery

Consumes dropship events from [5-by-5](dropship/5-by-5) and produces
lighting effects using NeoPixel lighting strips.

## Using the `ino` compiler

The `ino` compiler allows you to avoid the shit Arduino IDE.

```
$ brew install pip
$ brew install picocom
$ pip install ino
```

`ino` depends on your existing Arduino installation.  

With the version of Arduino that I have, I was getting errors compiling the Robot_Control library so fuck it:

```
$ rm -rf /Applications/Arduino.app/Contents/Resources/Java/libraries/Robot_Control
```

Setup up the submodule for the arduino library:

```
$ git submodule init
$ git submodule update
```

Now move your source code into the expected directory structure.  Use the [udp_server](https://github.com/dropship/arduino_networking/tree/682f2f1cec39b4a23a53c396c152430ce056fd03/arduino/udp_server) as an example.

```
$ ino build && ino upload && ino serial
$ ino build -m mega2560 && ino upload -m mega2560 && ino serial
```


And you're off to the :horse: races

- After importing any library in `vendor` using the Arduino app, it will copied to and compiled from
`Documents/Ardunio/libraries/<library>`, not `vendor`.

- Exit `ino serial` - `cntl-A cntl-X`

## Portable Hardware

#### Parts List

- Ardunio Mega 2560 (Uno may be enough, if not lighting hundreds of NeoPixels)
- [Adafruit CC3000 WiFi Shield](https://www.adafruit.com/products/1491)
- [NeoPixel LED Strip](https://www.adafruit.com/categories/183)
- Battery pack - This [9V pack](https://www.adafruit.com/products/248) plugs right into the Arduino

#### Instructions

- Attach WiFi Shield to Arduino
- Connect NeoPixel data line to Arduino Pin 6
- Power NeoPixel with additional 5V Power supply

#### Notes

- NeoPixel strips are not designed for a lot of repeated flexing. Be aware where you mount them.
