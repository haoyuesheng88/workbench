# 旋风分离器模拟案例

这个案例按 `ANSYS Workbench + Fluent` 的常见流程整理，目标是搭一个可复现的 `Stairmand high-efficiency` 旋风分离器 CFD 案例。

## 案例目标

- 观察旋风分离器内部强旋流结构
- 计算压降
- 跟踪颗粒分离轨迹
- 统计颗粒捕集效率

## 文件

- `cyclone_dimensions_stairmand.csv`
- `fluent_setup_checklist.md`
- `cyclone_schematic.svg`

## 建议案例定义

- 类型：三维，气固两相
- 连续相：空气，常温常压
- 离散相：粉尘颗粒，DPM
- 先做单相稳态流场，再叠加颗粒跟踪
- 旋流推荐使用 `Reynolds Stress Model (RSM)`

## 建议几何

这里采用文献里常见的 `Stairmand high-efficiency cyclone` 尺寸，基准直径取 `D = 290 mm`。

- 筒体直径 `D = 290 mm`
- 入口高度 `a = 145 mm`
- 入口宽度 `b = 58 mm`
- 筒体高度 `h = 435 mm`
- 锥段高度 `hc = 725 mm`
- 涡流查找管直径 `De = 145 mm`
- 涡流查找管插入长度 `s = 145 mm`
- 锥底直径 `Dd = 109 mm`
- 入口段长度 `Li = 400 mm`

## 建议边界条件

- 连续相入口：`velocity-inlet = 15 m/s`
- 气体出口：顶端 `pressure-outlet = 0 Pa`
- 颗粒出口：底端 `trap`
- 壁面：`no-slip`
- 粉尘密度：`1500 kg/m^3`
- 颗粒粒径：建议先做 `5, 10, 20, 40 μm` 四组离散注入

## 建议求解流程

1. 在 SpaceClaim 或 DesignModeler 按 CSV 参数建三维几何。
2. 在 Meshing 中做四面体或多面体网格，入口、涡流管和锥底附近加密。
3. Fluent 先跑单相稳态，确认残差和压降收敛。
4. 开启 DPM，做一向耦合颗粒跟踪。
5. 统计颗粒从底部收集与顶部逃逸的比例，得到分离效率。

## 结果输出建议

- 压力云图
- 速度矢量与流线
- 切向速度分布
- 颗粒轨迹图
- 压降 `ΔP`
- 分离效率 `η = trapped / injected`

## 来源

- Ansys Innovation Courses: Cyclone Separator lesson
  - https://innovationspace.ansys.com/courses/courses/fluids-in-industry/lessons/cyclone-separator/
- 公开论文中给出的 Stairmand high-efficiency 尺寸表
  - https://www.mdpi.com/2076-3417/11/12/5342
