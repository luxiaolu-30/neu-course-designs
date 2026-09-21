# machine_learn

机器学习学习笔记与 Demo 仓库 —— 记录机器学习课程练习和自学过程中编写的代码示例。

---

## 目录结构

```
machine_learn/
└── basic/                         # 基础机器学习 Demo
    ├── 线性回归/                   # 线性回归（吴恩达课程笔记 + 练习）
    │   ├── linear_regression.ipynb     # 主 Notebook
    │   ├── 吴恩达_*.ipynb              # 吴恩达课程各专题笔记
    │   ├── ex1data*.txt                # 练习数据集
    │   └── lab_utils_*.py              # 课程工具函数
    │
    ├── 逻辑回归/                   # 逻辑回归
    │   ├── logistic_regression.ipynb   # 主 Notebook
    │   ├── ex2data*.txt                # 练习数据集
    │   └── sample_for_scipy.optimize.minimize.ipynb  # SciPy 优化示例
    │
    ├── 梯度上升/                   # 梯度提升（LightGBM）
    │   └── lightgbm.ipynb              # LightGBM 示例
    │
    ├── 图像分类/                   # 图像分类
    │   └── 图像分类.ipynb              # CNN 图像分类 Demo
    │
    ├── 文本分类/                   # 文本分类
    │   └── 文本分类.ipynb              # NLP 文本分类 Demo
    │
    └── 正则化/                     # 正则化与模型评估
        └── 过拟合和欠拟合.py           # 过拟合/欠拟合演示（TensorFlow/Keras）
```

---

## 主题说明

### 线性回归

涵盖单变量与多变量线性回归、代价函数、梯度下降、特征缩放、多项式回归等内容。数据来自吴恩达机器学习课程的编程练习。

### 逻辑回归

二分类逻辑回归实现，包括决策边界、正则化、以及使用 `scipy.optimize.minimize` 进行优化求解。

### 梯度提升

使用 LightGBM 实现梯度提升树模型。

### 图像分类

基于深度学习的图像分类 Demo（CNN 架构）。

### 文本分类

自然语言处理文本分类 Demo。

### 正则化

使用 TensorFlow/Keras 演示过拟合与欠拟合现象，以及 L2 正则化、Dropout 等缓解方法。

---

## 运行环境

```bash
# 创建虚拟环境
python -m venv .venv
.venv\Scripts\activate          # Windows
# source .venv/bin/activate    # macOS/Linux

# 安装依赖
pip install numpy pandas matplotlib scipy jupyter
pip install tensorflow          # 图像分类、文本分类、正则化
pip install lightgbm            # 梯度提升
```

---

## 启动 Jupyter

```bash
cd basic
jupyter notebook
```

---

## 数据来源

- `ex1data*.txt`、`ex2data*.txt` —— 吴恩达机器学习课程编程作业数据集
