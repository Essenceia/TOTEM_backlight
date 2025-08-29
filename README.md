<picture align="center">
  <source media="(prefers-color-scheme: dark)" srcset="/docs/images/TOTEM_logo_dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="/docs/images/TOTEM_logo_bright.svg">
  <img alt="TOTEM logo" src="/docs/images/TOTEM_logo_dark.svg">
</picture>

<h1 align="center">T O T E M</h1>

Modified version of the wired TOTEM version 0.3 keyboard, reworked for outsourcing assembly to JLCPCB assembly services and modified to include white backlight.

## Backlight 

Adding simple white backlight to the keyboard. 
Since the default development board used as the controller doesn't have any more available pins 
the backlight could not be controlled by a key combination without the need to switch the board.

I debated removing this limitation but decided I decided to not invest the time in fixing this limitation
in favor of investing my time working on designing custom ASIC's. 

As such, the backlight intensity is controlled via a potentiometer accessible by opening the case. 

![switch](/docs/images/switch.png)

Since the switches are not symmetrical and only have an opening for the backlight led on the side opposite to the contact pins, placement 
of the led's implies switch direction. 
The original TOTEM layout gave the flexibility of placing the switch in either of two directions :
 
- pins up: connected to the switch shaft, allowing the switch to be swappable
- pins down: switches soldered in place 

![layout](/docs/images/layout.png)

I have chosen the **pins up** layout that allows the switch to still be swappable at the cost of requiring the use of the switch shaft.


:warning: The light intensity controlled circuit was dimensioned to fit these specific leds and potentiometer electrical characteristics, as such,
if you wish to re-use this design, you should **not** blindly switch the led's or the potentiometer model. 


## Manifacturability 

### Front face 

I like soldering 0603 led's as much as the next guys.
 
In other words: I rather do something else with my very limited time on earth, and my rumba is getting indigestion from all of the suckers that have vanished into the dust. 

Luckily, I can outsource the assembly of these components to wonderful pink and place machines, which on top of 
being more patient than me are orders of magnitude more consistent and precise. Such assembly services are 
offered directly by most big PCB manufacturers and for this board I will be going with JLCPCB. 

In order to outsource this work you will need to provide the BOM ( bill of materials ) and POS ( component position file ) files.

#### Bill of materials

Both files are human readable tables, the bill of materials file contains references to components in the JCBPCB component vendor database
as we will be purchasing the components as part of the assembly process. 

| Comment                  | Designator                                                                 | Footprint    | JLCPCB Part |
|---------------------------|----------------------------------------------------------------------------|--------------|---------------------------|
| Diodes 1N4148W           | DL1,DL2,DL3,DL4,DL5,DL6,DL7,DL8,DL9,DL10,DL11,DL12,DL13,DL14,DL15,DL16,   | SOD-123      | C2099                     |
|                           | DL17,DL18,DL19,DR1,DR2,DR3,DR4,DR5,DR6,DR7,DR8,DR9,DR10,DR11,DR12,DR13,   |              |                           |
|                           | DR14,DR15,DR16,DR17,DR18,DR19                                             |              |                           |
| Reset Button, SKHLLCA010 | RSW1,RSW2                                                                  | SKHLLCA010   | C139766                   |
| TRRS jack, PJ-320A       | J1,J2                                                                     | PJ-320A      | C2884926                  |
| LED                      | LEDL1,LEDL2,LEDL3,LEDL4,LEDL5,LEDL6,LEDL7,LEDL8,LEDL9,LEDL10,LEDL11,      | KT-0603W     | C2290                     |
|                           | LEDL12,LEDL13,LEDL14,LEDL15,LEDL16,LEDL17,LEDL18,LEDL19,LEDR1,LEDR2,      |              |                           |
|                           | LEDR3,LEDR4,LEDR5,LEDR6,LEDR7,LEDR8,LEDR9,LEDR10,LEDR11,LEDR12,LEDR13,    |              |                           |
|                           | LEDR14,LEDR15,LEDR16,LEDR17,LEDR18,LEDR19                                 |              |                           |
| Potenciometer            | RV1,RV2                                                                   | GF063P1-B201 | C128076                   |


#### Positional 

The positional file instructs pick and place machines, where and in which orientation each component should be placed on the board. 
These coordinates assume the part assume the footprints on the board are similar to the footprints used in the JCBPCB part database for this part. 
For example, it assumes both footprints are aligned on the orientation of a component. 

Since there where a few disparities between the original footprints and the JCBPCB part's footprints, a few of the footprint and schematic components 
has to been updated.

There is an overview of the result with the parts we will be outsourcing assemly for outlined in blue. 

These parts are : 

- diodes
- push button
- led's
- potentiometer
- jack connectors

![assembly](/docs/images/TOTEM_PCB_assembly.png)

## Back face 

Originally, the switch footprint and the switch shaft where part of the same footprint, make it incompatible with the 
footprint coordinate offset system used to automatically generate the positional file. 
As such, I have separated the switch from the switch shaft footprint allowing the generation of a bottom positional file to also outsource
shaft assembly. 

The begin said, JLCPCB doesn't offer assembly on both sides for the time being.
Thus, given the complexity difference I will only be outsourcing assembly of the top side.   

## Paths for improvement

- Switch out the developement board in favor of having more accessible pins : 
    - re-use my known to be good stm32 circuit -> removes the need to solder on the dev board + port QMK or ZMK to board \ 
        downside : design will be harder to re-use for the mechanical keyboard community as flashing the firmware now requires a JTAG
    - use another commonly used dev board as a controller \
        downside : still requires to solder on the dev board 

- Make backlight control be more easily accessible : 
    - rework case to have the potentiometer knob accessible on the side
    - add a switch upstream of the potentiometer and rework the case to have the backlight switch accessible on the side

## Credits

Original TOTEM repo : [https://github.com/GEIGEIGEIST/TOTEM](https://github.com/GEIGEIGEIST/TOTEM)

Credit to github user `geigeigeist` for the original design

## License

This hardware is under the CERN-OHL-P v2 license, see [LICENSE.md](LICENSE.md) 

