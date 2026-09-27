## 🖼️ 核心框架与验证策略 (Framework & Validation Strategy)

本项目的核心在于构建高精度的物理约束网络与严谨的验证体系。

### 1. PINN 基础架构实现
基于 PyTorch 自动微分机制 (`torch.autograd.grad`)，构建了包含输入层、隐藏层及输出层的深度全连接神经网络。通过自定义 `PINN` 类封装前向传播与物理损失计算逻辑。

<p align="center">
  < img src="https://raw.githubusercontent.com/amazine7/pinn-conv-2d-pde/main/code/code.png" width="600" alt="PINN代码框架"/>
</p >

### 2. 全域验证点采样框架
为确保模型在计算域内的泛化能力，设计了多尺度验证点生成策略：
- **内部域**：基于网格筛选椭圆外有效区域；
- **边界域**：沿椭圆边界参数化采样；
- **远场域**：随机均匀采样覆盖辐射边界条件。

<p align="center">
  < img src="https://raw.githubusercontent.com/amazine7/pinn-conv-2d-pde/main/figure/figure.png" width="600" alt="全域验证点分布"/>
</p >

---

## 📉 训练收敛性与 Loss 参数分析 (Loss Analysis)

为了评估模型的鲁棒性，我们进行了三组不同配置下的训练实验，重点考察 PDE 残差、边界误差与远场辐射误差的收敛行为。

### 🔹 训练组 1：基准收敛表现 (Baseline)
在此配置下，模型展现了标准的收敛曲线。PDE 残差与边界条件误差同步下降，验证了物理约束的有效性。
<p align="center">
  < img src="https://raw.githubusercontent.com/amazine7/pinn-conv-2d-pde/main/loss/loss1.jpg" width="700" alt="训练组1 Loss曲线"/>
</p >

### 🔹 训练组 2：高精度优化 (High Precision)
通过调整超参数，该组实验进一步降低了远场辐射误差（Radiation MSE），使其达到 $10^{-4}$ 量级，显著提升了无限域外场的求解精度。
<p align="center">
  < img src="https://raw.githubusercontent.com/amazine7/pinn-conv-2d-pde/main/loss/loss2.jpg" width="700" alt="训练组2 Loss曲线"/>
</p >

### 🔹 训练组 3：稳定性与泛化测试 (Stability Test)
此组实验重点测试了模型在复杂边界条件下的稳定性。尽管初期波动较大，但最终各项指标均收敛至稳定区间，证明了算法的鲁棒性。
<p align="center">
  < img src="https://raw.githubusercontent.com/amazine7/pinn-conv-2d-pde/main/loss/loss3.jpg" width="700" alt="训练组3 Loss曲线"/>
</p >
