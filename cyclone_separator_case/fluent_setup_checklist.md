# Fluent 设置清单

## 1. 通用

- Solver: `Pressure-Based`
- Time: `Steady` 先跑流场
- Velocity Formulation: `Absolute`
- Gravity: `-9.81 m/s^2` 沿轴向向下

## 2. Models

- Energy: `Off` 或先关掉
- Viscous: `Reynolds Stress Model (RSM)`
- Discrete Phase: 单相收敛后再开
- DPM Coupling: `One-way coupling`

## 3. Materials

- Continuous phase: air
- Particle material: generic solid
- Particle density: `1500 kg/m^3`

## 4. Boundary Conditions

- Inlet: `velocity-inlet`
  - Magnitude: `15 m/s`
  - Direction: 按入口通道法向
- Top outlet: `pressure-outlet`
  - Gauge pressure: `0 Pa`
- Dust outlet: 对连续相也可设成 `pressure-outlet`
- Walls: `stationary`, `no-slip`

## 5. DPM

- Injection Type: `surface`
- Injection Surface: inlet
- Diameter set:
  - `5e-6 m`
  - `1e-5 m`
  - `2e-5 m`
  - `4e-5 m`
- Initial velocity: 跟随入口
- BC at top outlet: `escape`
- BC at dust outlet: `trap`
- BC at walls: `reflect` 或按需要改成 `trap`

## 6. Methods

- Pressure-Velocity Coupling: `SIMPLE`
- Gradient: `Least Squares Cell-Based`
- Pressure: `Second Order`
- Momentum: `Second Order Upwind`
- Reynolds Stresses: `Second Order Upwind`

## 7. Initialization

- Hybrid Initialization

## 8. Run

- 单相先迭代 `800-1500` 步
- 看残差和压降是否稳定
- 再开启 DPM 做颗粒轨迹

## 9. Post-processing

- Reports:
  - inlet mass flow
  - outlet mass flow
  - static pressure difference
- Particle summary:
  - trapped at dust outlet
  - escaped at top outlet
- Contours:
  - static pressure
  - axial velocity
  - tangential velocity
- Graphics:
  - pathlines
  - particle tracks

## 10. 你可以直接观察的指标

- 压降是否在合理范围内
- 是否形成外旋向下、内旋向上的双涡结构
- 大颗粒是否主要从底部被捕集
- 小颗粒是否更容易从顶部逃逸
