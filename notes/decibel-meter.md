# Prep-work for the ["Decibel Meter Project"](https://github.com/dwyl/hq/issues/113)
Some notes on things to consider when creating the decibel meter...

> What do we expect from this product? Specs:
- Record the _level of noise_ in decibel(dB) in real-time on the device (using reliable components).
- Display the noise level in dB (screen or set of LEDs)
- **Flash** a clear warning when the sound level is too high so people are instantly aware.
- Optional:
  - Store the data _locally_ in a time-series database for later analysis.
  - Display a _graph_ so we know what times of the day are the most noisy/quiet

### Preliminary Research

#### Base Hardware choice:

###### (1) Raspberry Pi
(Suggested by @nelsonic in the [title of the original issue](https://www.raspberrypi.org/forums/viewtopic.php?t=97397&p=677178))

Pros:
- Follows through with the 'javascript' (JS) theme across existing dwyl repositories.
- Easier for hardware-newbies to dive into, if they already follows/learn from dwyl tutorials (because they will/may have already played around with JS).
- Very little _base_ set-up, as it _is_ a computer. If anything it's a lot more powerful than we probably need.

Cons:
- It's a computer, and apart from the extra hardware components (e.g. microphone, etc.), it's already been set-up - is this _advantageous_ or _disadvantageous_ for a beginner?
- A Raspberry Pi [_is a small computer_](https://www.raspberrypi.org/help/videos/) and can host an _operating system_ like Linux...Is this maybe "too" powerful?

(_TODO:_ Confirm the **type** of project - electronics or programming - that is being required.)

###### (2) Arduino


Pros:
- The hardware is _less complicated_ and gives you a chance to find out about each of the components that make up a 'computer'.   
  - This also means that we can _minimise energy usage_ because we will _only add the components we need_ --> something that's been requested for, in the [specs](https://github.com/dwyl/hq/issues/113)

###### (3) Picaxe
_Do we even need a processor?_ Picaxe suggested [here](https://www.raspberrypi.org/forums/viewtopic.php?t=97397&p=677178)

##### Additional Hardware Components

- [ ] Transducer (microphone)
- [ ] Audio amp --> Switchable frequency response?
- [ ] AC-DC converter
- [ ] Analogue to Digital converter
- [ ] Base hardware (RaspberryPi/Arduino/Picaxe)
- [ ] Bunch of LEDs

- [ ] Monitor (if not RaspberryPi)

##### Other things to consider

- JohnnyFive (@naazy's awesome suggestion!), which uses the [Firmata protocol](https://github.com/firmata/protocol) to talk to the micro-controller. This would allow us to programme in JS :thumbs-up: !! There are two options with this:
  - Use it on an Arduino, and send commands to the board through a Raspberry Pi.
  - Use it on a RaspberryPi, and use the Raspi-IO plugin to make Firmata compatible with the board.

- If we want to be doing other data analysis (e.g. spectrum analysis) we will need a processor --> Raspi or Arduino.

- How have other people achieved this?
  - [The Grove - Loudness Sensor](http://wiki.seeed.cc/Grove-Loudness_Sensor/): "Uses an amplifier and microphone. Amplifies and filters out high frequency signals. Outputs a positive envelop."
    - What is the significance of _amplifying_ the sound, when it's being _filtered out anyway_?

- How will we be measuring sound?
  - Peak-to-Peak amplitude from output signal (of amplifier)?
  - What will a sufficient sample window be? 50ms will allow us to sample low frequency signals (~20Hz) --> Do we need _lower_? I.e. what is the huamn-audible range of frequencies?

##### Software choices

- Raspi + JS (J5 + Raspi-IO)
- Raspi + JS && Arduino
- Arduino + Sketch (or IDE)

#### Notable issues

##### Perceived/Apparent loudness !== Sound picked up by a microphone

- Need to get a resolution to allow for a _good dynamic range_. 24 bits has been [suggested](https://www.raspberrypi.org/forums/viewtopic.php?t=18014&p=179448)
- Filtering for a _noise power reading_;
  - Do we want peak, RMS or average?
  - Do we weigh high frequencies higher or lower?
- If we want to measure (human-)perceived loudness, we need to consider _A-weighting_

##### Peak !== Loudness

- Need to look into loudness normalisation and peak normalisation 
