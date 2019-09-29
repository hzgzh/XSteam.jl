## XSteam for julia
Immigrate By hzgzh Date: 2019-9-29

X Steam for julia is a implementation of the IAPWS IF97 standard formulation immigrate from XSteam for matlab By Magnus Holmgren, www.x-eng.com
The steam tables are free and provided as is.
We take no responsibilities for any errors in the code or damage thereby.
You are free to use, modify and distribute the code as long as authorship is properly acknowledged.
Please notify me at magnus@x-eng.com if the code is used in commercial applications. It
provides accurate data for water and steam and mixtures of water and steam properties from
0 - 1000 bar and from 0 - 2000 deg C.

The initial units of XSteam are SI units as denoted in this document. All functions however
call unit conversion functions so the units can be easily changed. A text file with unit
conversion functions for English units are enclosed with the file.

### Usage
The XSteam code are used in the following way:
* Example: rho_pT(1,200) returns the density at 1 bar and 200°C.


### Introduction

X Steam for matlab is a implementation of the IAPWS IF97 standard formulation. It
provides accurate thermo hydraulic data for water and steam and mixtures of water and
steam in the region:
* 0°C < temperature < 2000°C for
* 0.00611 bar a < pressure < 100 bar a
* 0°C < temperature < 1000°C for
* 0.00611 bar a < pressure < 1000 bar a

For accuracy and further information on IAPWS IF97 formulation, se homepage of the
international association for properties of water and steam (www.iapws.org).

### Unit

|Notation|Quantity|Unit|
|-|-|-|
|T|Temperature|°C|
|p|Pressure|bar|
|h|Enthalpy|kJ/kg|
|v|Specific volume|$m^3/kg$|
|rho|Density|$kg/m^3$|
|s|Specific entropy|kJ/(kg °C)|
|u|Specific internal energy|kJ/kg|
|Cp|Specific isobaric heat capacity|kJ/(kg °C)|
|Cv|Specific isochoric heat capacity|kJ/(kg °C)|
|w|Speed of sound|m/s|
|my|Viscosity|Pa s|
|tc|Thermal Conductivity|W/(m °C)|
|st|Surface Tension|N/m|
|x|Vapour fraction (0-1)|-|
|vx|Vapour Volume Fraction (0-1)|-|

## XSteam functions

### Temperature
|Function|In1|In2|Out|
|-|-|-|-|
|Tsat_p|p||Saturation temperature|
|T_ph|p|H|Temperture as a function of pressure and enthalpy|
|T_ps|p|S|Temperture as a function of pressure and entropy|
|T_hs|h|S|Temperture as a function of enthalpy and entropy|

### Pressure
|Function|In1|In2|Out|
|-|-|-|-|
|psat_T|T||Saturation pressure|
|p_hs|h|s|Pressure as a function of h and s.|
|p_hrho|h|rho|Pressure as a function of h and rho (density).Very unaccurate for solid water region since it's almost incompressible!|

### Enthalpy
|Function|In1|In2|Out|
|-|-|-|-|
|hV_p|p||Saturated vapour enthalpy|
|hL_p|p||Saturated liquid enthalpy|
|hV_T|T||Saturated vapour enthalpy|
|hL_T|T||Saturated liquid enthalpy|
|h_pT| p| T| Entalpy as a function of pressure and temperature.|
|h_ps| p| s| Entalpy as a function of pressure and entropy.|
|h_px| p| x| Entalpy as a function of pressure and vapour fraction|
|h_Tx| T| X| Entalpy as a function of temperature and vapour fraction|
|h_prho| p| rho|Entalpy as a function of pressure and density. Observe for low temperatures (liquid) this equation has 2 solutions.(Not valid!!)|

### Specific volume
|Function|In1|In2|Out|
|-|-|-|-|
|vV_p| p|| Saturated vapour volume|
|vL_p| p|| Saturated liquid volume|
|vV_T| T|| Saturated vapour volume|
|vL_T| T|| Saturated liquid volume|
|v_pT| p| T|Specific volume as a function of pressure and temperature.|
|v_ph| p| h| Specific volume as a function of pressure and enthalpy|
|v_ps| p| s| Specific volume as a function of pressure and entropy.|

### Density
|Function|In1|In2|Out|
|-|-|-|-|
|rhoV_p| p|| Saturated vapour density|
|rhoL_p| p|| Saturated liquid density|
|rhoV_T| T|| Saturated vapour density|
|rhoL_T| T|| Saturated liquid density|
|rho_pT| p| T| Density as a function of pressure and temperature.|
|rho_ph| p| h| Density as a function of pressure and enthalpy|
|rho_ps| p| s| Density as a function of pressure and entropy.|

### Specific entropy
|Function|In1|In2|Out|
|-|-|-|-|
|sV_p| p|| Saturated vapour entropy|
|sL_p| p|| Saturated liquid entropy|
|sV_T| T|| Saturated vapour entropy|
|sL_T| T|| Saturated liquid entropy|
|s_pT|p| T|Specific entropy as a function of pressure and temperature(Returns saturated vapour entalpy if mixture.)|
|s_ph| p| h|Specific entropy as a function of pressure and enthalpy|

 ### Specific internal energy
 |Function|In1|In2|Out|
 |-|-|-|-|
 |uV_p| p|| Saturated vapour internal energy|
|uL_p| p|| Saturated liquid internal energy|
|uV_T| T|| Saturated vapour internal energy|
|uL_T| T|| Saturated liquid internal energy|
|u_pT|p| T|Specific internal energy as a function of pressure and temperature.|
|u_ph|p| h|Specific internal energy as a function of pressure and enthalpy|
|u_ps|p| s|Specific internal energy as a function of pressure and entropy.|

### Specific isobaric heat capacity
|Function|In1|In2|Out|
|-|-|-|-|
|CpV_p| p||Saturated vapour heat capacity|
|CpL_p| p|| Saturated liquid heat capacity|
|CpV_T| T|| Saturated vapour heat capacity|
|CpL_T| T|| Saturated liquid heat capacity|
|Cp_pT|p| T|Specific isobaric heat capacity as a function of pressure and temperature.|
|Cp_ph|p| h|Specific isobaric heat capacity as a function of pressure and enthalpy|
|Cp_ps|p| s|Specific isobaric heat capacity as a function of pressure and entropy.|

### Specific isochoric heat capacity
|Function|In1|In2|Out|
|-|-|-|-|
|CvV_p| p|| Saturated vapour isochoric heat capacity|
|CvL_p| p|| Saturated liquid isochoric heat capacity|
|CvV_T| T|| Saturated vapour isochoric heat capacity|
|CvL_T| T|| Saturated liquid isochoric heat capacity|
|Cv_pT|p| T|Specific isochoric heat capacity as a function of pressure and temperature.|
|Cv_ph|p| h|Specific isochoric heat capacity as a function of pressure and enthalpy|
|Cv_ps|p| s|Specific isochoric heat capacity as a function of pressure and entropy.|

### Speed of sound
|Function|In1|In2|Out|
|-|-|-|-|
|wV_p| p|| Saturated vapour speed of sound|
|wL_p| p|| Saturated liquid speed of sound|
|wV_T| T|| Saturated vapour speed of sound|
|wL_T| T|| Saturated liquid speed of sound|
|w_pT|p| T|Speed of sound as a function of pressure and temperature.|
|w_ph| p| h| Speed of sound as a function of pressure and enthalpy|
|w_ps| p| s| Speed of sound as a function of pressure and entropy.|

### Viscosity
Viscosity is not part of IAPWS Steam IF97. Equations from "Revised Release on the
IAPWS Formulation 1985 for the Viscosity of Ordinary Water Substance", 2003 are used.
Viscosity in the mixed region (4) is interpolated according to the density. This is not true
since it will be two fases.

|Function|In1|In2|Out|
|-|-|-|-|
|my_pT| p| T| Viscosity as a function of pressure and temperature.|
|my_ph| p| h| Viscosity as a function of pressure and enthalpy|
|my_ps| p| s| Viscosity as a function of pressure and entropy.|

### Thermal Conductivity
Revised release on the IAPS Formulation 1985 for the Thermal Conductivity of ordinary water substance (IAPWS 1998)

|Function|In1|In2|Out|
|-|-|-|-|
|tcL_p| p|| Saturated vapour thermal conductivity|
|tcV_p| p|| Saturated liquid thermal conductivity|
|tcL_T| T| |Saturated vapour thermal conductivity|
|tcV_T| T|| Saturated liquid thermal conductivity|
|tc_pT|p| T|Thermal conductivity as a function of pressure and temperature.|
|tc_ph|p| h|Thermal conductivity as a function of pressure and enthalpy|
|tc_hs| h| s| Thermal conductivity as a function of enthalpy and entropy|

### Surface Tension
IAPWS Release on Surface Tension of Ordinary Water Substance,September 1994

|Function|In1|In2|Out|
|-|-|-|-|
|st_T|T||Surface tension for two phase water/steam as a function of T|
|st_p|p||Surface tension for two phase water/steam as a function of T|

### Vapour fraction
|Function|In1|In2|Out|
|-|-|-|-|
|x_ph|p| h|Vapour fraction for two phase water/steam as a function of T|
|x_ps|p| s|Vapour fraction for two phase water/steam as a function of T|

### Vapour Volume Fraction
Observe that vapour volume fraction is very sensitive. Vapour volume is about 1000 times greater than liquid volume and therefore vapour volume fraction gets close to the accurancy of IAPWS IF-97

|Function|In1|In2|Out|
|-|-|-|-|
|vx_ph|p| h|Vapour volume fraction as a function of pressure and enthalpy|
|vx_ps|p| s|Vapour volume fraction as a function of pressure and entropy.|
