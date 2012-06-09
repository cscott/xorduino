This is an Open Hardware peripheral for the OLPC XO-1/1.5/1.75.

The files are created using Eagle 6.2.0 on Linux and the SparkFun footprint
libraries.

Strong inspiration drawn from the following Open Hardware designs (thanks for
sharing!):
  1) The Arduino Leonardo (arduino-compatible ATmega32U4 design)
  2) SparkFun's ATmega32U4 breakout (http://www.sparkfun.com/products/11117)
     for figuring out which parts of the Leonardo design are actually
     mandatory
  3) SparkFun's Scratch Sensor Board-compatible PicoBoard
     (http://www.sparkfun.com/products/10311)

Some notes:

1) Many of the Leonardo design's components are optional in a
   lowest-possible-cost design, for a number of different reasons:
   a) USB port protection which is already included on the XO
      motherboard
   b) ESD and protection diodes (helpful but not required)
   c) bypass caps and ferrites for less noise on analog signals
      (helpful but not required)
   Wherever possible I've included the pads anyway, so that less
   budget-conscious users can populate these components.  At times
   this has required jumper traces which you need to cut if you
   decide to populate the optional components.

2) I eliminated the multi-way 3.3V/5V internal/external power supply
   functionality of the Arduino to save cost.  The XOrduino is 5V
   only, powered by the USB port.  The Arduino "3.3V" pin on the
   shield connector is left disconnected.  It may be that I want to add
   pads and jumpers here to allow "power users" to explore other
   options.

3) I'm attempting to make this board local-assembly-friendly, so I
   used a large number of through-hole parts.  This complicates
   routing; I ended up needing to use a 4-layer board, which I can
   get away with but which drives up the PCB cost for most people.
   Different trade offs are possible, and maybe I shouldn't be quite
   so afraid of SMT, especially since the ATmega32U4 is only available
   in SMT versions anyway.

4) I made this Scratch Sensor Board compatible, but it occurs to me
   that many of the Scratch sensors are redundant on the XO.
   We have a microphone already, and the XO-1.75 includes an ambient
   light sensor.  We have two channels of analog input via the
   microphone jack.  The keyboard has plenty of "button" sensors.
   The XO-1.75 also has an accelerometer.  The only "new" input is the
   rotary pot ("slider" in the original scratch sensor board).
   Is there a better/more interesting set of sensors we could
   incorporate?  Or is tutorial-compatibility with the learning
   materials written for the original Scratch Sensor board worth
   preserving?  And the Scratch Sensors are usable by the Arduino
   even when you disconnect from the XO, which is worth something.

5) There's a USB plug integrated with the PCB but it has some issues:
   the board may well be too heavy to use unsupported, and the PCB
   being used is only 0.8mm thick, which is too thin for good
   connection in the slot (I could add break-off tabs like I
   did for the XO stick to remedy the latter).

   There are pads for using a through-hole USB-mini-B connector, but
   they are rather expensive (~$1) -- and the prognosticators of the
   future say that "mini" USB is being phased out in favor of "micro"
   USB worldwide, in part due to the EU regulations specifying micro
   USB as the universal power adapter format.

   Also, when the discrete connector is populated, it leaves the USB
   signals and power/gnd exposed on big metal tabs, which could be
   non-ideal.

   It may well be that I should switch to a SMT micro-B connector, if
   I can find one which is acceptably hand-solderable.

  -- C. Scott Ananian, 2012-06-09
