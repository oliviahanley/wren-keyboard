# Wren Keyboard

![wren_preview](/images/wren-preview.png)

## Introduction
The Wren Keyboard is a split ergonomic "system keyboard". It takes heavy inspiration from [Afternoon Labs' Breeze](https://afternoonlabs.com/breeze/) and [SplitKB's Kyria](https://blog.splitkb.com/blog/introducing-the-kyria), in addition to employing a case similar to the Corne's.

My primary keyboard for the last few years has been Prime Keyboards' prime_o, before which I used a handwired Planck. On both I made pretty heavy use of the numpad. I grew to appreciate the prime\_o's physical one, though, mostly because I spend a lot of time in Excel at my day job and like using the mouse and numpad simultaneously. I've been wanting to switch to ergo for a while, but I was annoyed by the thought of having to use a separate numpad to recreate that experience. This project was an attempt to solve that problem.

My original design, reflected in the [author layout](/images/author-layout.png), simply incorporated a southpaw numpad. After some feedback on my original deign from members of the r/ergomechkeyboards community, though, I decided to reinvent it as a "system keyboard" modeled after the old system cameras. The repository includes three boards, each reversible:
- A Lilly58/Kyria-inspired split board, with no extra keys;
- An extended layout with a 4x4 numpad; and
- An extended layout with a traditional nav cluster.

Each of these boards can be combined with the others in a split setup, so users can take their pick of a right or left nav cluster/numpad, or combine both in the same board. You could even just use two of the basic boards together for a more traditional layout, though I'm sure there are more elegant designs out there for that.

## Controller
The Wren uses a Pro Micro-compatible footprint, but is designed around the Elite-C's extra I/O pins on the numpad board. With just a Pro Micro, the numpad's rotary encoder won't work. I _think_ you could get a Nice!Nano to full compatibility with some creative soldering from the mid-board I/O pins to the appropriate pins for the encoder, but I haven't spent any time on this myself.

## PCB
The PCB uses reversible, MX-compatible footprints. There isn't hot-swap support yet, in large part because I didn't want to deal with the structural considerations of those sockets. If someone else wanted to make a pull request for a hotswap version, though, I'd be happy to merge it in. As well, in the system update I removed support for Alps switches.

The PCB is also specifically designed around rotary encoders with a diameter less than 0.5". I'm using Kilo 50 sized knobs, but others in a similar size class will work well, too.

## Case and Plate
This repository includes a top and bottom plate designed around M2 screws and standoffs. As with the PCB, this plate is only compatible with MX switches.

Additionally, a 3D printed outer case has been planned. This design wraps the PCB and top plate in a printed outer layer.

## Software
(To be added later.)

## Cost Estimates
(To be added later.)
