# Keras 安装配置

## 1 安装 Miniconda / Anaconda

&emsp;&emsp;书接上回：[Win11 安装配置 Miniconda](./Win11安装配置Miniconda全过程记录.md)



## 2 创建并激活虚拟环境

### 2.1 创建虚拟环境

> 创建名为 venv 的 python3.9 虚拟环境

```shell
conda create -n venv python=3.9
```

![](keras_files/1.jpg)

### 2.2 激活虚拟环境

> 激活虚拟环境

```shell
conda activate venv
```

![](keras_files/2.jpg)



## 3 安装并运行 Jupyter Notebook

### 3.1 安装 ipython 和 notebook

> 使用 conda 在对应的虚拟环境中安装

```shell
conda install -n venv ipython notebook
```

![](keras_files/3.jpg)

### 3.2 运行 Jupyter Notebook

> 运行 jupyter notebook

```shell
jupyter notebook
```

- vscode 终端界面

![](keras_files/4.jpg)

- 浏览器运行界面

![](keras_files/5.jpg)

- 注：按 Ctrl + C 关闭 Notebook



## 4 安装 Kears 主要的包

```shell
conda install -n venv numpy matplotlib pandas pydotplus h5py scikit-learn
```

![](keras_files/6.jpg)

```shell
conda install -n venv scipy mkl-service libpython m2w64-toolchain
```

![](keras_files/7.jpg)



## 5 安装深度学习库

> 安装 git 和 graphviz

```shell
conda install -n venv git graphviz
```

> 安装 Theano

```shell
pip install --ignore-installed --upgrade theano
```

> 安装 TensorFlow

```shell
pip install --ignore-installed --upgrade tensorflow
```

- 注1：在安装 TensorFlow 时，Keras 也会随之安装，不用单独安装，且当前的版本中，TensorFlow 会同时安装 CPU 和 GPU 两个版本。
- 注2：`--ignore-installed --upgrade` &emsp;忽略已安装的升级



## 6 安装 CUDA

### 6.1 检查当前版本 

> 检查当前 nvidia 显卡版本指令

```shell
nvidia-smi
```

![](keras_files/8.jpg)

### 6.2 [CUDA 所有版本安装](https://developer.nvidia.com/cuda-toolkit-archive)

![](keras_files/9.jpg)

### 6.3 安装注意

&emsp;&emsp;与普通软件安装不同，在安装 CUDA 时，需要设置两次。第一次要求设置临时解压目录，第二次才是设置安装目录，这里建议默认即可，也可以自定义。安装结束后，临时解压文件夹会自动删除。<font style="color:red">切记，使用两次设置的路径不能相同，否则安装后会找不到目录。</font>同时，因为是系统级软件，所以最好全程使用默认的安装位置。

- 解压 CUDA 安装包

![image-20220726110749394](keras_files/image-20220726110749394.png)

- 选择自定义安装

![image-20220726105411640](keras_files/image-20220726105411640.png)

- 取消安装 Visual Studio Integration 组件，防止后续报错

![image-20220726111111967](keras_files/image-20220726111111967.png)

- 使用默认安装路径，不做修改

![image-20220726111331816](keras_files/image-20220726111331816.png)

> 检查是否安装成功

- 检查当前 C版本指令

```shell
nvcc -V
```

- 输出版本即为成功

![image-20220726112544663](keras_files/image-20220726112544663.png)



## 7 安装 cuDNN

### 7.1 cuDNN 官网

- 官网：[cuDNN下载](https://developer.nvidia.com/zh-cn/cudnn)，这里 <font style="color:red">必须登录账号</font> 才能继续下载。

![image-20220726135042391](keras_files/image-20220726135042391.png)

- 首次使用需要注册账号并输入详细信息

![image-20220726140602291](keras_files/image-20220726140602291.png)

### 7.2 下载对应版本

&emsp;&emsp;[cuDNN下载](https://developer.nvidia.com/rdp/cudnn-archive)，因为之前安装的 CUDA 版本号为 11.6，所以我们选择对应版本的 cuDNN 进行下载。

![image-20220726135657176](keras_files/image-20220726135657176.png)

### 7.3 安装 cuDNN

&emsp;&emsp;上面我们下载的内容实际上是压缩包文件，本质上就是对 CUDA 的关于深度学习的补充文件，我们需要将解压后的文件 <font style="color:red">逐一复制</font> 到 CUDA Development 目录中。

- cuDNN 解压包内容

![image-20220726144717844](keras_files/image-20220726144717844.png)

- CUDA Development 安装目录内容

![image-20220726145523088](keras_files/image-20220726145523088.png)



## 8 配置环境变量

> 在环境变量中添加如下内容

&emsp;&emsp;如若在系统环境变量中没有，则需要自行添加如下内容。【注：此处安装目录以实际情况为准】

```
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.6\bin
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.6\include
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.6\lib
C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.6\libnvvp
```

![image-20220726145324709](keras_files/image-20220726145324709.png)



## 9 测试安装环境

```python
import scipy
import numpy
import matplotlib
import pandas
import sklearn
import pydotplus
import h5py

import theano
import tensorflow
import keras

print('scipy ' + scipy.__version__)
print('numpy ' + numpy.__version__)
print('matplotlib ' + matplotlib.__version__)
print('pandas ' + pandas.__version__)
print('sklearn ' + sklearn.__version__)
print('h5py ' + h5py.__version__)

print('theano ' + theano.__version__)
print('tensorflow ' + tensorflow.__version__)
print('keras ' + keras.__version__)
```



## 参考文章

1. [CSDN - CUDA安装](https://blog.csdn.net/oxygenh2o/article/details/122145588)
2. [CSDN - CUDA安装教程（超详细）](https://blog.csdn.net/m0_45447650/article/details/123704930)
3. [CSDN - 深度学习环境搭建超级详解（Miniconda、pytorch安装）](https://blog.csdn.net/weixin_44263674/article/details/125516305)
4. [CSDN - TensorFlow 2.8.0安装 + Miniconda + GPU支持](https://blog.csdn.net/encbkakw1/article/details/123702213)
5. [知乎 - 深度学习GPU环境CUDA详细安装过程（简单快速有效）](https://zhuanlan.zhihu.com/p/358737417)

