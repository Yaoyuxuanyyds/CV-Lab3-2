<h1 align = 'center'>CNN vs ViT on CIFAR-100<h1/>

​	**本项目分别基于CNN和Transformer架构实现具有相近参数量的图像分类网络（Resnet18 与自定义ViT），并在CIFAR-100数据集上采用相同的训练策略对二者进行训练，同时训练中采用了 CutMix 数据增强策略。**

#### 

#### Requirements:

- Python 3.x
- PyTorch
- torchvision
- NumPy
- Matplotlib
- Jupyter Notebook

#### Install:

1. 克隆仓库:
   ```bash
   git clone https://github.com/your_username/cifar100_classification.git
   cd cifar100_classification
   ```

2. 安装所需软件包:
   ```bash
   pip install -r requirements.txt
   ```



### 数据集准备

下载 CIFAR-100 数据集并将其放置在 `data/cifar-100-python/` 目录下。该目录应包含以下文件：
- `meta`
- `train`
- `test`

***（Google 云盘的完整项目目录中包含了 data 目录）***

### 预训练模型权重

**预训练模型权重位于 Google 云盘的完整 Repo 目录中：**

- `resnet18_Adam_bt-512_lr0.0005_wd-0_e200.pth`: 使用 Adam 优化器、批量大小 512、学习率 0.0005、权重衰减 0、训练 200 个 epoch 的 ResNet18 模型。
- `vit_Adam_bt-512_lr0.0005_wd-0_e200.pth`: 使用相同设置训练的 Vision Transformer 模型。

### 训练

如果想要在本地训练模型，请准备好数据集和依赖按照后直接运行 `Lab3-2.ipynb` Jupyter Notebook，Notebook 中包含以下内容的代码：

- 加载和预处理 CIFAR-100 数据集
- 定义 ResNet18 和 Vision Transformer 模型
- 使用不同的超参数训练模型
- 将训练好的模型权重保存到 `weights/` 目录

**训练部分支持各种自定义的训练设置，包括**：

- 训练轮数 
- 学习率（设计成了 `lr_list` 以便于多种参数设置的实验）
- 正则化强度 （设计成了 `weight_decay_list` 以便于多种参数设置的实验）
- 数据增强策略
  - 默认为基础增强+CutMix, 
  - 可以选择运行最后注释的代码块以选择无增强和基础增强策略

### 评估

要评估训练好的模型，请运行 `vis.ipynb` Jupyter Notebook。该 Notebook 包含以下内容的代码：

- 从 `weights/` 目录加载训练好的模型权重
- 在测试集上评估模型
- 可视化结果并比较模型性能

### 日志

- `logs/` 目录包含不同模型配置的训练日志和图表。

  - `resnet18` 和 `vit` 子目录分别存储 ResNet18 和 Vision Transformer 模型的 TensorBoard 日志。

  - `graph` 子目录包含性能比较的曲线图。







---

​								*本项目为 Fudan University Computer Vision 课程作业，作者：律己zZZ*