# amaz# PINN-Conv 2D PDE Solver

> A Physics-Informed Neural Network (PINN) solver with convolutional layers for solving 2D partial differential equations.

## 📖 项目简介
本项目实现了一个基于**卷积神经网络 (CNN)** 的物理信息神经网络 (PINN) 求解器，专门用于解决**二维偏微分方程 (2D PDEs)**。

与传统的全连接 PINN (MLP-PINN) 不同，本项目利用卷积层提取空间局部特征，旨在提高二维空间场问题（如热传导、流体场）的求解精度与收敛速度。

## 🔬 核心方法
### 1. 网络架构
- **输入层**: 二维坐标网格 $(x, y)$
- **特征提取**: 使用多层卷积层 (Conv2d) 捕捉空间依赖性
- **输出层**: 物理量预测值 $u(x, y)$
- **激活函数**: Tanh / Sigmoid (保证高阶可微性以计算残差)

### 2. 损失函数设计
总损失由物理残差与边界条件组成：
$$ L_{total} = L_{PDE} + \lambda_{BC} L_{BC} + \lambda_{IC} L_{IC} $$
- $L_{PDE}$: 方程残差损失 (Residual Loss)
- $L_{BC}$: 边界条件损失 (Boundary Condition Loss)

## 🚀 快速开始
### 环境依赖
```bash
pip install torch numpy matplotlib scipyine7
