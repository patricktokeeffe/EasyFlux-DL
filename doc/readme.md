# Supplemental Documentation for EasyFlux-DL CR3000OP

> The following revisions apply to *EasyFlux-DL Instruction Manual For CR3000 and Open-Path Eddy-Covariance System (Revision 03/2018)*.
>
> Online: https://s.campbellsci.com/documents/us/manuals/easyflux-dl.pdf

## 1. Introduction

Make the following additions to the list of supported sensors (in bold):

* Biometeorology (biomet) and energy balance sensors (optional)
    * **03B Cup-and-Vane Anemometer (qty 0 to 1)**<br/>*(Backported from Campbell Scientific pre-EasyFlux OPEC program)*
    * Soil Water Content Reflectometer (qty 0 to 2)
        * CS616
        * CS650
        * CS655
        * **5TM**
        * **TDR310x**
* **Vertical Profile of Soil Sensors (optional)**
    * **Option 1: 5TM (qty 0 to 6)**
    * **Option 2: TDR31x (qty 0 to 6)**
* **GPS Receiver (optional, qty 0 to 1)**
    * **GPS16X-HVS**
* **Enclosure door switch (optional, qty 0 to 1)**
    * **Magnetic reed switch (NO or NC)**
* **Solar charge controller (optional)**
    * **TriStar 45**

## 2. Precautions

Insert this additional note:

* *EasyFlux DL* requires the EC100 to have operating system version 7.01 or newer.

## 3.1 Wiring

### 3.1.8 Soil Water Content 

This version of *EasyFlux DL* supports five models of soil water content reflectometers:
CS616, CS650, CS655, 5TM (METER Group), or TDR3xx (Acclima).
From zero to two of any one model is supported.
The default wiring is shown in Table 3-8.

> **NOTE**<br/>Some early 5TM units may have the older Decagon wiring scheme. 
> The wire colors for older sensors are denoted by an * in Table 3-8.

Add the following rows to **Table 3-8. Default wiring for Soil Water Content Probes**

| Sensor | Quantity | Wire Description | Color | Datalogger terminal |
|:-:|:-:|:-:|:-:|:-:|
| 5TM soil sensor<br />(Addresses 1/2) | 0 to 2 | SDI-12 Data | Orange/Red* | **C5** |
| | | SDI-12 Power | Brown/White* | **+12 V** |
| | | SDI-12 Reference | Bare/Bare* | **G** |
| TDR3xx soil sensor<br />(Addresses 1/2) | 0 to 2 | SDI-12 Data | Blue | **C5** |
| | | SDI-12 Power | Red | **+12 V** |
| | | SDI-12 Reference | White | **G** |

### 3.1.11 Cup-and-Vane Anemometer (new section)

This version of *EasyFlux DL* can support from zero to one MetOne 034B cup-and-vane anemometer.
The default wiring for the cup-and-vane anemometer is shown in Table 3-11.

> **CAUTION**<br/>This sensor requires an input channel which is also used by the NR01 net radiometer.
> The default wiring must be modified before it can support both sensors.

**Table 3-11. Default wiring for Cup-and-Vane Anemometer**

| Sensor | Quantity | Wire Description | Color | Datalogger terminal |
|:-:|:-:|:-:|:-:|:-:|
| 034B Cup-and-Vane Anemometer | 0 or 1 | Wind direction signal | Green | **SE 20** |
| | | Wind direction excitation | Blue | **VX3** |
| | | Wind direction reference | White | **&#x23DA;** |
| | | Wind speed signal | Red | **P2** |
| | | Wind speed reference | Black | **&#x23DA;** |
| | | Shield | Clear | **&#x23DA;** |

### 3.1.12 Vertical Profile Soil Sensors (new section)

This version of *EasyFlux DL* supports two models of soil sensors for vertical profiles:
METER Group (Decagon Devices) 5TM, or Acclima TDR series.
From zero to nine of any one model is supported.
The default wiring shown in Table 3-12 uses the same SDI-12 input channel as soil water content sensors.

To accomodate SDI-12  soil probes for energy balance, default profile sensor quantity is 6 and SDI-12 addresses are 3 to 8.
The maximum number of sensors is 9 using SDI-12 addresses from 1..9, assuming other SDI-12 sensors use higher addresses (`A`, `B`, `C`, ...).
Field names in data output tables contain a numeric index ranging from 1 to \{qty} which corresponds to addresses from low to high.

> **NOTE**<br/>Some early 5TM units may have the older Decagon wiring scheme, which is denoted by an * in Table 3-8.

**Table 3-12. Default Wiring for Vertical Profile Soil Sensors**

| Sensor | Quantity | Wire Description | Color | Datalogger terminal |
|:-:|:-:|:-:|:-:|:-:|
| 5TM soil sensor<br />(Addresses 3..8) | 0 to 6 | SDI-12 Data | Orange/Red* | **C5** |
| | | SDI-12 Power | Brown/White* | **+12 V** |
| | | SDI-12 Reference | Bare/Bare* | **G** |
| TDR3xx soil sensor<br />(Addresses 3..8) | 0 to 6 | SDI-12 Data | Blue | **C5** |
| | | SDI-12 Power | Red | **+12 V** |
| | | SDI-12 Reference | White | **G** |

### 3.1.13 GPS Receiver (new section)

A GPS receiver is optional but will keep the datalogger clock synchronized to GPS time.
If the datalogger clock drifts from the GPS time, then it will be resynchronized.
The default wiring for the GPS receiver is shown in Table 3.13.

> **NOTE**<br/>Units with serial numbers greater than 1A4189318 have a 3 V PPS output signal
> and require a level shifter for the datalogger to recognize the PPS signal. 
> A Campbell Scientific SW12V or A300 can be used for this purpose.

**Table 3-13. Default Wiring for GPS Receiver**

| Sensor | Quantity | Wire Description | Color | Datalogger terminal |
|:-:|:-:|:-:|:-:|:-:|
| GPS16X-HVS | 0 or 1 | PPS | Gray | **C7** |
| | | Tx data | White | **C8** |
| | | Rx data | Blue | **G** |
| | | Shield | Clear | **&#x23DA;** |
| | | Power in | Red | **+12 V** |
| | | Power ground | Black | **G** |
| | | Power enable | Yellow | **G** |

### 3.1.14 Enclosure door switch (new section)

This version of *EasyFlux DL* supports zero or one magnetic reed switch for tracking datalogger enclosure status.
Both normally open and normally-closed switches are supported.
The default wiring for the enclosure door switch is shown in Table 3-14.

**Table 3-14. Default Wiring for Enclosure Door Switch**

| Sensor | Quantity | Wire Description | Color | Datalogger terminal |
|:-:|:-:|:-:|:-:|:-:|
| Enclosure door switch | 0 or 1 | Wire 1 | | **C6** |
| | | Wire 2 | | **5V** |

### 3.1.15 Solar charge  controller (new section)

This version of *EasyFlux DL* supports zero or one solar charge controller: MorningStar TriStar 45.
Operating parameters and state flags for the PV system are aggregated at the same interval as flux outputs. 
The default wiring for the charge controller is shown in Table 3-15.

**Table 3-15. Default Wiring for Solar Charge Controller**

| Sensor | Quantity | Wire Description | Color | Datalogger terminal |
|:-:|:-:|:-:|:-:|:-:|
| TriStar 45 | 0 or 1 | Serial Rx (pin 2) | | **C1** |
| | | Serial Tx (pin 3) | | **C2** |
| | | Serial ground (pin 5) | | **G** |
| | | +5V (DTR/pin 4) | | **5V** |
| | | Ground (RTS/pin 7) | | **G** |

## 4. Operation

### 4.1 Set Constants in *CRBasic Editor* and Load Program

The content in this section of the Instruction Manual applies to this version of *EasyFlux DL*, 
however, several important notes apply:

* Category 3, Sensor Calibration Constants, have been relocated to a separate include file: `constants.cr3`.
* If you use a sensor with unique constants, the include file must be present in the same directory. 
* If no sensors with unique constants are used, the include file is not required.
* In some cases, the corresponding constant in the include file is used to compute the correct program constant.
  **Ensure the values provided match units specified in comments.**

> **NOTE**<br/>The unique constants for sensor quantities remain in the main program file 
> since modifying them results in data table structures changing and a potential loss of data or failure to record new data.

### 4.1.1. Sending the program (new section)

After unique constants are verified, send the include file and program file to the datalogger using *CRBasic Editor* or the *File Control* screen.
Send the include file first, if required, but do not run it; then send the program file and configure run options as desired. 
If the include file has not been modified, it does not need to be resent to the logger before sending an updated program file.

### 4.1.2 Field editing unique constants (new section)

The sensor calibration constants in the include file will be incorporated when the program compiles and begins running. 
Once running, constants become user-editable through the ConstTable menu or data table. 
Only constants for enabled sensors will be shown.
There are two options for modifying the include file:

Option 1, using a remote client (e.g. LoggerLink, LoggerNet or PC400):

1. Connect to the datalogger.
1. Use the Table Monitor to view the *Const_Table* table.
1. Update values, as needed. Be sure values are provided in correct units.
1. When finished, set ApplyAndRestart to True.

Option 2, using the local keyboard display:

1. Open <kbd>System Menu<kbd>&rarr;<kbd>Const Table</kbd>
1. Update values, as needed. Be sure values are provided in correct units.
1. When finished, use Save and Apply to update the program.

A third, older option which is still supported is to 
(a) upload a modified copy of the include file or 
(b) edit the file in-memory using the logger keyboard display,
and then restart the program.

### 4.3 Data Retrieval

> *Note: values provided in Table 4-3. CF Card Fill Times may need slight but negligible downward adjustment due to 
> additional fields stored in the time series and flux output data tables.*

### 4.4.0 Data Dictionaries (new section)

The tables in this chapter follow the conventions of the *EasyFlux DL* Instruction Manual, including the text used for Units.
Many entries contain special characters or otherwise deviate from unit labels present in actual data output files. 

Tables throughout chapter 4 are good for general reference, but users should also utilize the machine-readable metadata files linked below.
These data dictionaries are derived from program-generated data tables and contain the full complement of available fields, not just those related to active sensors.

Files are in tab-separated format with a single header row and the following columns:

1. Field
1. Units
1. Description

| Table(s) | Dictionary file
|:-|:-|
| Time_Series | [datadict-Time_Series.txt](datadict-Time_Series.txt)
| Flux<br/>Flux_Notes | [datadict-Flux.txt](datadict-Flux.txt)
| LTAR_Met<br/>LTAR_Met_1Minute | [datadict-LTAR_Met.txt](datadict-LTAR_Met.txt)

### 4.4 Output tables

Add the following rows to **Table 4-4. Data Output Tables**:

| Table name | Description | Recording interval | Memory on CR3000 CPU | Memory on CF card |
|:-:|:-:|:-:|:-:|:-:|
| LTAR_Met | Processed biomet data | 15 minutes | Auto-Allocate (typically less than 1 hour) | The LTAR_Met table is broken up into 30-day files |
| LTAR_Met_1Minute | Processed biomet data | 1 minute | Auto-Allocate (typically less than 1 hour) | The LTAR_Met_1Minute table is broken up into 30-day files |

For **Table 4-5. Data Fields in the Time_Series Data Output Table**:

| Change Type | Data Field Name | Units | Description | Data Field Included |
|:-:|:-:|:-:|:-:|:-:|
| Insert 1 row after H2O_sig_strgth | CO2_hf | mg m<sup>-3</sup> | CO<sub>2</sub> density output using humidity-corrected sonic temperature | Always |

For **Table 4-7: Data fields in the Flux Data Output Table**:

> **NOTE**<br/>Field names with `(i)` qualifiers will appear with no suffixes if only one sensor is activated.
> This makes creating a data dictionary potentially much more difficult.

Make the following substitutions in the Units column (actual units in output table vs. Instruction Manual):

* `counts` &rarr; `samples`
* `ratio` &rarr; `Fraction`
* `deg` &rarr; `degrees`

And insert or update rows as follows:

| Change Type | Data Field Name | Units | Description | Data Field Included |
|:-:|:-:|:-:|:-:|:-:|
| Update row | tau | (kg m/s)/(m^2 s)<br/>*[reformatted]* | - | - |
| Update row | Td &rarr; Td_Avg<br/>*[misnamed]* | - | - | - |
| Update row | wnd_dir_Std &rarr; std_wnd_dir<br/>*[misnamed]* | - | - | - |
| Insert 4 rows after T_SI111_body_Avg | cupvane_WS_Avg | m/s | Average wind speed from cup-and-vane anemometer | If 034B is used |
| | cupvane_WS_rslt_Avg | m/s | Average wind vector magnitude from cup-and-vane anemometer | If 034B is used |
| | cupvane_WD_rslt_Avg | degrees | Average compass wind direction from cup-and-vane anemometer | If 034B is used |
| | cupvane_WD_csi_Std | degrees | Standard deviation of wind direction from cup-and-vane anemometer | If 034B is used |
| Update row | soil_wtr_T_Avg(i) | ratio &rarr; frac_v_wtr<br/>*[mislabeled]* | - | - |
| Update row | cs65x_wc_Avg(i) | ratio &rarr; frac_v_wtr<br/>*[mislabeled]* | - | - |
| Insert 8 rows after CS65x_tmpr_Avg(i) | tdr31x_wc_Avg(i) | % | Average soil water content for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| | tdr31x_tmpr_Avg(i) | &deg;C | Average soil temperature for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| | tdr31x_E_Avg(i) | unitless | Average soil permittivity for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| | tdr31x_bulkEC_Avg(i) | &micro;S/cm | Average bulk electrical conductivity for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| | tdr31x_poreEC_Avg(i) | &micro;S/cm | Average pore water electrical conductivity for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| | soil_5TM_E_Avg(i) | unitless | Average soil permittivity for each sensor; i identifies which 5TM sensor | If 5TM is used |
| | soil_5TM_tmpr_Avg(i) | &deg;C | Average soil temperature for each sensor; i identifies which 5TM sensor | If 5TM is used |
| | soil_5TM_wc_Avg(i) | frac_v_wtr | Average soil water content for each sensor; i identifies which 5TM sensor | If 5TM is used |
| shf_plate_cal(i) | unitless<br/>*[add missing units]* | - | - | - |
| Insert 8 rows after shf_plate_cal(i) | profile_tdr31x_wc_Avg(i) | % | Average soil water content for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| | profile_tdr31x_tmpr_Avg(i) | &deg;C | Average soil temperature for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| | profile_tdr31x_E_Avg(i) | unitless | Average soil permittivity for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| | profile_tdr31x_bulkEC_Avg(i) | &micro;S/cm | Average bulk electrical conductivity for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| | profile_tdr31x_poreEC_Avg(i) | &micro;S/cm | Average pore water electrical conductivity for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| | profile_5TM_E_Avg(i) | unitless | Average soil permittivity for each sensor; i identifies which 5TM sensor | If 5TM is used |
| | profile_5TM_tmpr_Avg(i) | &deg;C | Average soil temperature for each sensor; i identifies which 5TM sensor | If 5TM is used |
| | profile_5TM_wc_Avg(i) | frac_v_wtr | Average soil water content for each sensor; i identifies which 5TM sensor | If 5TM is used |
| Update row | FP_equation | text &rarr; authors<br/>*[mislabeled]* | - | - |

For **Table 4-7: Data fields in the Flux Data Output Table**:

Make the following substitutions in the Units column (actual units in output table vs. Instruction Manual):

* `counts` &rarr; `samples`
* `ratio` &rarr; `Fraction`
* `deg` &rarr; `degrees`

And insert or update rows as follows:

| Change Type | Data Field Name | Units | Description | Data Field Included |
|:-:|:-:|:-:|:-:|:-:|
| Insert row between d & z0<br/>*[undocumented row]* | roughness_user | m | User entered roughness length; 0 for auto calculation | Always |
| Update row | stability_zL | m/m&rarr;unitless<br/>*[reformatted]* | - | - |
| Update row | iteration_FreqFactor | m&rarr;*None defined<br/>[mislabeled]* | - | - |
| Update row | separation_lag_scan_FW | m&rarr;scans<br/>*[mislabeled]* | - | - |
| Update row | time_const_FW | m&rarr;s<br/>*[mislabeled]* | - | - |
| Update row | MAX_LAG | scans&rarr;*None defined<br/>[mislabeled]* | - | - |
| Update row | FreqFactor_uw_vw | number&rarr;unitless<br/>*[mislabeled]* | - | - |
| Update row | FreqFactor_wTs | number&rarr;unitless<br/>*[mislabeled]* | - | - |
| Update row | FreqFactor_wCO2_wH2O | number&rarr;unitless<br/>*[mislabeled]* | - | - |
| Update row | FreqFactor_wFW | number&rarr;unitless<br/>*[mislabeled]* | - | - |
| Insert 17 rows after Lv | batt_V_Avg | V | Average PV system battery voltage | If TS45 is used |
| | batt_sens_V_Avg | V | Average PV system battery sense voltage | If TS45 is used |
| | array_V_Avg | V | Average PV system array/load voltage | If TS45 is used |
| | charge_I_Avg | A | Average PV system charging current | If TS45 is used |
| | batt_V_slow_Avg | V| Average PV system battery voltage, slow filtered | If TS45 is used |
| | heatsink_T_Avg | &deg;C | Average PV charge controller heatsink temperature | If TS45 is used |
| | batt_T_Avg | &deg;C | Average PV system battery temperature | If TS45 is used |
| | reference_V_Avg | V | Average PV charge controller reference voltage | If TS45 is used |
| | ah_reset | Ah | PV charge controller resettable amp-hour meter | If TS45 is used |
| | ah_total | Ah | PV charge controller total amp-hour meter | If TS45 is used |
| | hourmeter | hr | PV charge controller hourmeter | If TS45 is used |
| | alarm_bits | unitless | PV charge controller alarms (bitfield) | If TS45 is used |
| | fault_bits | unitless | PV charge controller faults (bitfield) | If TS45 is used |
| | dip_num | unitless | PV charge controller DIP switch settings (bitfield) | If TS45 is used |
| | state_num | unitless | PV charge controller control state | If TS45 is used |
| | pwm_duty | unitless | PV charge controller PWM Duty Cycle | If TS45 is used |
| | door_is_open_Hist | | Fraction of time door was open (0-1) | If DOOR is used |
| Update row | process_time_Avg | &micro;s&rarr;ms<br/>*[mislabeled]* | - | - |
| Update row | process_time_Max | &micro;s&rarr;ms<br/>*[mislabeled]* | - | - |
| Update row | buff_depth_Max | number&rarr;scans<br/>*[mislabeled]* | - | - |

Insert new table, **Table 4-9: Data fields in the LTAR_Met output table**:

| Data Field Name | Units | Description | Data Field Included |
|:-:|:-:|:-:|:-:|
| amb_tmpr_Avg | &deg;C | Average ambient temperature from EC100 temperature probe | Always |
| rslt_wnd_spd | m/s | Average horizontal wind speed | Always |
| wnd_dir_compass | deg | Average compass wind direction | Always |
| RH_Avg | % | Average relative humidity | Always |
| Precipitation_Tot | mm | Total precipitation | If TE525mm is used |
| amb_press_Avg | kPa | Average ambient air pressure | Always |
| PAR_density_Avg | &micro;mol/(m<sup>2</sup> s) | Average density of photosynthetic active radiation | If LI190SB is used |
| batt_volt_Avg | volt | Average voltage supplying power to the datalogger | Always |
| panel_tmpr_Avg | ºC | Average temperature of the datalogger wiring panel | Always |
| std_wnd_dir | deg | Standard deviation of wind direction | Always |
| VPD_air | kPa | Average vapor pressure deficit | Always |
| Rn_meas_Avg | W/m<sup>2</sup> | Average net radiation (raw, not corrected for wind) | IF NR_LITE is used |
| e_sat | kPa | Average saturation water vapor pressure | Always |
| e | kPa | Average water vapor pressure | Always |
| tdr31X_wc_Avg(i) | % | Average volumetric soil water content for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| tdr31X_tmpr_Avg(i) | &deg;C | Average soil temperature for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| tdr31x_E_Avg(i) | unitless | Average soil permittivity for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| tdr31x_bulkEC_Avg(i) | &micro;S/cm | Average bulk electrical conductivity for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| tdr31x_poreEC_Avg(i) | &micro;S/cm | Average pore water electrical conductivity for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| Tsoil(i) | ºC | Average soil temperature for each TCAV sensor; i identifies which TCAV sensor | If TCAV is used |
| profile_tdr31X_wc_Avg(i) | % | Average volumetric soil water content for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| profile_tdr31X_tmpr_Avg(i) | &deg;C | Average soil temperature for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| profile_tdr31X_E_Avg(i) | unitless | Average soil permittivity for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| profile_tdr31X_bulkEC_Avg(i) | &micro;S/cm | Average bulk electrical conductivity for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| profile_tdr31X_poreEC_Avg(i) | &micro;S/cm | Average pore water electrical conductivity for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| shf_plate_Avg(i) | W/m<sup>2</sup> | Average soil heat flux; i identifies which sensor | If HFP or HFP01SC is used |
| shf_plate_cal(i) | &micro;V/(W m<sup>2</sup>) | Coefficients found from the HFP01SC self-calibration and used to calculate shf_plate_Avg(i); i indicates which sensor | If HFP01SC is used |

Insert new table, **Table 4-10: Data fields in the LTAR_Met_1Minute output table**:

| Data Field Name | Units | Description | Data Field Included |
|:-:|:-:|:-:|:-:|
| amb_tmpr_Avg | &deg;C | Average ambient temperature from EC100 temperature probe | Always |
| rslt_wnd_spd | m/s | Average horizontal wind speed | Always |
| wnd_dir_compass | deg | Average compass wind direction | Always |
| RH_Avg | % | Average relative humidity | Always |
| amb_press_Avg | kPa | Average ambient air pressure | Always |
| PAR_density | &micro;mol/(m<sup>2</sup> s) | Average density of photosynthetic active radiation | If LI190SB is used |
| std_wnd_dir | deg | Standard deviation of wind direction | Always |
| VPD_air | kPa | Average vapor pressure deficit | Always |
| Rn_meas_Avg | W/m<sup>2</sup> | Average net radiation (raw, not corrected for wind) | IF NR_LITE is used |
| e_sat | kPa | Average saturation water vapor pressure | Always |
| e | kPa | Average water vapor pressure | Always |
| tdr31X_wc_Avg(i) | % | Average volumetric soil water content for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| tdr31X_tmpr_Avg(i) | &deg;C | Average soil temperature for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| tdr31X_E_Avg(i) | unitless | Average soil permittivity for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| tdr31X_bulkEC_Avg(i) | &micro;S/cm | Average bulk electrical conductivity for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| tdr31X_poreEC_Avg(i) | &micro;S/cm | Average pore water electrical conductivity for each sensor; i identifies which TDR3x sensor | If TDR31X is used |
| Tsoil(i) | ºC | Average soil temperature for each TCAV sensor; i identifies which TCAV sensor | If TCAV is used |
| shf_plate_Avg(i) | W/m<sup>2</sup> | Average soil heat flux; i identifies which sensor | If HFP01 or HFP01SC is used |
| shf_plate_cal(i) | &micro;V/(W m<sup>2</sup>) | Coefficients found from the HFP01SC self-calibration and used to calculate shf_plate_Avg(i); i indicates which sensor | If HFP01SC is used |

Insert new table, **Table 4-11: Data fields in the Cal_Constants output table**:

| Data Field Name | Units | Description | Data Field Included |
|:-:|:-:|:-:|:-:|
| CUPVANE_AZIMUTH | degrees | Azimuth angle of windset w.r.t. True North | If 034B is used |
| NRLITE_SENS | &micro;V/W/m<sup>2</sup> | Sensitivity for NR Lite2 net radiometer | If NR_LITE is used |
| NR01_SW_IN_SENS | &micro;V/W/m<sup>2</sup>| Sensitivity for NR01 shortwave downwelling radiation | If NR01 is used |
| NR01_SW_OUT_SENS | &micro;V/W/m<sup>2</sup> | Sensitivity for NR01 shortwave upwelling radiation | If NR01 is used |
| NR01_LW_IN_SENS | &micro;V/W/m<sup>2</sup> | Sensitivity for NR01 longwave downwelling radiation | If NR01 is used |
| NR01_LW_OUT_SENS | &micro;V/W/m<sup>2</sup> | Sensitivity for NR01 longwave upwelling radiation | If NR01 is used |
| CNR4_SW_IN_SENS | &micro;V/W/m<sup>2</sup>| Sensitivity for CNR4 shortwave downwelling radiation | If CNR4 is used |
| CNR4_SW_OUT_SENS | &micro;V/W/m<sup>2</sup> | Sensitivity for CNR4 shortwave upwelling radiation | If CNR4 is used |
| CNR4_LW_IN_SENS | &micro;V/W/m<sup>2</sup> | Sensitivity for CNR4 longwave downwelling radiation | If CNR4 is used |
| CNR4_LW_OUT_SENS | &micro;V/W/m<sup>2</sup> | Sensitivity for CNR4 longwave upwelling radiation | If CNR4 is used |
| PYRAN_MULT | W/m<sup>2</sup>/mV | Multiplier for pyranometer | If LI200X or CS300 is used |
| PYRAN_OFFSET | W/m<sup>2</sup> | Offset for pyranometer | If LI200X or CS300 is used |
| QUANTUM_MULT | &micro;mol/(s m<sup>2</sup>)/mV | Multiplier for quantum (PAR) sensor | If LI190SB is used |
| QUANTUM_OFFSET | &micro;mol/(s m<sup>2</sup>) | Offset for quantum (PAR) sensor | If LI190SB is used |
| SI111_m0 |  | Calibration m0 for SI-111 | If SI111 is used |
| SI111_m1 |  | Calibration m1 for SI-111 | If SI111 is used |
| SI111_m2 |  | Calibration m2 for SI-111 | If SI111 is used |
| SI111_b0 |  | Calibration b0 for SI-111 | If SI111 is used |
| SI111_b1 |  | Calibration b1 for SI-111 | If SI111 is used |
| SI111_b2 |  | Calibration b2 for SI-111 | If SI111 is used |
| SHFP_1_SENS | &micro;V/W/m<sup>2</sup> | Heat flux plate #1 calibration factor | If one HFP01 or HFP01SC is used |
| SHFP_2_SENS | &micro;V/W/m<sup>2</sup> | Heat flux plate #2 calibration factor | If two HFP01 or HFP01SC are used |
| SHFP_3_SENS | &micro;V/W/m<sup>2</sup> | Heat flux plate #3 calibration factor | If three HFP01 or HFP01SC are used |
| SHFP_4_SENS | &micro;V/W/m<sup>2</sup> | Heat flux plate #4 calibration factor | If four HFP01 or HFP01SC are used |


