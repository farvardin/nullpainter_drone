# nullPainter Drone I

This is a fork of the [nullPainter Drone I](https://github.com/nullpainter/drone/).

The nullPainter Drone I is a four-oscillator drone synthesizer, driven by PureData Vanilla and running on a Raspberry Pi 4 Model B.

While the original version was made for a physical hardware, this version is adding a PureData panel and an interface for Akai MidiMix (which you can adapt for your own midi controller).

<img src="images/panel.png" title="PureData panel"></a>

<img src="images/midimix_sheet.png" title="midimix"></a>


get the [midimix](images/midimix_sheet_nullpainter_drone.pdf) sheet to print.

To connect to your controller, on Linux you can use jack, or list your midi devices with:

- aconnect -l

then 

- aconnect device_out:port device_in:port

(for example: ``aconnect 20:0 128:0``)




----------------------------


From the original README:

&nbsp;

The Drone I uses wavetable synthesis to generate sine, triangle and sine+triangle waveforms for each oscillator. Oscillators are selectively modulated together and each have a three-octave control. The Drone I features LFO and VCO against the first oscillator, a sub-oscillator, resonance control, a flanger, and blinkenlights for aesthetics. Audio is run through a stereo chorus, panner, compressor, and mid-side mixing. 

To interface the front panel controls, it uses two MCP3008 ICs for analog-to-digital conversion, and two MCP23S17 ICs for GPIO port expansion. These all use SPI bit-banging using the excellent [pigpio](https://abyz.me.uk/rpi/pigpio/) library. The Drone I uses my PureData [pigpio externals](https://github.com/nullpainter/pdpigpio) to read from both ICs and perform regular GPIO writes.

<img src="images/synth.jpg" title="Glamour shot"></a>

## Audio samples

Audio samples are available on [Soundcloud](https://soundcloud.com/nullpainter/sets/nullpainter-drone-i-audio-samples).

## Video

A video of the synth in action is on [YouTube](https://www.youtube.com/watch?v=A3pWmTlM0MA).


## Running

1. Clone and build PureData [pdpigpio externals](https://github.com/nullpainter/pdpigpio)
1. Add pdpigpio folders and `externals` folder to pd startup paths
1. Update GPIO pin mappings based on wiring

### GPIO pin mappings

Your pin mappings will most likely be different to mine. The MCP3008 and MCP23S17 pin mappings are defined in the `gpiorouter` subpatch. Additionally, pin mappings for LEDs are specified in the `freqbeat` and `pigpio` externals, used in the main drone patch.

## 

<img src="images/full-patch.png" title="Full patch"></a>
