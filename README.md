<picture align="center">
  <source media="(prefers-color-scheme: dark)" srcset="/docs/images/TOTEM_logo_dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="/docs/images/TOTEM_logo_bright.svg">
  <img alt="TOTEM logo" src="/docs/images/TOTEM_logo_dark.svg">
</picture>

<h1 align="center">T O T E M</h1>

Modified version of the wired TOTEM version 0.3 keyboard, reworked for outsourcing assembly to JLCPCB assembly services and modified to include white backlight.

## Backlight 

Adding simple white backlight to the keyboard. 
Since the default developpement board used as the controller doesn't have any more availble pins 
the backlight could not be controlled by a key combination without the need to switch the board.

I debated removing this limitation but decided I decided to not invest the time in fixing this limitation
in favor of investing my time working on designing custom ASIC's. 

As such, the backlight intensity is controlled via a potenciometer accessible by opening the case. 

Since the switches are not symetrical and only have an opening for the backlight led on the side opposite to the contact pins, placement 
of the led's implies switch direction. 
The original TOTEM layout gave the flexibility of placing the switch in either of two directions : 
- pins up: connected to the switch shaft, allowing the switch to be swappable
- pins down: switches sodered in place 
I have chosen the **pins up** layout that makes the switch swappably and requires the use of the switch shaft.

![switch](/docs/images/switch.png)

:warning: The light intensity controlled circuit was dimentioned with these specific leds and potenciometer model in mind, as such,
if you wish to re-use this design, you should **not** blindly switch the led's or the potenciometer model. 




## Manifacturability 

### Front face 

I like sodering 0603 led's as much as the next guys.
 
In other words: I rather do something else with my very limited time on earth, and my rumba is getting indigestion from all of the suckers that have vanished into the dust. 

Luckily, I can outsource the assembly of these components to wonderful pink and place machines, which on top of 
being more patient than me are orders of magnitude more consistent and precise. Such assembly services are 
offered directly by most big PCB manifacturers and for this board I will be going with JLCPCB. 

In order to outsource this work you will need to provide the BOM ( bill of materials ) and POS ( component position file ) files.

#### Bill of materials

Both files are human readable tables, the bill of materials file contains references to components in the JCBPCB component vendor database
as we will be purchasing the components as part of the assembly process. 

| Comment                  | Designator                                                                 | Footprint    | JLCPCB Part #（optional） |
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



This repo contrains the bom and front layer pos files for outsourcing assembly of the following part to JLCPCB : 
- diodes
- push button
- led's
- potenciometers
- jack connectors

![assemnly](/docs/images/TOTEM_PCB_assembly.png)

## Back face 

Originally, the switch footprint and the switch shaft where part of the saa
The footprints for the switches has been changed and the switch shaft has been seperating from the switch. 
As such generating the bottom pos file for assembling the switch sharf is also possible, though JLCPCB doesn't offer assembly on both sides for the time being.  

## Paths for improvement

        downside : design will be harder to re-use for the mechanical keyboard comunity as flashing the firmware now requires a jtag
    - use another commonly used dev board as a controller \
        downside : still requires to soder on the dev board 

- Make backlight control be more easily accessible : 
    - rework case to have the potencimeter knob accissible on the side
    - add a switch upstream of the potenciometer and rework the case to have the backlight switch accessible on the side

## Credit

Original TOTEM repo : [https://github.com/GEIGEIGEIST/TOTEM](https://github.com/GEIGEIGEIST/TOTEM)

Credit to github user geigeigeist for the original design. 

