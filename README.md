# PINN-2D-PDE-Solver

> A high-precision Physics-Informed Neural Network (PINN) solver based on deep fully-connected layers for solving 2D partial differential equations.

## 📖 项目简介
本项目实现了一个基于**深度全连接神经网络 (Deep MLP)** 的物理信息神经网络 (PINN) 求解器，专门用于解决**二维偏微分方程 (2D PDEs)**。

项目采用标准的 PINN 架构，通过自动微分技术将物理方程嵌入损失函数，无需大量标注数据即可实现高精度的数值求解。代码结构清晰，适合作为二维场问题（如热传导、静电场、流体力学）的研究基准。

## 🔬 核心方法
### 1. 网络架构
- **输入层**: 二维空间坐标 $(x, y)$
- **隐藏层**: 6层全连接网络 (Fully-Connected Layers)，每层包含 50 个神经元
- **激活函数**: Tanh (保证高阶可微性，便于计算二阶导数)
- **输出层**: 物理量预测值 $u(x, y)$

### 2. 损失函数设计
总损失由物理残差与边界条件组成：
$$ L_{total} = L_{PDE} + \lambda_{BC} L_{BC} $$
- $L_{PDE}$: 偏微分方程残差损失
- $L_{BC}$: 狄利克雷/诺伊曼边界条件损失

## 🚀 快速开始
### 环境依赖
```bash
pip install torch numpy matplotlib
