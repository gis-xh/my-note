# PyTorch 安装配置

## 1 安装 Miniconda / Anaconda

&emsp;&emsp;书接上回：[Win11 安装配置 Miniconda](../python/01conda/Win11-Miniconda-install.md)



## 2 创建并激活虚拟环境

### 2.1 创建虚拟环境

> 创建名为 pytorchtest 的 python3.9 虚拟环境

```shell
conda create -n pytorchtest python=3.9
```

![image-20220809143210356](img/image-20220809143210356.png)

### 2.2 激活虚拟环境

> 激活虚拟环境

```shell
conda activate pytorchtest
```

![image-20220809143242151](img/image-20220809143242151.png)



## 3 安装并配置 CUDA & cuDNN

### 3.1 安装 CUDA

&emsp;&emsp;详情请见：[Keras 安装配置 - 安装 CUDA](./Keras-install.md#6-安装-cuda)

### 3.2 安装 cuDNN

&emsp;&emsp;详情请见：[Keras 安装配置 - 安装 cuDNN](./Keras-install.md#7-安装-cudnn)

### 3.3 配置环境变量

&emsp;&emsp;详情请见：[Keras 安装配置 - 配置环境变量](./Keras-install.md#8-配置环境变量)



## 4 安装 torch & torchvision

### 4.1 [下载地址](https://download.pytorch.org/whl/torch_stable.html)

&emsp;&emsp;进入网址，选择适合自己版本的进行下载。保存到路径稍浅的文件夹里面，方面后续调用。

![image-20220809141743113](img/image-20220809141743113.png)

> 版本号说明

- cu116：表示 cuda 版本为 11.6（及以上都可以）
- torch-1.12.1：表示 torch 版本为 1.12.1
- cp39：表示 python 版本为 3.9
- win：表示 windows 系统

![image-20220809144022534](img/image-20220809144022534.png)

### 4.2 在 Miniconda 中安装

> 转到下载目录

&emsp;&emsp;`Ctrl+R` 后调出 cmd 命令行，需要先激活虚拟环境，再转入到下载目录。【注：此处目录以实际情况为准】

```shell
cd ../../
D:
cd Downloads
```

![image-20220809143630482](img/image-20220809143630482.png)

> 安装 torch

```shell
pip install 输入torch并按下Tab键自动补全
```

![image-20220809144314211](img/image-20220809144314211.png)

> 安装 torchvision

```
pip install 输入torchvision并按下Tab键自动补全
```

- 注：这里会安装一些必要相关库，所以显示条文会长一些。

![image-20220809144634555](img/image-20220809144634555.png)



## 5 验证是否安装成功

> 调用 Python

```shell
python
```

![image-20220809144910292](img/image-20220809144910292.png)

> 检查 torch 版本

```python
import torch
print(torch.__version__) #注意，此处下划线"_"是两个下划线"__"
print(torch.cuda.is_available())
```

![image-20220809145237431](img/image-20220809145237431.png)

## 参考文章

1. [CSDN - 深度学习环境搭建超级详解（Miniconda、pytorch安装）](https://blog.csdn.net/weixin_44263674/article/details/125516305)

