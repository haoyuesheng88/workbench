# Stairmand Baseline Case

Use this baseline when the user asks for a cyclone separator example and does not provide a geometry.

## Baseline type

- `Stairmand high-efficiency cyclone`
- Base diameter: `D = 290 mm`

## Dimensions

| Parameter | Symbol | Value |
| --- | --- | ---: |
| Cylinder diameter | `D` | `290 mm` |
| Inlet height | `a` | `145 mm` |
| Inlet width | `b` | `58 mm` |
| Cylinder height | `h` | `435 mm` |
| Cone height | `hc` | `725 mm` |
| Vortex finder diameter | `De` | `145 mm` |
| Vortex finder insert length | `s` | `145 mm` |
| Cone tip diameter | `Dd` | `109 mm` |
| Straight inlet length | `Li` | `400 mm` |
| Vortex finder upper length | `Le` | `290 mm` |

## Dimension ratios to D

- `a/D = 0.50`
- `b/D = 0.20`
- `h/D = 1.50`
- `hc/D = 2.50`
- `De/D = 0.50`
- `s/D = 0.50`
- `Dd/D = 0.376`

## Recommended boundaries

- Tangential inlet at the rectangular side inlet
- Clean gas outlet at the vortex finder top outlet
- Dust outlet at the cone bottom outlet
- No-slip walls everywhere else

## Typical starter conditions

- Inlet velocity: `15 m/s`
- Air at ambient conditions
- Particle density: `1500 kg/m^3`
- Particle diameter sweep: `5, 10, 20, 40 um`

## References

- Ansys Innovation Courses cyclone separator lesson:
  - `https://innovationspace.ansys.com/courses/courses/fluids-in-industry/lessons/cyclone-separator/`
- Public paper using Stairmand cyclone geometry:
  - `https://www.mdpi.com/2076-3417/11/12/5342`
