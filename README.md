# Finite Strain Viscoelastic - Viscoplastic (VEVP) [^1] Constitutive Law

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC_BY_4.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![MOAMMM](https://img.shields.io/badge/MOAMMM-2ea44f?logo=gitlab)](https://gitlab.uliege.be/moammm/moammmPublic)
[![Fortran - >=77](https://img.shields.io/badge/Fortran->=77-blue?logo=Fortran)](https://fortran-lang.org/en/compilers/)


| Description         | Quantity|
|---------------------|---------|
| Material parameters | 51      |
| Internal variables  | 108     |

## Material Parameters Description

The UMAT implementation uses the material parameters **_in the following order_**:

|No |Description                                      |Parameter                      |Unit         |
|---|-------------------------------------------------|-------------------------------|-------------|
|1  | Power Series Strain Approximation               |      $order$                  |     -       |
|2  | Bulk Modulus                                    |      $K_{\infty}$             |    Pa       |
|3  | Shear Modulus                                   |      $G_{\infty}$             |    Pa       |
|4  | Yield Exponent                                  |      $\alpha$                 |    -        |
|5  | Plastic Poisson Ratio                           |      $\nu_p$                  |    -        |
|6  | Viscoplastic coefficient                        |      $\eta$                   |    Pas      |
|7  | Viscoplasic exponent                            |      $p$                      |    -        |
|8  | Initial Yield Limit - Compression               |      $\sigma_{c0}$            |    Pa       |
|9  | Isotropic Hardening - Compression $H_c=c_0+H_{c}^{0}exp(-h_c\gamma)$   |      $c_0$                    |   -         |
|10 | Isotropic Hardening - Compression               |      $H_{c}^{0}$              |   -         |
|11 | Isotropic Hardening - Compression               |   $h_{c}$                     |   -         |
|12 | Initial Yield Limit - Tension                   |      $\sigma_{t0}$            |    Pa       |
|13 | Isotropic Hardening - Tension $H_t=t_{0}+H_{t}^{0}exp(-h_{t}\gamma)$      |      $t_{0}$                  |   -         |
|14 | Isotropic Hardening - Tension                   |      $H_{t}^{0}$              |   -         |
|15 | Isotropic Hardening - Tension                   |    $h_{t}$                  |   -         |
|16 | Kinematic Hardening Parameter $H_b = h_{b0}+h_{b1}\gamma+h_{b2}\gamma^2$    |      $h_{b0}$                 |   -         |
|17 | Kinematic Hardening Parameter                   |      $h_{b1}$                 |   -         |
|18 | Kinematic Hardening Parameter                   |      $h_{b2}$                 |   -         |
|19 | Bulk Modulus - Maxwell branch 1 [^2]            |      $K_1$                    |    Pa       |
|20 | Bulk Modulus - Maxwell branch 2                 |      $K_2$                    |    Pa       |
|21 | Bulk Modulus - Maxwell branch 3                 |      $K_3$                    |    Pa       |
|22 | Bulk Modulus - Maxwell branch 4                 |      $K_4$                    |    Pa       |
|23 | Bulk Modulus - Maxwell branch 5                 |      $K_5$                    |    Pa       |
|24 | Bulk Modulus - Maxwell branch 6                 |      $K_6$                    |    Pa       |
|25 | Bulk Modulus - Maxwell branch 7                 |      $K_7$                    |    Pa       |
|26 | Bulk Modulus - Maxwell branch 8                 |      $K_8$                    |    Pa       |
|27 | Retardation Time Volumetric - Maxwell Branch 1  |      $k_1$                    |    s        |
|28 | Retardation Time Volumetric - Maxwell Branch 2  |      $k_2$                    |    s        |
|29 | Retardation Time Volumetric - Maxwell Branch 3  |      $k_3$                    |    s        |
|30 | Retardation Time Volumetric - Maxwell Branch 4  |      $k_4$                    |    s        |
|31 | Retardation Time Volumetric - Maxwell Branch 5  |      $k_5$                    |    s        |
|32 | Retardation Time Volumetric - Maxwell Branch 6  |      $k_6$                    |    s        |
|33 | Retardation Time Volumetric - Maxwell Branch 7  |      $k_7$                    |    s        |
|34 | Retardation Time Volumetric - Maxwell Branch 8  |      $k_8$                    |    s        |
|35 | Shear Modulus- Maxwell branch 1 [^2]            |      $G_1$                    |    Pa       |
|36 | Shear Modulus- Maxwell branch 2                 |      $G_2$                    |    Pa       |
|37 | Shear Modulus- Maxwell branch 3                 |      $G_3$                    |    Pa       |
|38 | Shear Modulus- Maxwell branch 4                 |      $G_4$                    |    Pa       |
|39 | Shear Modulus- Maxwell branch 5                 |      $G_5$                    |    Pa       |
|40 | Shear Modulus- Maxwell branch 6                 |      $G_6$                    |    Pa       |
|41 | Shear Modulus- Maxwell branch 7                 |      $G_7$                    |    Pa       |
|42 | Shear Modulus- Maxwell branch 8                 |      $G_8$                    |    Pa       |
|43 | Retardation Time Deviatoric - Maxwell Branch 1  |      $g_1$                    |    s        |
|44 | Retardation Time Deviatoric - Maxwell Branch 2  |      $g_2$                    |    s        |
|45 | Retardation Time Deviatoric - Maxwell Branch 3  |      $g_3$                    |    s        |
|46 | Retardation Time Deviatoric - Maxwell Branch 4  |      $g_4$                    |    s        |
|47 | Retardation Time Deviatoric - Maxwell Branch 5  |      $g_5$                    |    s        |
|48 | Retardation Time Deviatoric - Maxwell Branch 6  |      $g_6$                    |    s        |
|49 | Retardation Time Deviatoric - Maxwell Branch 7  |      $g_7$                    |    s        |
|50 | Retardation Time Deviatoric - Maxwell Branch 8  |      $g_8$                    |    s        |

## Remark

Lines 164-168 have to be uncommented for use in FFTMAD but have to be commented for ABAQUS or cm3Libraries.
If you comment out, then in ABAQUS, use the inp file to set initial values for F_vp.

## Disclaimer

Code related to MOAMMM project
This project has received funding from the European Union’s Horizon 2020 research and innovation programme under grant agreement No 862015.

Views and opinions expressed are however those of the author(s) only and do not necessarily reflect those of the European Union. Neither
the European Union nor the granting authority can be held responsible for them.

[^1]: The finite-strain visco-elastic visco-plastic model follows: "_Nguyen, V. D., Lani, F., Pardoen, T., Morelle, X., & Noels, L. (01 October 2016)._ **A large strain hyperelastic viscoelastic-viscoplastic-damage constitutive model based on a multi-mechanism non-local damage continuum for amorphous glassy polymers.** International Journal of Solids and Structures, 96, 192-216.  [doi:10.1016/j.ijsolstr.2016.06.008](doi:10.1016/j.ijsolstr.2016.06.008)" which can be downloaded [here](https://hdl.handle.net/2268/197898).  
we would be grateful if you could cite this publication in case you use the files

[^2]: The UMAT is hardcoded for **8 Maxwell VE Branches**. If you feel the need for more branches send me an email at <mohibmustafa@gmail.com>.
