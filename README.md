<picture align="center">
  <source media="(prefers-color-scheme: dark)" srcset="/docs/images/TOTEM_logo_dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="/docs/images/TOTEM_logo_bright.svg">
  <img alt="TOTEM logo" src="/docs/images/TOTEM_logo_dark.svg">
</picture>

<h1 align="center">T O T E M</h1>

Modified version of the wired TOTEM 0.3 keyboard, rework for outsourcing part of the assembly to JLCPCB assembly services and featuring white backlight.

## Backlight 

Adding simple white backlight to the keyboard. 
Since the selected developpement board doesn't have any more availble pins the backlight could not be controlled by a key combination without needing to switch the board.
Given this project was intended to be a small day long project, I have opted to not change the controller or the case design ( for now at least ). 
As such, the backlight intensity is controlled via a potenciometer accessible by opening the case. 

This design stems from my usage, where I rarely adjust the light intensity once I find a setting I like.  

## Manifacturability 

I like sodering 0603 led's as much as the next guys. 
For the uninitiated this means: please make it stop, my eyes can't stand it, and my rumba is getting indigestion from all of the suckers that have vanished into the dust. 

This repo contrains the bom and front layer pos files for outsourcing assembly of the following part to JLCPCB : 
- diodes
- push button
- led's
- potenciometers
- jack connectors

![assemnly](/docs/images/TOTEM_PCB_assembly.png)

Unlike the original totem design, generating the bottom pos file for assembling the switch sharf is also possible, though JLCPCB doesn't offer assembly on both sides for the time being.  

## Paths for improvement

- Switch out the developpement board in favor of having more accessible pins : 
    - re-use my known to be good stm32 circuit -> removes the need to soder on the dev board + port QMK or ZMK to board \
        downside : design will be harder to re-use for the mechanical keyboard comunity as flashing the firmware now requires a jtag
    - use another commonly used dev board as a controller \
        downside : still requires to soder on the dev board 

- Make backlight control be more easily accessible : 
    - rework case to have the potencimeter knob accissible on the side
    - add a switch upstream of the potenciometer and rework the case to have the backlight switch accessible on the side

## Credit

Original TOTEM repo : [https://github.com/GEIGEIGEIST/TOTEM](https://github.com/GEIGEIGEIST/TOTEM)

Credit to github user geigeigeist for the original design. 

