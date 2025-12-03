# 第1章 基础概念

**网格世界示例**

- **状态（State）**：智能体的位置，共9个状态 \( \mathcal{S} = \{s_1, \dots, s_9\} \)。
- **动作（Action）**：包括上、右、下、左、停留，共5个动作 \( \mathcal{A} = \{a_1, \dots, a_5\} \)。
- **目标**：找到从任意初始状态到达目标单元格的策略。


## 状态转移（State Transition）

- 描述从当前状态 \( s \) 执行动作 \( a \) 后进入下一状态 \( s' \) 的过程。
- 可表示为确定转移 \( s \xrightarrow{a} s' \) 或概率转移 \( p(s' \mid s, a) \)。


## 策略（Policy）

- 定义智能体在每个状态下**选择动作**的方式。
- **确定性策略**：每个状态下只选一个动作。
- **随机性策略**：每个状态下按概率分布选择动作。
- 表示为条件概率 \( \pi(a \mid s) \)，满足 \( \sum_a \pi(a \mid s) = 1 \)。
- **表格表示（Tabular Representation）**：适用于有限状态-动作空间。


## 奖励（Reward）

- 环境对智能体执行动作后的反馈，记为 \( r(s, a) \)。
- 设计示例：
  - 撞边界：\( r_{\text{boundary}} = -1 \)
  - 进禁止区：\( r_{\text{forbidden}} = -1 \)
  - 到达目标：\( r_{\text{target}} = +1 \)
  - 其他：\( r_{\text{other}} = 0 \)
- **即时奖励（Immediate Reward）** vs **总奖励（Total Reward）**：决策应基于长期总奖励，而非即时奖励。


## 轨迹、回报与片段（Trajectory, Return, Episode）

- **轨迹**：状态-动作-奖励序列，如 \( s_1 \xrightarrow{a_2} s_2 \xrightarrow{a_3} s_5 \dots \)。
- **回报（Return）**：轨迹中所有奖励之和，用于评估策略。
- **片段（Episode）**：从开始到终止状态的一次完整交互过程。
- **折扣回报（Discounted Return）**：用于无限长轨迹，引入折扣率 \( \gamma \in (0,1) \)：
  \[
  G_t = r_{t+1} + \gamma r_{t+2} + \gamma^2 r_{t+3} + \dots
  \]
  - \( \gamma \) 接近 0：注重近期奖励（短视）。
  - \( \gamma \) 接近 1：注重远期奖励（远视）。


## 马尔可夫决策过程（Markov Decision Process, MDP）

- 强化学习的数学框架，包含以下要素：
  1. **状态空间** \( \mathcal{S} \)
  2. **动作空间** \( \mathcal{A}(s) \)
  3. **奖励集合** \( \mathcal{R}(s,a) \)
  4. **模型**：
     - 状态转移概率 \( p(s' \mid s, a) \)
     - 奖励概率 \( p(r \mid s, a) \)
  5. **策略** \( \pi(a \mid s) \)
  6. **马尔可夫性质（Markov Property）**：下一状态/奖励仅依赖于当前状态与动作，与历史无关：
     \[
     p(s_{t+1} \mid s_t, a_t, \dots) = p(s_{t+1} \mid s_t, a_t)
     \]

- **有限MDP（Finite MDP）**：状态与动作数量有限，是本书主要讨论情形。
- **平稳模型（Stationary Model）**：状态转移与奖励概率不随时间变化。

