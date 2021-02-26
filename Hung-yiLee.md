# 1/9

Local Explanation  解释如何对单个样例做出决策

Global Explanation  解释会基于哪些原因如何做出各种决策的

模型诊断 机器学到了什么

参考观点

完全解释是不必要的 类似人类大脑

目标：让人觉得有道理 可信

# 2/9  Local Explanation

X={X_1, X_2, ..., X_N}

知道 X_i 对最终决策结果的重要性


dY/dX_i


参考文献

Grad_CAM 1610.02391

SmoothGrad 1706.03825

Layer-wise Relevance Propagation 1604.00825

Guided Backpropagation 1412.6806

问题

Saturation X_i 的值已经到了导数平滑区间 但实际很重要 (3m是高个子2m也是) 该区域可用于攻击

Noisy X_i 的导数不光滑

相关工作

Vanilla Gradient

DeepLIFT

# 3,4,5/9 global

max activatetion

因为没有约束, 直接求让y_i 最大的X会出现无意义的X

利用GAN训练一个生成器 然后求让y_i最大的Z, 令X = G(Z)  1612.00005

# 6,7,8/9 model explain model

LIME Local interpretable Model-Agnostic Explanations

划块后用线性模型

Dicesion Three

训练一个容易被决策树分析的网络 查阅 1711.06178

# 9/9

Layer-wise Relevance Propagation

LRP 能否用于 residual connection？


Sensitivity








