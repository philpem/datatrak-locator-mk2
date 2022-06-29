# Datatrak Locator Mk.2 schematic

Author: Phil Pemberton <philpem@philpem.me.uk>

This is part of [my work reverse-engineering the Datatrak LF navigation system](https://www.philpem.me.uk/datatrak/start) -- specifically, it's a reverse-engineered schematic for the Locator Mk.2 navigation receiver.

I largely undertook this multi-year project (I started the PCB reverse-engineering in 2019 and finished it in mid-2022) as an experiment. My main objective was to make some use out of the half-dozen Datatrak receivers in my spares drawer, but I also wanted to improve my processes for de-layering and reverse-engineering complex multi-layer PCBs.

If anything, this repo (and my other Datatrak repositories) are a show of what can happen when a simple project balloons into an obsession.


## How this was done

I had six Locator Mk.2 units, in a variety of conditions. One of them had significant damage to the connectors and metalwork and a dead backup battery. It was this unit I sacrificed to produce this circuit diagram.

### PCB preparation

First the PCB was scanned and photographed on both sides, to produce a straight-on image of the component locations.

The component location and designator print is only present on the top layer. To handle this, I assigned the components on the bottom layer designators with a lower-case "b", e.g. `Ub1`.

I removed all the components from the Locator PCB, removed excess solder, then scanned both sides to get the component overlay print.

### PCB de-layering

De-layering was the most laborious part of the process and involved:

  - Sanding off the solder mask and overlay print from both sides
  - Scanning the top and bottom copper layers (layers 1 and 4)
  - Sanding through the fibreglass and down to the inner layers on both sides
  - Scanning the two inner copper layers (layers 2 and 3).

### Reverse engineering to schematic

I imported the four layers and the component overlay into GIMP and enhanced them to produce a binary black-and-white image, or as close as I could get. Once I had this, I used "Select Colour" to select the background, and made it transparent. I repeated this for all four layers.

Next I re-coloured the copper layers to make them more distinct:

  - Top overlay: white
  - Top copper (layer 1): red
  - Power plane (layer 2): yellow
  - Ground plane (layer 3): green
  - Bottom copper (layer 4): blue

I added a solid black layer as the bottom layer, then adjusted the layer transparency and blending modes to get the best image.

To create the schematic, I added a layer mask to each of the copper track layers (layers 1, 2 and 4). Layer 3 was a solid ground plane which I left unmasked.

As I traced each track and entered it into Kicad, I drew on the layer mask in black. This had the effect of hiding the track from the overall view. Adjusting layer opacity, blending modes and hiding/showing layers made it relatively easy (albeit tedious) to follow the traces around the PCB.

Once the design was in KiCad, I entered parts of it in LTSPICE and modelled them to get an idea how the circuitry (especially the LF receiver) behaved.


