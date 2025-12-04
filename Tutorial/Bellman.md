本章介绍强化学习的核心概念**状态值（state value）**及其分析工具**贝尔曼方程（Bellman equation）**。

### 一、状态值（State Value）
- **定义**：从某一状态出发所能获得的**期望回报（expected return）**，记为 \( v_{\pi}(s) \)。
- **意义**：用于评估策略优劣，值越大策略越好。
- **与回报（return）的关系**：在随机系统中，状态值是所有可能轨迹回报的平均值。

### 二、贝尔曼方程（Bellman Equation）
- **作用**：描述各状态值之间的依赖关系，是分析状态值的基本工具。
- **核心形式**：
  \[
  v_{\pi}(s) = \sum_{a} \pi(a|s) \left[ \sum_{r} p(r|s,a) r + \gamma \sum_{s'} p(s'|s,a) v_{\pi}(s') \right]
  \]
  其中 \(\gamma\) 为**折扣率（discount rate）**。
- **矩阵向量形式**：
  \[
  v_{\pi} = r_{\pi} + \gamma P_{\pi} v_{\pi}
  \]
  可通过 \( v_{\pi} = (I - \gamma P_{\pi})^{-1} r_{\pi} \) 求解（闭式解），或通过迭代 \( v_{k+1} = r_{\pi} + \gamma P_{\pi} v_{k} \) 逼近。

### 三、动作值（Action Value）
- **定义**：在状态 \( s \) 下执行动作 \( a \) 后所能获得的期望回报，记为 \( q_{\pi}(s,a) \)。
- **与状态值的关系**：
  - 状态值是其所有可能动作值的加权平均：\( v_{\pi}(s) = \sum_{a} \pi(a|s) q_{\pi}(s,a) \)
  - 动作值可表示为：\( q_{\pi}(s,a) = \sum_{r} p(r|s,a) r + \gamma \sum_{s'} p(s'|s,a) v_{\pi}(s') \)
