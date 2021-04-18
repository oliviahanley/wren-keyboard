# Wren Keyboard
## Introduction
The Wren Keyboard is a 6x5+4 key asymmetrical split ergonomic keyboard with a southpaw numpad. It takes heavy inspiration from [Afternoon Lab's Breeze keyboard](https://afternoonlabs.com/breeze/), but adds rotary encoder support and an additional row on the larger half.

My primary keyboard for the last few years has been Prime Keyboards' prime_o, before which I used a handwired Planck. On both I made pretty heavy use of the numpad. I grew to appreciate the prime\_o's physical one, though, mostly because I spend a lot of time in Excel at my day job and like using the mouse and numpad simultaneously. I've been wanting to switch to ergo for a while, but I was annoyed by the thought of having to use a separate numpad to recreate that experience. This design came from that annoyance.

## Controller
The Wren uses a Pro Micro-compatible footprint, but is designed around the Elite-C's extra I/O pins on the left side. With just a Pro Micro, the left side's rotary encoder won't work. I _think_ you could get a Nice!Nano to full compatibility with some creative soldering from the mid-board I/O pins to the appropriate pins for the encoder, but I haven't spent any time on this myself.

## PCB
The PCB uses Alps/MX compatible footprints. There isn't hot-swap support yet, in large part because I didn't want to deal with the structural considerations of those sockets. If someone else wanted to make a pull request for a hotswap version, though, I'd be happy to merge it in.

## Case and Plate
This repository includes a top and bottom plate designed around M2 screws and standoffs. As with the PCB, this plate should be compatible with both Alps and MX switches.

Additionally, a 3D printed outer case has been provided. This design wraps the PCB and top plate in a printed outer layer.

## Software

## Cost Estimates