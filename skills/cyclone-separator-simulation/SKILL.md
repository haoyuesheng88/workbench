---
name: cyclone-separator-simulation
description: Use this skill when the user asks to build, set up, or document a cyclone separator CFD simulation in ANSYS Workbench/Fluent. It covers a reusable Stairmand high-efficiency cyclone case, recommended geometry ratios, Fluent setup, and expected outputs such as pressure drop, particle tracks, and separation efficiency.
---

# Cyclone Separator Simulation

Use this skill when the task is to create or organize a cyclone separator simulation case, usually in `ANSYS Workbench + Fluent`.

## What this skill provides

- A reusable `Stairmand high-efficiency` cyclone baseline
- Suggested geometry ratios and one ready-to-use dimension set
- Fluent setup guidance for single-phase swirl and DPM particle separation
- Standard output expectations for reports and plots

## Quick workflow

1. If the user does not give dimensions, use the baseline in [references/stairmand-case.md](references/stairmand-case.md).
2. If the user wants a case package, create a local workspace folder and include:
   - geometry dimensions
   - Fluent setup checklist
   - one schematic or notes file
3. For Fluent:
   - solve the continuous phase first
   - then enable DPM for particle tracking
4. Deliver results in a compact bundle:
   - setup notes
   - key dimensions
   - expected reports and plots

## Default modeling choices

- Solver: pressure-based, steady
- Turbulence: `RSM`
- Gravity: on, axial downward
- Continuous phase: air
- Discrete phase: dust particles with `DPM`
- First pass: one-way coupling

## Read these references when needed

- Geometry and baseline dimensions: [references/stairmand-case.md](references/stairmand-case.md)
- Fluent setup and post-processing: [references/fluent-setup.md](references/fluent-setup.md)

## Output standard

Unless the user asks otherwise, aim to produce:

- a geometry dimension table
- a Fluent setup checklist
- a short explanation of assumptions
- recommended result plots:
  - static pressure
  - velocity vectors or streamlines
  - particle tracks
  - pressure drop
  - separation efficiency

## Notes

- Prefer `RSM` over simpler turbulence models for strong cyclone swirl unless the user explicitly wants a lighter model.
- If the user asks for a fast starter case, keep it at steady single-phase plus DPM.
- If the user asks for higher fidelity, suggest mesh refinement near inlet, vortex finder, and cone tip, plus particle size sweeps.
