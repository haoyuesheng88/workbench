# Fluent Setup

Use this as the default Fluent setup for the cyclone separator starter case.

## Solver

- `Pressure-Based`
- `Steady`
- `Absolute`
- gravity on, axial downward: `-9.81 m/s^2`

## Models

- Energy: off for the basic case
- Turbulence: `Reynolds Stress Model (RSM)`
- DPM: off during initial flow solution, then on for particle tracking

## Materials

- Continuous phase: air
- Particle phase: generic solid
- Particle density: `1500 kg/m^3`

## Boundary conditions

- Inlet: `velocity-inlet`
  - magnitude: `15 m/s`
- Top outlet: `pressure-outlet`
  - gauge pressure: `0 Pa`
- Bottom dust outlet:
  - continuous phase: often `pressure-outlet`
  - particles: `trap`
- Walls: stationary, no-slip

## Discrete phase

- Coupling: one-way
- Injection type: surface from inlet
- Diameters:
  - `5e-6 m`
  - `1e-5 m`
  - `2e-5 m`
  - `4e-5 m`
- Top outlet particle behavior: `escape`
- Bottom outlet particle behavior: `trap`
- Walls: `reflect` unless the user wants wall deposition

## Numerics

- Pressure-velocity coupling: `SIMPLE`
- Gradient: `Least Squares Cell-Based`
- Pressure: `Second Order`
- Momentum: `Second Order Upwind`
- Reynolds stresses: `Second Order Upwind`

## Mesh guidance

- Refine near:
  - tangential inlet
  - vortex finder lip
  - cone tip
- For a starter case, a moderate unstructured mesh is acceptable.
- For better separation predictions, refine swirl core and near-wall zones.

## Recommended outputs

- Pressure contours
- Velocity vectors / streamlines
- Tangential velocity slices
- Particle tracks
- Pressure drop `Delta P`
- Separation efficiency:
  - `eta = trapped / injected`

## Delivery pattern

When packaging a case for the user, provide:

- geometry dimensions
- setup checklist
- key assumptions
- expected result plots and metrics
