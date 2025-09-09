# Pi Pico AWG

The repository contains the design for a PCB to host
a Raspberry Pi Pico acting as an arbitrary wave
form generator

## Design

This is a prototype design.

The PCB is not optimised for size and the DAC can
be reduced to a single component. Optimisation of
the design could reduce the size of the board
substantially. The Pico device can be swapped out
for a smaller design than the official Pico
provided the exposed GPIO pins meet the requirements
of the AWG code (8 sequentially numbered IO pins).

## Software

The python code included is not my own and has been
taken from an instructables page by rgco 
https://www.instructables.com/Arbitrary-Wave-Generator-With-the-Raspberry-Pi-Pic/

## Usage

The pico must be operating with micropython installed
as a base requisite.

By default the pico requires a computer host to upload
and run the required python code. This is a minimally
interactive process and requires the user to hard code
the desired frequency and wave form.

The python code generates a set of digital samples (from
4096 samples up to 65536 samples). Once generated the pico
will automatically replay the sample on loop.

If the code is renamed as "main.py" and uploaded to the
pico it will automatically run that code on boot allowing
the board to be integrated with another system.

## Issues

The RUN button is currently ineffective, this was
tested on breadboard but does not appear to be
operating. It is also worth noting that contrary
to the software notes it actually behaves as a 
HALT operation intead of RUN.

In order to achieve reasonable accuracy the 
generated wave form requires a high sample size to
avoid jitter. Generating larger sample sizes increases
the time required to begin producing the wave form
output.

The micropython firmware and supplied python code 
currently have a problem working on the Pico 2. This
has been previously tested as working and the cause
of the fault is not yet known.

## License

This design is licensed under the Creative Commons
CC-BY-SA 4.0 International license 
https://creativecommons.org/licenses/by-sa/4.0/deed.en