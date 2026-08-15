<div align="center">

# ZeroG Hydra

### Large-format CoreXY platform with 3-point automated bed tramming and Beacon eddy-current probing

[![Status](https://img.shields.io/badge/Status-Complete-22c55e?style=flat-square)](#project-overview)
[![Firmware](https://img.shields.io/badge/Firmware-Klipper-6f42c1?style=flat-square&logo=klipper&logoColor=white)](code/)
[![Slicer](https://img.shields.io/badge/Slicer-OrcaSlicer-0078d4?style=flat-square)](code/)
[![Kinematics](https://img.shields.io/badge/Kinematics-CoreXY-0a7f5a?style=flat-square)](#corexy-motion-system)
[![Parent](https://img.shields.io/badge/Lab-3D_Printer_Lab-111111?style=flat-square)](../)

<picture>
  <img src="images/cover.jpg" alt="ZeroG Hydra" width="820" draggable="false">
</picture>

A custom large-format Mercury/Hydra CoreXY machine engineered for dimensional consistency, sensor-rich toolhead monitoring, and automated bed calibration.

<strong>Quick navigation:</strong><br>
[Project Overview](#project-overview) | [Motion & Bed Tramming](#corexy-motion-system) | [Filametrix Toolhead](#modernized-toolhead) | [Sensor Stack](#toolhead-sensors) | [Configurations](code/) | [Back to Lab](../)

</div>

---

## Project Overview

Unlike speed-focused builds that compromise surface finish, the ZeroG Hydra was built as a reliable manufacturing workhorse. Designed around high-accuracy sensors and a rigid CoreXY frame, the printer achieves precise first-layer calibration across a large build area.

| Machine Specification | Configuration & Details |
| --- | --- |
| Kinematic architecture | CoreXY with stationary dual-stepper drive |
| Bed leveling system | True 3-point kinematic floating bed with independent Z steppers |
| Probing & resonance | Beacon eddy-current surface sensor + integrated accelerometer |
| Extruder & hotend | Voron Clockwork 2 geared extruder + Phaetus Rapido high-flow hotend |
| Toolhead platform | Modified Filametrix with dual optical/mechanical filament sensors & cutter |
| Electronics enclosure | Ventilated under-bed bay with 24 V PSU, USB hub, and 110 V SSR |
| Host & firmware | Klipper on Linux with adaptive bed meshing and RGB status feedback |

## CoreXY Motion System

The CoreXY kinematic layout keeps both primary stepper motors stationary on the rear frame, significantly reducing moving carriage inertia along the Y axis. Belt tensioning paths are symmetrically balanced to ensure orthogonal travel across the entire envelope.

<div align="center">
  <img src="images/corexy-assembly.jpg" alt="ZeroG Hydra CoreXY assembly" width="700">
</div>

## 3-Point Floating Bed Tramming

The build plate floats on three independent spherical-seat pivots driven by dedicated Z steppers. On boot, Klipper probes the three kinematic points with the Beacon sensor, automatically leveling the physical plane of the bed relative to the XY gantry before generating an adaptive high-resolution mesh.

## Electronics Bay

Located directly beneath the heated bed, the ventilated lower compartment houses the primary computing and power distribution hardware.

<div align="center">

| Left Electronics Bay | Right Electronics Bay |
| :---: | :---: |
| <img src="images/electronics-bay-left.jpg" alt="Left side of the ZeroG electronics bay" width="100%"> | <img src="images/electronics-bay-right.jpg" alt="Right side of the ZeroG electronics bay" width="100%"> |

</div>

- **110 V AC Bed Power:** An external solid-state relay (SSR) powers the high-wattage silicone bed heater directly from AC mains for rapid warm-up times.
- **Dedicated Sensor USB Hub:** Isolates CAN/USB communication from the Beacon probe and auxiliary toolhead controllers.

## Modernized Toolhead

The toolhead is based on the [Filametrix](https://github.com/sorted01/Filametrix) platform, integrating an mechanical filament cutter, dual runout sensors, Beacon surface probe, RGB lighting, and an integrated status display.

<div align="center">

| Toolhead Physical Build | Toolhead CAD Model |
| :---: | :---: |
| <img src="images/toolhead-photo.jpg" alt="ZeroG toolhead" width="100%"> | <img src="images/toolhead-render.jpg" alt="ZeroG toolhead CAD render" width="100%"> |

</div>

## Toolhead Sensors

| Sensor | Position | Function |
| --- | --- | --- |
| Primary Runout Sensor | Above CW2 Extruder | Pauses prints immediately upon spool exhaustion |
| Post-Cutter Sensor | Below Filament Cutter | Confirms complete material cut and retraction for multi-material tool changes |
| Beacon Eddy-Current Probe | Adjacent to Nozzle | High-speed non-contact magnetic surface mapping and input-shaping accelerometer |

<div align="center">

| Sensor CAD Layout | Installed Sensor Array |
| :---: | :---: |
| <img src="images/toolhead-sensor-render.jpg" alt="ZeroG toolhead sensor render" width="100%"> | <img src="images/toolhead-sensor-photo.jpg" alt="ZeroG toolhead sensor" width="100%"> |

</div>
