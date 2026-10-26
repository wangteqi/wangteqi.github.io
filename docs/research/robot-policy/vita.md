>2026.7.9
>
>王特起

# VITA的复现记录

## 理论部分

### 研究逻辑

1. 研究背景

    视觉运动模仿学习已经广泛采用生成式策略建模方法，例如 diffusion policy、flow matching policy 和其他动作生成模型。这类方法通过学习动作分布来处理复杂连续控制任务，已经成为机器人视觉运动策略学习的重要方向。VITA 所处的背景是：生成式策略已经有效，但视觉条件动作生成的结构越来越复杂。

2. 研究问题

    现有 diffusion-based 或 flow-matching 视觉运动策略通常从标准噪声分布，例如 Gaussian noise，经过迭代去噪或 flow 过程生成动作；同时还需要额外的视觉条件注入机制，例如 cross-attention、FiLM、AdaLN 等，把图像信息注入动作生成过程。这带来了较高的时间开销、显存开销和模型复杂度。VITA 的 gap 是：**现有生成式视觉动作策略是否过度依赖复杂的噪声采样和 conditioning 机制**。

3. 研究动机

    探索是否可以建立一种更简单、更高效的视觉到动作策略学习范式，在减少噪声采样过程和复杂视觉条件注入机制的同时，仍然保持较强的视觉运动控制性能。

4. 研究方法

    VITA 提出 **Vision-to-Action Flow Matching Policy**，将策略学习建模为从视觉潜变量到动作潜变量的 **noise-free、conditioning-free flow matching** 过程。由于流的起点已经是视觉表征，而不是标准高斯噪声，因此 VITA 可以直接从 latent image 演化到 latent action，减少额外视觉 conditioning 模块，并使用更轻量的结构实现动作生成。

VITA：解决视觉到动作生成策略如何更简单、更高效。