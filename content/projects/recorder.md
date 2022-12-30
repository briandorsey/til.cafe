+++
title="Learning project: build an audio recorder"
date=2022-12-29 
[extra] 
summary="Multi-year learning plan for designing and building an audio recorder."
+++

# Multi-year plan to build an audio recorder

## goal - learn and build something real

Build an audio recorder for unattended overnight outdoor recordings. 

Current target features: 

- *very* reliable.
- 2x stereo Plug-In-Power analog mic inputs. (for mics similar to [Lom Uši](https://store.lom.audio/products/usi) or [Clippy EM272](https://micbooster.com/clippy-and-pluggy-microphones/98-clippy-stereo-em272-microphone.html#/84-plug_type-right_angle) )
- reasonably optimized, low power consuption
- low noise ADC - at least as good or better than noise floor on EM272 capsules
- safely finish writing files (including WAV headers/offsets) on power loss. 
- Parallel ADCs for each input channel - allowing lower gain on one for safety
- above implies recording 8 channels at the same time
- each channel sampled and recorded at 24bit, up to 96khz (bonus for higher, but not needed for ambience recording)
- WAV only
- onboard stereo mics. MEMS microphones if the new generation are good, or use EM272 capsules
- excellent embedded metadata in recorded WAV files
- functional in a wide range of temperatures, approx: -20C through 50C

Stretch feature goals:

- adjustible PIP voltage (~2-8V) (many capsules operate best at ~8V)
- dual SD cards & dual simultaneous writing (for backup/reliability)
- GPS for date and timecode - if clock is accurate enough, doesn't need to run often


# learning plan

This is primarily a learning project. I want this device to exist, but I also want to use it as an excuse to learn more about audio electronics, embedded programming, board design, testing, etc. Plan is to take the long way to get there, and do the electronics design, phsyical design, firmware authoring, and testing myself. Expecting to build smaller sub-projects along the way to learn by doing & iteration.

I'm strongly considering doing all the work in-public and as open source hardware/software. But haven't decided yet. 

## where I'm starting

- software development experience - mostly glue code in Python/Go, comfy with infra stuff
- very basic electronics & DC power knowledge, from building eurorack kits, fiddling with Arduino/Teensy for simple projects, and remote control cars/planes
- amature audio recordist - currently recording outdoors, editing and cataloging

## learning plan

- embedded programming
    - I don't think I'll be able to get the perf needed in Python, and don't want to learn C/C++, so currently thinking of Rust. Currently ~2 months into learning Rust.
    - Learn Rust fundamentals
    - Learn embedded Rust via [embedded Rust book}(https://docs.rust-embedded.org/discovery/microbit/)
    - Work on projects below
-  audio programming
    - learn about WAV files
        - _project:_ write command line tool to parse and summarize WAV files & their metadata
    - learn about sampling analog signals on embedded devices
        - _project:_ try to write very basic recorder firmware using microbit & onboard MEMS mic. 
    - _what else am I missing here?_
- hardware design
    - _(no idea where to start really)_
    - Need to learn fundamentals of analog audio, specifically the mic -> preamp -> ADC path
    - Learn some board layout software and iterate on sending designs out to be created? 
        - _project:_ MixPre power adapter board (a very small, power distribution board)
    - learn how to test audio paths - enough to determine and verify the specs of the recorder
    - _what else am I missing here?_
- Iterate on design, build, test of the actual recorder
    - _project:_ avoid the analog path and build an AES3 recorder (I have a use for a dedicated bit-bucket like this)



