###### Sound Level Meters (SLM) - What are they?
It's used to quantify different _kinds_ of noise --> i.e. not _necessarily_
the _level_ of noise. It can pick up a wide range of frequencies, and because
of this, it is often the case that the output does not correlate well to
human-perceived loudness. Whilst some sources suggest using a _loudness meter_
instead, unless the use case requires a high level of precision, then there are
other methods of making the measuresd level of noise correspond to that heard
by humans.

###### Measuring Sound
There are broadly, 3 types of sound measuring systems.
(1) Conventional SLM
(2) Integrating-averaging SLM
(3) Integrating SLM


<!-- MORE NOTES TO EXPLAIN AC/DC, RMS conversion -->
(2) and (3) _sums_ the frequency-weighted noise, to produce "sound exposure" in
Pa^2s; they are useful for distinguishing and recording ["damage risk"](------).
(1) takes the alternating current (AC) signal output from a microphone, and
converts it into direct current (DC) by a root-mean-square (RMS) circuit. When a
snapshot of this is taken at a certain noise level, the output is referred to
as the _"exponentially averaging"_ SLM.

###### Time Weighting
RMS circuits require a time constant of integrations; a.k.a. _"time-weighting"_.
They are measurements of noise and can be described by the following 3 standards.
Slow (S) = 1s, Fast (F) = 125ms and Impulse (I) = F/4

<!-- CHECK -->
Output of an RMS circuit is directly proportional to voltage. This output is
passed through a logarithmic circuit, which outputs a reading calculated by:
20 x log(RMS(sound pressure)/(reference sound pressure)).

The RMS of Ps is obtained with standard frequency weighting and standard time weighting.
For airborne sound, Ps(ref) = 20microPa

=> dB is a dimensionless ratio of 2 pressures.

Read more by googling the international standards, "IEC61672-1"

###### How speakers produce sound
A microphone consists of a _transducer_ which picks up **mechanical vibrations**
caused by sound waves traversing the air, and converts them into _sound_.
The transducer is composed of a _diaphragm_ which responds to _changes_ in the
air pressure, due to sound wave propagation. The deviation in sound pressure is
then converted into an **electrical signal**, which is then output as voltage.
The sensitivity of the microphone is graded on the voltage output, when a known,
constant sound pressure is applied. The SLM uses this to convert the electrical
signal back into sound pressure (i.e. to produce the sound that we hear through
speakers), which is outputted in _decibels_ (dB).

###### Glossary
- Transducer: A component which converts one form of energy into another; often
in the form of a signal.
- Sound Level Meter === Sound Pressure Meter
