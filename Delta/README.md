# Delta 3D Printer

<p>
  <img src="images/cover-front.jpg" alt="Delta 3D printer front view" width="49%">
  <img src="images/cover-side.jpg" alt="Delta 3D printer side view" width="49%">
</p>

[Browse the printer configurations and macros](code/)

## Overview

Over the summer of 2023, I came up with an idea for a 3D printer: a delta-based machine with closed-loop stepper motors and an effector (delta toolhead) with extremely rapid cooling. This combination could produce extremely fast, consistent, and accurate parts.

The primary issue with a system like this is the complexity of building and programming a delta machine. This style of 3D printer does not use conventional X, Y, and Z axes. Instead, it uses three arms attached to three vertical posts arranged in a triangle. The printer arms can only move vertically, so the three arms move the effector through X, Y, and Z by moving independently. The machine prints within a circular build volume to maximize the surface area the toolhead can reach.

The printer reused the frame, power supply, and solid-state relay for the 110 V bed heater from a pre-existing TEVO Little Monster. I created a custom effector, installed NEMA 17 closed-loop stepper motors, and added a touchscreen and belt tensioners to enable accurate prints without visual issues.

**Status:** This project is finished and the printer has been scrapped.

## Effector V1

The first effector design was a proof of concept to test whether a Bowden extruder would be optimal despite the very long filament path. Because this style of printer needs as little weight as possible on the effector, a Bowden setup seemed best because it removed the extruder's weight from the effector.

However, the long Bowden tube reduced control over the filament because of friction within the tube. This led to inconsistent extrusion and print artifacts. The 5015 fan also had trouble blowing consistent air through the duct because of the curves in the design. The next design therefore used a direct-drive extruder and a more powerful part-cooling fan.

<p>
  <img src="images/effector-v1-render.jpg" alt="Effector V1 CAD render" width="49%">
  <img src="images/effector-v1-alt-render.jpg" alt="Alternate Effector V1 CAD render" width="49%">
</p>

## CPAP fan

Instead of mounting a fan on the printer's toolhead, a CPAP blower was mounted to the back of the printer and used a hose to route airflow to the part-cooling ducts. This lowered the effector's weight and freed space because no fan needed to be installed directly on it.

<p>
  <img src="images/effector-photo.jpg" alt="Delta effector" width="49%">
  <img src="images/printer-photo.jpg" alt="Delta printer and CPAP cooling system" width="49%">
</p>

## Effector V2

The new effector integrated the part-cooling ducts, hotend mount, extruder mount, and bed-leveling probe mount into one part. It supported an automatic bed-leveling probe for calibrating the printer arms, the toolhead's minimum position, and the flatness of the bed.

A direct-drive extruder improved extrusion consistency. A new hotend provided a higher flow rate and faster heating through a more efficient heater, larger melt zone, and bigger nozzle. I also added a CPAP fan to the printer frame and a hose attachment on the hotend.

These upgrades improved print quality, but the effector probe produced inconsistent readings because it was offset from the nozzle. The integrated fan ducts also failed to cool parts properly because they did not concentrate airflow at the nozzle tip.

<p>
  <img src="images/effector-v2-render.jpg" alt="Effector V2 CAD render" width="49%">
  <img src="images/effector-v2-assembly.jpg" alt="Effector V2 assembly" width="49%">
</p>

## Effector V3

For the third effector, I kept the same parts apart from the probe and changed how everything was mounted. I moved the hotend to the bottom of the effector and placed the extruder slightly above it, lowering the system's center of gravity. I also used new fan ducts that concentrated air at the nozzle tip for consistent airflow.

The new probe is a membrane switch that attaches to the nozzle tip, allowing the printer to probe with the nozzle. It is installed whenever calibration is needed and removed afterward.

## Closed-loop stepper motors

Closed-loop stepper motors use an encoder to track the shaft's absolute position, turning the motor into a servo-like system. This allows the printer to run more smoothly, produce less resonance than ordinary stepper motors, and avoid lost steps.

I bolted these motors into the existing NEMA 17 stepper-motor plates. In this build, each motor's PCB interacts with a stepper driver that powers it. The driver mimics an A4988 to receive commands from the motherboard, while the PCB sends information to the motor and uses the encoder to verify the shaft position.

## Touchscreen interface

The printer's touchscreen interface runs on a TFT35. The screen hosts KlipperScreen and provides functionality similar to the web interface used from a computer. It is bolted to the electronics box and can pivot approximately 75 degrees upward and downward. The screen frame is mounted to the existing electronics enclosure.
