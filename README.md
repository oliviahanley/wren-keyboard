# Wren Keyboard

![glamor shot](/images/glamor_shot.jpeg)
![Universal PCB](/images/wren-universal.png)
![Example Layout](/images/author-layout.png)

## Table of Contents
- [Introduction](https://github.com/oliviahanley/wren-keyboard#introduction)
- [2.0 Update](https://github.com/oliviahanley/wren-keyboard#2.0-update)
- [Controller](https://github.com/oliviahanley/wren-keyboard#controller)
- [PCB](https://github.com/oliviahanley/wren-keyboard#pcb)
- [Case and Plate](https://github.com/oliviahanley/wren-keyboard#case-and-plate)
- [Software](https://github.com/oliviahanley/wren-keyboard#software)
- [Cost Estimates and Purchasing](https://github.com/oliviahanley/wren-keyboard#cost-estimates-and-purchasing)
- [BOM](https://github.com/oliviahanley/wren-keyboard#bom)
- [Build Guide](https://github.com/oliviahanley/wren-keyboard#build-guide)

## Introduction
The Wren is a split ergonomic system keyboard. It takes heavy inspiration from the Lily58, [Afternoon Labs' Breeze](https://afternoonlabs.com/breeze/), and [SplitKB's Kyria](https://blog.splitkb.com/blog/introducing-the-kyria) with a Corne-ish layout.

Before this, my primary keyboard had been Prime Keyboards' prime_o, before which I used a handwired Planck. On both I made pretty heavy use of the numpad. I grew to appreciate the prime\_o's physical one, though, mostly because I spend a lot of time in Excel at my day job and like using the mouse and numpad simultaneously. I've been wanting to switch to ergo for a while, but I was annoyed by the thought of having to use a separate numpad to recreate that experience. This project was an attempt to solve that problem.

My original design simply incorporated a southpaw numpad. After some feedback, though, I decided to reinvent it as a more adaptable design. The repository includes a universal PCB (incorporating break-away tabs) and plates to make four boards, each reversible:
- A Lilly58/Kyria-inspired split board, with no extra keys;
- An extended layout with a 4x4 numpad;
- An extended layout with a traditional nav cluster; and
- A small 4x4 macropad (nicknamed Egg).

Each of these boards (besides the macropad) can be combined with the others in a split setup, so users can take their pick of a right or left nav cluster/numpad or combine both in the same board. You could even just use two of the basic boards together for a more traditional layout, though I'm sure there are more elegant designs out there for that.

## 2.0 Update
The 2.0 release includes several major changes, including:
- A 3D printable (or CNCable) case with two height variations
- Nice!Nano compatibility with battery plug and ZMK compatibility
- Nice!View support
- Support for hot-swap sockets in addition to soldered switches
- Choc v1 variant
- Optional display cover
- Better design and documentation for the Egg
- Flip-flop footprints for the MCU

## Controller
The Wren uses a Pro Micro-compatible footprint, but is designed around the Elite-C or nice!Nano's extra I/O pins. With just a Pro Micro, the outer column and nice!view won't work.

## PCB
The PCB uses reversible, MX and choc compatible footprints with hot-swap support.

The PCB is specifically designed around rotary encoders with a diameter less than 0.5". I'm using Kilo 50 sized knobs, but others in a similar size class will work well, too.

## Case and Plate
This repository includes a top and bottom plate designed around M2 screws and standoffs. The bottom plate can be manufactured out of FR4 PCB material by any manufacturer; this will likely be the most cost-effective option. The top plate cannot be manufactured by my preferred PCB fabricator, JLCPCB, but your milage may vary. Instead, I used the .eps files included in the [Case folder](https://github.com/oliviahanley/wren-keyboard/tree/main/Case) to have my top plates manufactured in stainless steel by SendCutSend. In my experience these plates are an extremely tight fit around Kailh Box switches, but considering these aren't hot-swap that's an acceptable trade-off for me.

To make a complete case, you'll need 7 M2 spacers (5 for the plain board), a top plate, and a bottom plate.

There's also a 3D-printed bottom case. This uses the top plate and PCB without the bottom plate. \<\<MORE HERE\>\>

## Software
Tested code for this board is in the [main QMK repository](https://github.com/qmk/qmk_firmware/pull/14570). Thanks so much to [noroadsleft](https://github.com/qmk/qmk_firmware/pull/16462) for getting QMK configurator working! To build a hex file with the default keymap, use the following code after setting up your [QMK build environment](https://docs.qmk.fm/#/newbs_getting_started):

```
qmk compile -kb wren -km default
```

This can be flashed to your keyboard [in the usual way](https://docs.qmk.fm/#/newbs_flashing). The push-button below the microcontroler will put the keyboard into DFU mode. 

When customizing your keymap, note that the matrix includes all keys that would be present in a numpad-numpad pair. In other words, even if the left side of your physical keyboard lacks a numpad, your keymap.c file will include those keys. Feel free to either mark all those keys with a KC_NO keycode or leave them as-is--it's not like you can press them anyway :). As well, if you'd like to plug your USB cable into the right half instead of the default left, add the following to your config.h:

```
#define MASTER_RIGHT
```

\<\<ZMK INFO HERE\>\>

## Cost Estimates and Purchasing <\<\UPDATE\>\>
It should be relatively affordable to have these boards manufactured. Here are my costs for my PCB components at JLCPCB in USD as of September 2021:
- Universal PCB (15 boards): $35.30
- Numpad bottom plate (5 boards): $14.50
- Nav bottom plate (5 Boards): $13.60
- Plain bottom plate (5 boards): $10.80
- Egg bottom plate (5 boards): $2.00

And for my plates from SendCutSend:
- Numpad top plate (2 plates): $62.38
- Nav top plate: $34.94
- Plain top plate: $26.08

The repository should include up-to-date zipped Gerber files, which can be used to have PCBs fabbed at your manufacturer of choice. I'm partial to JLCPCB (which consistently has very low prices and now offers aluminum PCB options for plates), but OSHPark is a good option if you're in the US and like purple or want single boards. For best compatibility, please have both plates and cases manufactured with a 1.6mm or 1.5mm thickness.

(I'm currently not planning on offering these boards as a kit. It should be cost-competitive to source the cases and plates yourself, and getting comfortable with ordering PCBs is a great first step to designing your own custom board. If you are interested in stocking this keyboard, though, please feel free to reach out and I'll be happy to provide any help I can.)

## BOM <\<\UPDATE\>\>
### Numpad Board
To assemble a numpad half, you'll need these parts:
- 1 Universal PCB
- 1 Numpad top plate
- 1 Numpad bottom plate
- 1 Elite-C microcontroller
- 7 8mm M2 threaded separators
- 14 4mm M2 screws
- 44 MX-style keyswitches
- 43 1u MX keycaps
- 1 2u MX keycaps
- 45 1N4148 diodes
- 1 Alps EC-11 compatible rotary encoder (Bourns PEC11L-4115F-S0020 recommended)
- 1 Rotary encoder knob (0.5" diameter or less)
- 1 2u PCB-mount cherry stabilizer
- 1 6mm push-button switch
- 1 PJ320E TRRS jack
- 2 4.7kΩ axial resistors

### Nav Cluster Board
To assemble a nav cluster half, you'll need these parts:
- 1 Universal PCB
- 1 Nav cluster top plate
- 1 Nav cluster bottom plate
- 1 Pro Micro compatible microcontroller
- 7 8mm M2 threaded separators
- 14 4mm M2 screws
- 38 MX-style keyswitches
- 37 1u MX keycaps
- 1 2u MX keycaps
- 39 1N4148 diodes
- 1 Alps EC-11 compatible rotary encoder (Bourns PEC11L-4115F-S0020 recommended)
- 1 Rotary encoder knob (0.5" diameter or less)
- 1 2u PCB-mount cherry stabilizer
- 1 6mm push-button switch
- 1 PJ320E TRRS jack
- 2 4.7kΩ axial resistors

### Plain Board
To assemble a nav cluster half, you'll need these parts:
- 1 Universal PCB
- 1 Plain top plate
- 1 Plain bottom plate
- 1 Pro Micro compatible microcontroller
- 7 8mm M2 threaded separators
- 14 4mm M2 screws
- 28 MX-style keyswitches
- 27 1u MX keycaps
- 1 2u MX keycap
- 29 1N4148 diodes
- 1 Alps EC-11 compatible rotary encoder (Bourns PEC11L-4115F-S0020 reccomended)
- 1 Rotary encoder knob (0.5" diameter or less)
- 1 2u PCB-mount cherry stabilizer
- 1 6mm push-button switch
- 1 PJ320E TRRS jack
- 2 4.7kΩ axial resistors

### Egg Macro Pad
To assemble an egg with a broken-off piece of a main board, you'll need these parts:
- 1 Universal PCB
- 1 Egg top plate
- 1 Egg bottom plate
- 1 Pro Micro compatible microcontroller
- 4 8mm M2 threaded separators
- 8 4mm M2 screws
- 12/16 MX-style keyswitches
- 12/16 1u MX keycaps
- 12/16 1N4148 diodes

## Build Guide <\<\UPDATE\>\>
_Please note that this build guide refers to the "top" or "bottom" of the PCB. Since the PCB is reversible, these terms are relative to the final orientation of the board, not anything absolute. For example, the top of the right hand board would be the bottom of the left-hand board._

0. If necessary, break off any unused sections of the PCB. This is best accomplished by placing the board on a hard, flat surface with the perforated section of the board placed over the edge. While holding the main section of the board to the surface, firmly press down on the section you'd like to detach until it breaks off. Then, use a file to remove any remnants of the perforation. 

![break-off](/images/tutorial/0_break-off.jpeg)

1. Next, place diodes on the bottom side of the PCB, taking care to place the diodes with the black stipe facing the square pad.

![placing diodes](/images/tutorial/2_placing_diodes.jpeg)

TIP: Use needle-nose pliers to assist in bending diodes, as shown below.

![bending diodes](/images/tutorial/1_bending_diodes.jpeg)

2. Solder the diodes in place on the bottom side of the board.

![soldering diodes](/images/tutorial/3_soldering_diodes.jpeg)

3. Place the resistors on the bottom side of the PCB and solder them into place.

![placing resistors](/images/tutorial/4_placing_resistors.jpeg)

4. Turn the board over and clip the leads of the resistors and diodes as close as possible to the PCB. To avoid fitment issues with switches, ensure that the leads are cut nearly flush; nail clippers are good for this purpose.

![unclipped leads](/images/tutorial/5_unclipped_leads.jpeg)
![clipped leads](/images/tutorial/6_clipped_leads.jpeg)

5. Place the headers for the microcontroller in place with the plastic spacer at the front of the board and secure them with a piece of painter's tape, taking care that they are perfectly straight. 

![headers placed](/images/tutorial/7_headers_placed.jpeg)
![headers taped](/images/tutorial/8_headers_taped.jpeg)
![headers taped below](/images/tutorial/9_headers_taped_below.jpeg)

Using the tape to ensure the headers remain straight, tack solder a pin on each strip.

![headers tack soldered](/images/tutorial/10_headers_tack_soldered.jpeg)

Remove any remaining tape and solder the remaining pins.

![headers soldered](/images/tutorial/11_headers_soldered.jpeg)

6. Solder the controller to the headers on the front of the board. The controller should be facing down on the left half, and up on the right half. 

![controller soldered](/images/tutorial/12_controller_soldered.jpeg)

7. Place the reset button below the controller on the front of the board and solder it into place.

![button placed](/images/tutorial/13_button_placed.jpeg)
![button soldered](/images/tutorial/14_button_soldered.jpeg)

8. Place the TRRS jack on the front of the PCB and solder it into place.

![trrs placed](/images/tutorial/15_trrs_placed.jpeg)
![trrs soldered](/images/tutorial/16_trrs_soldered.jpeg)

9. Place the rotary encoder on the front of the PCB and solder it into place. Take care to ensure the encoder is as straight as possible; it is possible for the encoder to interfere with the plate if it's attached incorrectly.

![encoder placed](/images/tutorial/17_encoder_placed.jpeg)
![encoder soldered](/images/tutorial/18_encoder_soldered.jpeg)

10. Place the stabilizer.

![stab placed](/images/tutorial/19_stab_placed.jpeg)

11. Snap the switches into the plate, taking care to match the orientation of the PCB. They will likely be a tight fit.

![switches placed front](/images/tutorial/20_switches_placed_front.jpeg)
![switches placed rear](/images/tutorial/21_switches_placed_rear.jpeg)

12. Fit the switchplate onto the PCB, taking care to fit it around the encoder as shown.

![encoder fit](/images/tutorial/22_encoder_fit.jpeg)
![switchplate fitted](/images/tutorial/23_switchplate_fitted.jpeg)

13. Tack solder the switchplate into place using the switches on the corners of the board.

![switchplate tack soldered](/images/tutorial/24_switchplate_tack_soldered.jpeg)

14. Finish soldering the switchplate.

![switchplate soldered](/images/tutorial/25_switchplate_soldered.jpeg)

15. Attach the knob for the rotary encoder.

![encoder knob attached](/images/tutorial/27_encoder_knob_attached.jpeg)

16. Attach the standoffs using a screw through the front of the PCB.

![standoff attached front](/images/tutorial/28_standoff_attached_front.jpeg)
![standoff attached rear](/images/tutorial/29_standoff_attached_rear.jpeg)
![standoff attached all](/images/tutorial/30_standoff_attached_all.jpeg)

17. Clean off any excess flux using isopropyl alchohol.

18. Using the standoffs, attach the rear plate to the board.

![rear plate attached](/images/tutorial/31_rear_plate_attached.jpeg)

19. Attach rubber bumpers to the rear of the board for stability.

![rubber bumpers](/images/tutorial/32_bumpers_attached.jpeg)

20. Admire your work! Your board is ready to be flashed. If necessary, repeat with the other side of the board.

![finished](/images/tutorial/33_finished.jpeg)
