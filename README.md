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
* winsteam syntax pth(1,200) returns the entalpy at 1bar and 200°C

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
|Tsat_p or pt|p||Saturation temperature|
|T_ph or pht|p|H|Temperture as a function of pressure and enthalpy|
|T_ps or pst|p|S|Temperture as a function of pressure and entropy|
|T_hs or hst|h|S|Temperture as a function of enthalpy and entropy|

### Pressure
|Function|In1|In2|Out|
|-|-|-|-|
|psat_T or tp|T||Saturation pressure|
|p_hs or hsp|h|s|Pressure as a function of h and s.|
|p_hrho|h|rho|Pressure as a function of h and rho (density).Very unaccurate for solid water region since it's almost incompressible!|

### Enthalpy
|Function|In1|In2|Out|
|-|-|-|-|
|hV_p or pqh(p,1)|p||Saturated vapour enthalpy|
|hL_p or pqh(p,0)|p||Saturated liquid enthalpy|
|hV_T or tqh(t,1)|T||Saturated vapour enthalpy|
|hL_T or tqh(t,0)|T||Saturated liquid enthalpy|
|h_pT or pth| p| T| Entalpy as a function of pressure and temperature.|
|h_ps or psh| p| s| Entalpy as a function of pressure and entropy.|
|h_px or pqh| p| x| Entalpy as a function of pressure and vapour fraction|
|h_Tx or tqh| T| X| Entalpy as a function of temperature and vapour fraction|
|h_prho| p| rho|Entalpy as a function of pressure and density. Observe for low temperatures (liquid) this equation has 2 solutions.(Not valid!!)|

### Specific volume
|Function|In1|In2|Out|
|-|-|-|-|
|vV_p or pqv(p,1)| p|| Saturated vapour volume|
|vL_p or pqv(p,0)| p|| Saturated liquid volume|
|vV_T or tqv(p,1)| T|| Saturated vapour volume|
|vL_T or tqv(p,0)| T|| Saturated liquid volume|
|v_pT or ptv| p| T|Specific volume as a function of pressure and temperature.|
|v_ph or phv| p| h| Specific volume as a function of pressure and enthalpy|
|v_ps or psv| p| s| Specific volume as a function of pressure and entropy.|

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
|sV_p or pqs(p,1)| p|| Saturated vapour entropy|
|sL_p or pqs(p,0)| p|| Saturated liquid entropy|
|sV_T or tqs(p,1)| T|| Saturated vapour entropy|
|sL_T or tqs(p,0)| T|| Saturated liquid entropy|
|s_pT or pts|p| T|Specific entropy as a function of pressure and temperature(Returns saturated vapour entalpy if mixture.)|
|s_ph or phs| p| h|Specific entropy as a function of pressure and enthalpy|

 ### Specific internal energy
 |Function|In1|In2|Out|
 |-|-|-|-|
|uV_p or pqu(p,1)| p|| Saturated vapour internal energy|
|uL_p or pqu(p,0)| p|| Saturated liquid internal energy|
|uV_T or tqu(t,1)| T|| Saturated vapour internal energy|
|uL_T or tqu(t,0)| T|| Saturated liquid internal energy|
|u_pT or ptu|p| T|Specific internal energy as a function of pressure and temperature.|
|u_ph or phu|p| h|Specific internal energy as a function of pressure and enthalpy|
|u_ps or psu|p| s|Specific internal energy as a function of pressure and entropy.|

### Specific isobaric heat capacity
|Function|In1|In2|Out|
|-|-|-|-|
|CpV_p or pqc(p,1)| p||Saturated vapour heat capacity|
|CpL_p or pqc(p,0)| p|| Saturated liquid heat capacity|
|CpV_T or tqc(t,1)| T|| Saturated vapour heat capacity|
|CpL_T or tqc(t,0)| T|| Saturated liquid heat capacity|
|Cp_pT or ptc|p| T|Specific isobaric heat capacity as a function of pressure and temperature.|
|Cp_ph phc|p| h|Specific isobaric heat capacity as a function of pressure and enthalpy|
|Cp_ps psc|p| s|Specific isobaric heat capacity as a function of pressure and entropy.|

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
|wV_p or pqw(p,1)| p|| Saturated vapour speed of sound|
|wL_p or pqw(p,0)| p|| Saturated liquid speed of sound|
|wV_T or tqw(t,1)| T|| Saturated vapour speed of sound|
|wL_T or tqw(t,0)| T|| Saturated liquid speed of sound|
|w_pT or ptw|p| T|Speed of sound as a function of pressure and temperature.|
|w_ph phw| p| h| Speed of sound as a function of pressure and enthalpy|
|w_ps psw| p| s| Speed of sound as a function of pressure and entropy.|

### Viscosity
Viscosity is not part of IAPWS Steam IF97. Equations from "Revised Release on the
IAPWS Formulation 1985 for the Viscosity of Ordinary Water Substance", 2003 are used.
Viscosity in the mixed region (4) is interpolated according to the density. This is not true
since it will be two fases.

|Function|In1|In2|Out|
|-|-|-|-|
|my_pT or ptm| p| T| Viscosity as a function of pressure and temperature.|
|my_ph or phm| p| h| Viscosity as a function of pressure and enthalpy|
|my_ps or psm| p| s| Viscosity as a function of pressure and entropy.|
|pqm|p|q| Viscosity as a function of pressure and quality.|

### Thermal Conductivity
Revised release on the IAPS Formulation 1985 for the Thermal Conductivity of ordinary water substance (IAPWS 1998)

|Function|In1|In2|Out|
|-|-|-|-|
|tcL_p or pqk(p,1)| p|| Saturated vapour thermal conductivity|
|tcV_p or pqk(p,0)| p|| Saturated liquid thermal conductivity|
|tcL_T or tqk(t,1)| T||Saturated vapour thermal conductivity|
|tcV_T or tqk(t,0)| T|| Saturated liquid thermal conductivity|
|tc_pT or ptk|p| T|Thermal conductivity as a function of pressure and temperature.|
|tc_ph or phk|p| h|Thermal conductivity as a function of pressure and enthalpy|
|tc_hs or hsk|h| s| Thermal conductivity as a function of enthalpy and entropy|

### Surface Tension
IAPWS Release on Surface Tension of Ordinary Water Substance,September 1994

|Function|In1|In2|Out|
|-|-|-|-|
|st_T|T||Surface tension for two phase water/steam as a function of T|
|st_p|p||Surface tension for two phase water/steam as a function of T|

### Vapour fraction
|Function|In1|In2|Out|
|-|-|-|-|
|x_ph or phq|p| h|Vapour fraction for two phase water/steam as a function of T|
|x_ps or psq|p| s|Vapour fraction for two phase water/steam as a function of T|

### Vapour Volume Fraction
Observe that vapour volume fraction is very sensitive. Vapour volume is about 1000 times greater than liquid volume and therefore vapour volume fraction gets close to the accurancy of IAPWS IF-97

|Function|In1|In2|Out|
|-|-|-|-|
|vx_ph|p| h|Vapour volume fraction as a function of pressure and enthalpy|
|vx_ps|p| s|Vapour volume fraction as a function of pressure and entropy.|
