# Voron V0.2990

![Voron V0.2990](images/cover.jpg)

[Browse the Fly Gemini V3 and BTT M8P configurations and OrcaSlicer profile](code/)

## Overview

Ever since I began researching 3D printing during my sophomore year of high school, I wanted to build a Voron 3D printer. These machines intrigued me because of the ethos of the organization that creates them. Each machine is unique because there is no official kit: the builder sources all of the parts from a bill of materials and assembles the machine from CAD renderings and a manual.

After finishing the machine, I quickly noticed bottlenecks in the system. I added a series of modifications—most of which I designed—to push the printer further. They are documented below.

**Status:** This project is finished.

## Custom toolhead

The motion system was created for speed, so this printer can move much faster than most machines. An average 3D printer may print around 50–100 mm/s and travel at up to roughly 300 mm/s without issues. On this machine, I reached approximately 225–350 mm/s printing speed and 650 mm/s travel movement without problems.

Although the machine could move extremely fast, the plastic was not melting quickly enough and caused clogs. To solve this, I created a toolhead using a different extruder and a hotend with a larger melt zone. The extruder can supply more current to the stepper motor without excessive heat, and its higher gear ratio provides a better grip on the filament. The hotend increases flow through a larger heat zone and a nozzle that expands the internal contact surface while providing a larger exit for the filament.

Together, these changes produced a major increase in flow rate and allowed the printer to lay down layers at speeds beyond what the unmodified motion system could practically achieve. The toolhead frame is completely 3D printed.

![Custom Voron toolhead CAD render](images/custom-toolhead-render.jpg)

## Auxiliary cooling fan

The auxiliary fan provides extra part cooling without adding weight to the gantry. This allows the printer to use a lighter toolhead because larger, heavier fans are not needed on the moving assembly. The fan is a 12032 grille fan.

![Voron auxiliary cooling fan](images/auxiliary-cooling.jpg)

## Active carbon filter

The carbon filter allows volatile organic compounds released by hazardous filaments to bind to the carbon inside the filter. A 5015 blower directs chamber air through the filter.

![Voron active carbon filter](images/carbon-filter.jpg)

## Chamber temperature sensor

I reused a spare thermistor from a previous hotend and designed a mount that positions it at the top of the printer's internal frame for accurate chamber-temperature readings.

![Voron chamber temperature sensor](images/chamber-sensor.jpg)

## Camera mount and AI integration

Because I cannot constantly babysit the printer, I added a camera to the machine and integrated its stream into the web interface. An open-source script uses the camera to record prints, create timelapses and photos, and automatically pause a print if it detects a failure.

![Voron camera mount](images/camera-mount.jpg)

## Filament runout sensor

The filament runout sensor prevents user error when estimating whether a spool contains enough material to finish a print. The pre-made sensor uses an encoder and limit switch to determine whether filament is present and feeding into the extruder at the expected rate. It is mounted on the back of the printer above the rear door.

![Voron filament runout sensor](images/filament-runout-sensor.jpg)

## Semi-custom RGB panels and hinges

After approximately 200 print hours, the 3D-printed hinges on the front door snapped. I modified a design by [Leiwandizer](https://www.printables.com/model/306742-voron-v0-door-hinges/files) by enlarging the internal holes for longer M3 heat-set inserts. These hinges use the bolt as the pivot point instead of as the rotating surface.

I also created clips that fit over the edges of the new doors and cover the sharp panel edges. The same hinge modification was copied to the back of the machine for easier electronics access. During this upgrade, I replaced one side panel with smoked acrylic and installed an RGB panel behind it to diffuse the light, making the printer chamber more visible on camera.

<p>
  <img src="images/rgb-panel-design.jpg" alt="Voron RGB panel design" width="49%">
  <img src="images/rgb-panel.jpg" alt="Voron RGB panel" width="49%">
</p>

## Mini12864 V2.0 screen mount

The printer's original screen was extremely small and difficult to use, so I replaced it with a larger, programmable Mini12864 LCD. I designed a completely 3D-printed mount that places the display at the bottom of the machine under the front door.

![Voron Mini12864 screen mount](images/screen-mount.jpg)

## Electronics DIN rail mount

The replacement motherboard did not have the same form factor as the original, so the mounting holes in the acrylic electronics plate were incompatible. I created a DIN rail mount that bolts the rail between the rear frame extrusions through a 3D-printed adapter. A second printed mount attaches to the motherboard and slots onto the rail.

<p>
  <img src="images/din-rail-render.jpg" alt="Voron DIN rail mount render" width="49%">
  <img src="images/electronics-bay.jpg" alt="Voron electronics bay" width="49%">
</p>

## Back door

Because I frequently modify this machine, I made a hinged back door that provides access to the electronics bay without unbolting the entire panel. The door incorporates a Noctua fan for motherboard cooling, a small 3D-printed frame, and the hinges.

![Voron electronics bay back door](images/back-door.jpg)
