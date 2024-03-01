[![DOI](https://sandbox.zenodo.org/badge/747821333.svg)](https://sandbox.zenodo.org/doi/10.5072/zenodo.32144)

# EasyFlux<sup>&reg;</sup> DL for CR3000

EasyFlux<sup>&reg;</sup> DL is a free CRBasic program by Campbell Scientific for
acquiring data from an open-path eddy-covariance system and computing fluxes of 
carbon dioxide (CO<sub>2</sub>), latent heat (H<sub>2</sub>O), sensible heat and momentum 
using commonly-applied techniques described in the scientific literature. 
More information is available on the project website: 

> EasyFlux<sup>&reg;</sup> DL: Eddy-Covariance Datalogger Program  
> <https://www.campbellsci.com/easyflux-dl>

## Requirements

* CR3000 firmware version &ge; 28.0
    * To use an SN500 component radiometer, requires firmware &ge; 30
* EC100 firmware version &ge; 7.01

## Usage

Refer to the EasyFlux<sup>&reg;</sup> DL CR3000OP [Instruction Manual][#csi-manual]
and the [supplemental documentation file](doc/readme.md) for complete directions,
including sensor wiring, program configuration, data table descriptions and important usage notes. 

### Getting Started

1. Download a program [release][#gh-release] or clone this repo.
1. Update the program file (`EasyFlux-DL.cr3`) according to your particular hardware configuration.
1. Update the include file (`constants.cr3`) with unique sensor-specific calibration values.
1. Push the include file to the datalogger, but do not run it.
1. Push the program file to the datalogger and set to run automatically.
    * Optional: upload the program file as `default.cr3` so it always runs automatically.

[#csi-manual]: https://s.campbellsci.com/documents/us/manuals/easyflux-dl.pdf
[#gh-release]: https://github.com/wsular/EasyFlux-DL/releases/

## Features

### Editable constants

This version of EddyFlux<sup>&reg;</sup> DL is modified to enable field editing of sensor calibration constants using the keyboard display or a remote client (e.g. PC400).
By introducing a ConstTable and custom menu, the unique constants can be modified without editing or uploading program files, which simplifies exchanging sensors during site maintenance.
To facilitate quality-control and post-processing corrections, unique sensor constants are stored in output table *Cal_Constants* each time the program is compiled.


### New hardware support

The supported sensor list is expanded as follows (additions in bold):

* Gas analyzer and sonic anemometer (qty 1)
    * EC150 with CSAT3A
    * IRGASON
* Fine-wire thermocouple (optional, qty 0 to 1)
    * FW05
    * FW1
    * FW3
* Biometeorology (biomet) and energy balance sensors (optional)
    * Temperature/Relative Humidity (RH) Probe (qty 0 to 1)
        * HC2S3
        * HMP155A
    * Radiation measurements
        * Option 1
            * NR Lite2 Net Radiometer (qty 0 to 1)
            * CS300 or LI200x Pyranometer (qty 0 to 1)
            * LI190x Quantum Sensor (qty 0 to 1)
            * SI-111 Infrared Radiometer (qty 0 to 1)
        * Option 2
            * NR01 or CNR4 4-Way Radiometers (qty 0 to 1)
        * **Option 3**
            * **SN500 4-way Radiometer (qty 0 to 1)**
            * CS300 or LI200x Pyranometer (qty 0 to 1)
            * LI190x Quantum Sensor (qty 0 to 1)
            * SI-111 Infrared Radiometer (qty 0 to 1)
    * TE525x Rain gauge (qty 0 to 1))
    * **034B Cup-and-Vane Anemometer (qty 0 to 1)**<br/>*(Backported from Campbell Scientific pre-EasyFlux OPEC program)*
    * TCAV Soil Thermocouple Probe (qty 0 to 2)
    * Soil Water Content Reflectometer (qty 0 to 2)
        * CS616
        * CS650
        * CS655
        * **5TM** ([METER Group](https://metergroup.com/))
        * **TDR31x** ([Acclima](https://acclima.com/))
    * Soil Heat Flux Plates
        * Option 1: HFP01 plates (qty 0 to 4)
        * Option 2: HFP01SC self-calibrating plates (qty 0 to 4)
* **Vertical Profile of Soil Sensors (optional)**
    * **Option 1: 5TM (qty 0 to 6)**
    * **Option 2: TDR31x (qty 0 to 6)**
* **GPS Receiver (optional, qty 0 to 1)**
    * **GPS16X-HVS**
* **Enclosure door switch (optional, qty 0 to 1)**
    * **Magnetic reed switch (generic)**
* **Solar charge controller (optional)**
    * **TriStar 45** ([MorningStar](https://www.morningstarcorp.com/))

### High-frequency CO<sub>2</sub>

This version of *EasyFlux DL* adds the capability to log alternate CO<sub>2</sub> density output using sonic temperature in the time series (high-frequency) output table. 
If enabled, users can specify the alternate CO<sub>2</sub> density be used in flux computations, instead of standard CO<sub>2</sub> density output using slow-response temperature probe.
Using the fast-response temperature measurements from the sonic anemometer compensates for spectroscopic effects during high sensible heat flux regimes
as explained in *Helbig et al. (2016)*.

* CRBasic Program Reference for `EC100`. *Campbell Scientific, Inc.* CR3000.Std.32.04
* Campbell Scientific. *Improved Flux Measurements from Campbell Scientific Open-Path Gas Analyzers: Utilizing Sonic Temperature to Account for Spectroscopic Effects on CO2 Density.* May 23, 2017. Online:
  <https://s.campbellsci.com/documents/us/miscellaneous/Improved-Flux-Measurements-from-Campbell-Scientific-Open-Path-Gas-Analyzers.pdf>
* Helbig, M., et al.: “Addressing a Systematic Bias in Carbon Dioxide Flux Measurements with the EC150 and the IRGASON Open-Path Gas Analyzers”, Agricultural and Forest Meteorol., 228-229 (2016), 349-359. [doi:10.1016/j.agrformet.2016.07.018](https://doi.org/10.1016/j.agrformet.2016.07.018)
* Russell, E.S., et al.: "Adjustment of CO2 flux measurements due to the bias in the EC150 infrared gas analyzer", Agricultural and Forest Meteorol., 276-277 (2019), 107593. [doi:10.1016/j.agrformet.2019.05.024](https://doi.org/10.1016/j.agrformet.2019.05.024)

### Data tables

Several new data tables and changes to existing output data tables are summarized below.
For full details, refer to the [instruction manual supplement](doc/readme.md).

* Time_Series
    * New field `CO2_hf` contains alternate CO<sub>2</sub> density output
* Flux and Flux_Notes
    * New fields for 034B cup-and-vane anemometer
    * New fields for soil water content sensors
    * New fields for vertical profile soil sensors
    * New fields for solar charge controller
    * New field for enclosure door status
* New table: LTAR_Met 
    * Added to satisfy reporting requirements for LTAR Common Observation Repository (CORe)
    * Does averaging on a 15-minute basis
    * Contains basic meteorology (TA, RH, PA, WS, WD, PAR, Rn, precip...) and soil-related data, including heat flux plates and vertical profile sensors
* New table: Cal_Constants
    * Added to track unique sensor calibration values
    * Triggered once during program compilation (due to power-on or program changes)
    * Stores up to 100 records

## License

* The EasyFlux-DL code base is *Copyright (c) 2014, 2015 Campbell Scientific,
  Inc. All rights reserved.* For more details, refer to the official
  [project website](https://www.campbellsci.com/easyflux-dl).
* Original software contributions are licensed under *TBD*
* Supporting documentation is subject to the *TBD* 
