Spherical Nanoindentation Simulation: Substrate Size, Indenter Radius, and Force Constant Effects
Overview

This project investigates the critical parameters influencing spherical nanoindentation simulations using Molecular Dynamics (MD). The study focuses on a Nickel (Ni) substrate with a Copper (Cu) base and aims to quantify the effect of:

a.Substrate size

b.Indenter radius

c.Force constant (k)

on the material's mechanical response, specifically:

1.Force vs. Depth curve

2.Hardness (H)

3.Young's Modulus (E)

The simulations were performed using the LAMMPS MD package with the EAM/alloy potential to model interatomic forces.

Simulation Details

System Setup

| Parameter          | Value / Material            | Description                                         |
|-------------------|----------------------------|-----------------------------------------------------|
| Substrate          | Nickel (Ni)               | Primary material being indented                     |
| Base               | Copper (Cu, 1 unit thick) | Rigid, stationary base layer (set force = 0)       |
| Potential          | EAM/alloy                 | Models pairwise interactions between metals/alloys |
| Indenter Type      | Ghost Spherical Indenter  | Indents along the y-direction, centered on substrate |
| Indentation Depth  | Constant (~28 units)      | Maintained across all cases for comparison         |
| Velocity           | Constant                  | Ensures consistent indentation rate                |


Key Simulation Parameters Investigated

1. Effect of Substrate Size

Objective: Investigate how varying substrate dimensions affects mechanical properties with a fixed indenter radius of 15 units.

| Case | Substrate Dimensions (units) | Key Observation |
|------|-----------------------------|----------------|
| 1    | Smallest                    | Highest Hardness. Rigid boundaries restrict atom/dislocation motion → Boundary effect. High load drop on unloading. |
| 2    | Medium                       | Hardness and Young's Modulus decrease. Reduced boundary effect allows more atomic relaxation. |
| 3    | Large                        | Further decrease in Young's Modulus. Force vs. Depth curve shows rapid fluctuations. |
| 4    | Largest                      | Lowest Hardness and Young's Modulus. Smooth curve indicates minimal boundary interference and efficient atomic relaxation. |


Summary: Increasing substrate size reduces Hardness and Young's Modulus due to enhanced atomic/dislocation relaxation and reduced boundary effects, approaching bulk behavior.

2. Effect of Indenter Radius

Objective: Analyze the effect of indenter radius with a fixed large substrate.

| Indenter Radius (r) | Observations |
|--------------------|--------------|
| Increasing r       | Maximum load increases due to larger contact area; deformation becomes tougher. Unloading slope becomes steeper → Young's Modulus increases. |

Summary: Larger indenter radii increase Maximum Load, Hardness, and Young's Modulus because a larger area requires greater force to initiate plastic deformation.

3. Effect of Force Constant (k)

Objective: Study how indenter stiffness affects the indentation response.

| Case | Substrate Size | Indenter Radius | Force Constant (k)     | Observation                                      |
|------|----------------|----------------|-----------------------|-------------------------------------------------|
| 1    | Small          | 15 units       | High k (100, 10, 1)   | Steep curves, higher forces                     |
| 1    | Small          | 15 units       | Low k (0.1, 0.01)     | Shallow, smooth curves                           |
| 2    | Large          | 30 units       | High k                 | Higher force, less noise than small domain      |
| 2    | Large          | 30 units       | Low k                  | Lower force, smoother response                  |


Conclusion: The force constant profoundly influences the load-depth response. High k → higher forces, potential numerical artifacts. Low k → underestimation of mechanical properties. Appropriate selection of k is essential for realistic results.

Calculations Used

Hardness (H)

𝐻=Load applied/Contact Area

where contact area is related to the indenter diameter and maximum indentation depth

Young's Modulus (E)

Calculated from the slope of the unloading curve in the Force vs. Depth plot using Linear Regression(sklearn Model).

Unit Conventions (LAMMPS Metal Units)

| Quantity | Metal Units | SI Units Approx. |
|----------|------------|-----------------|
| Length   | Å (angstrom) | 1 Å = 1×10⁻¹⁰ m |
| Mass     | amu          | 1 amu ≈ 1.66×10⁻²⁷ kg |
| Energy   | eV           | 1 eV ≈ 1.60×10⁻¹⁹ J |
| Force    | eV/Å         | 1 eV/Å ≈ 1.60×10⁻⁹ N |

