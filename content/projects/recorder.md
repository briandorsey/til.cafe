+++
title="Learning project: build an audio recorder"
[extra] 
summary="Multi-year learning plan for designing and building an audio recorder."
+++

Multi-year plan to build an audio recorder. Learn in public. Learn slowly, and through iteration and direct experience.

## goal - learn and build something real

Build an audio recorder for unattended overnight outdoor field recordings.

Current target features: 

- *very* reliable.
- onboard stereo mics. MEMS microphones if the new generation are good, or use EM272 capsules.
- 2x stereo Plug-In-Power analog mic inputs (four inputs). For mics similar to [Lom Uši](https://store.lom.audio/products/usi) or [Clippy EM272](https://micbooster.com/clippy-and-pluggy-microphones/98-clippy-stereo-em272-microphone.html#/84-plug_type-right_angle).
    - inputs protected from shorts, overloads (& other potential issues?)
- analog low cut filter before ADCs. Support enable/disable... maybe cutoff adjustment.
- low noise ADC - at least as good or better than noise floor on EM272 capsules.
- parallel ADCs for each input channel - allowing lower gain on one for safety.
- above implies recording 8 channels at the same time.
- each channel sampled and recorded at 24bit, up to 96khz (bonus for higher, but not needed for ambiance recording).
- WAV only.
- excellent embedded metadata in recorded WAV files.
- reasonably optimized, low power consumption.
- safely finish writing files (including WAV headers/offsets) on power loss. 
- functional in a wide range of temperatures, approx: -20C through 50C.
- designed for electronics hobbyist assembly at home. 
- minimize software dependencies where possible
- API for control, device status and metadata updates.

Stretch feature goals:

- adjustable PIP voltage (~2-8V) (many capsules operate best at ~8V).
- XLR inputs
- dual SD cards & dual simultaneous writing (for backup/reliability).
- GPS for date and timecode - if clock is accurate enough, doesn't need to run often.
- modular design: swappable analog input sections (PiP, XLR, built-in), power, UX on separate boards
- API is also available remotely (BLE, or maybe LoRa)

Non goals: 

- Price optimization. Planning to spend years on this and only build a few. Use high quality parts.


# learning plan

This is primarily a learning project. I want this device to exist, but I also want to use it as an excuse to learn more about audio electronics, embedded programming, board design, testing, etc. Plan is to take the long way to get there, and do the electronics design, physical design, firmware authoring, and testing myself. Expecting to build smaller sub-projects along the way to learn by doing & iteration.

Planning to do the work in-public and as open source hardware/software.

## where I'm starting

- Software development experience - mostly glue code in Python/Go, comfy with infra stuff.
- Very basic electronics & DC power knowledge, from building eurorack kits, fiddling with Arduino/Teensy for simple projects, and remote control cars/planes.
- Amateur audio recordist - currently recording outdoors, editing and cataloging.

## learning plan

- Embedded programming
    - I don't think I'll be able to get the perf needed in Python, and don't want to learn C/C++, so thinking of Rust. Currently ~2 months into learning Rust.
    - Learn Rust fundamentals.
    - Learn embedded Rust via [embedded Rust book}(https://docs.rust-embedded.org/discovery/microbit/).
    - _project:_ write program to test SD write path: write synthesized WAV files & log data
    - Work on projects below.
- Audio programming
    - Learn about WAV files.
        - _project:_ write command line tool to parse and summarize WAV files & their metadata.
    - Learn about sampling analog signals on embedded devices.
        - _project:_ try to write very basic recorder firmware using microbit & onboard MEMS mic.
    - _what else am I missing here?_
- Audio testing
    - Learn how to test audio paths - enough to determine and verify the specs of the recorder
    - EIN, THD, Frequency response, SNR, etc.
- Hardware design
    - _(no idea where to start really)_
    - Need to learn fundamentals of analog audio, specifically the mic -> preamp -> ADC path.
    - Learn some board layout software and iterate on sending designs out to be created? 
        - _project:_ MixPre power adapter board (a very small, power distribution board)
    - Learn enough to decide on high level architecture (primary chip?, include FPGA?, board modularity?)
    - _what else am I missing here?_
- Iterate on design, build, test of the actual recorder.
    - _project:_ avoid the analog path and build an AES3 recorder (I have a use for a dedicated bit-bucket like this)
    - Iterate, build, test.



