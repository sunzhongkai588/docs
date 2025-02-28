..  _install_introduction:

=========
 安装指南
=========


-----------
  重要更新
-----------

* 新增对 python3.12 的支持，并不再支持 python3.7
* 新增对 CUDA 12.0 的支持，并不再支持 CUDA 10.2


-----------
  安装说明
-----------

本说明将指导您在 64 位操作系统编译和安装 PaddlePaddle

**1. 操作系统要求：**

* Windows 7 / 8 / 10，专业版 / 企业版
* Ubuntu 18.04 / 20.04
* CentOS 7
* macOS 10.x/11.x/12.x/13.x/14.x
* 操作系统要求是 64 位版本

**2. 处理器要求**

* 处理器支持 MKL
* 处理器架构是 x86_64（或称作 x64、Intel 64、AMD64）架构，目前 PaddlePaddle 不支持 arm64 架构

**3. Python 和 pip 版本要求：**

* Python 的版本要求 3.8/3.9/3.10/3.11/3.12
* Python 具有 pip, 且 pip 的版本要求 20.2.2+
* Python 和 pip 要求是 64 位版本

**4. PaddlePaddle 对 GPU 支持情况：**

* 目前 **PaddlePaddle** 支持 **NVIDIA** 显卡的 **CUDA** 驱动和 **AMD** 显卡的 **ROCm** 架构
* 需要安装 `cuDNN <https://docs.nvidia.com/deeplearning/sdk/cudnn-install/>`_ ，版本要求 7.6+(For CUDA11+)
* 如果您需要 GPU 多卡模式，需要安装 `NCCL 2 <https://developer.nvidia.com/nccl/>`_

    * 仅 Ubuntu/CentOS 支持 NCCL 2 技术
* 需要安装 `CUDA <https://docs.nvidia.com/cuda/cuda-installation-guide-windows/>`_ ，根据您系统不同，对 CUDA 版本要求不同：

    * Windows 安装 GPU 版本

        * Windows 7/8/10 支持 CUDA 11.0/11.2/11.6/11.8/12.0 单卡模式
        * 不支持 **nvidia-docker** 方式安装
    * Ubuntu 安装 GPU 版本

        * Ubuntu 18.04 支持 CUDA (11.0 - 12.0)
        * Ubuntu 20.04 支持 CUDA (11.0 - 12.0)
        * 如果您是使用 **nvidia-docker** 安装，支持 CUDA 11.2/11.7/12.0
    * CentOS 安装 GPU 版本

        * 如果您是使用本机 **pip** 安装：

            * CentOS 7 支持 CUDA (11.0 - 12.0)
        * 如果您是使用本机源码编译安装：

            * CentOS 7 支持 CUDA (11.0 - 12.0)
        * 如果您是使用 **nvidia-docker** 安装，在 CentOS 7 下支持 CUDA 11.2/11.7/12.0
    * macOS 不支持：macOS 平台不支持 GPU 安装

请确保您的环境满足以上条件。如您有其他需求，请参考 `多版本 whl 包安装列表 <Tables.html#ciwhls-release>`_ .

**5. PaddlePaddle 对 NCCL 支持情况：**

* Windows 支持情况

    * 不支持 NCCL
* Ubuntu 支持情况

    * Ubuntu 20.04：

        * 支持 NCCL v2.4.7-v2.16.5
* CentOS 支持情况

    * CentOS 7：

        * 支持 NCCL v2.4.7-v2.16.5
* macOS 支持情况

    * 不支持 NCCL

**第一种安装方式：使用 pip 安装**

您可以选择“使用 pip 安装”、“使用 conda 安装”、“使用 docker 安装”、“从源码编译安装” 四种方式中的任意一种方式进行安装。

本节将介绍使用 pip 的安装方式。

1. 需要您确认您的 操作系统 满足上方列出的要求

2. 需要您确认您的 处理器 满足上方列出的要求

3. 确认您需要安装 PaddlePaddle 的 Python 是您预期的位置，因为您计算机可能有多个 Python

    使用以下命令输出 Python 路径，根据您的环境您可能需要将说明中所有命令行中的 python 替换为具体的 Python 路径

        在 Windows 环境下，输出 Python 路径的命令为：

        ::

            where python

        在 macOS/Linux 环境下，输出 Python 路径的命令为：

        ::

            which python


4. 检查 Python 的版本

    使用以下命令确认是 3.8/3.9/3.10/3.11/3.12
    ::

        python --version

5. 检查 pip 的版本，确认是 20.2.2+

    ::

        python -m ensurepip
        python -m pip --version


6. 确认 Python 和 pip 是 64 bit，并且处理器架构是 x86_64（或称作 x64、Intel 64、AMD64）架构。下面的第一行输出的是 "64bit" ，第二行输出的是 "x86_64" 、 "x64" 或 "AMD64" 即可：

    ::

        python -c "import platform;print(platform.architecture()[0]);print(platform.machine())"


7. 如果您希望使用 `pip <https://pypi.org/project/pip/>`_ 进行安装 PaddlePaddle 可以直接使用以下命令:

    (1). **CPU 版本** ：如果您只是想安装 CPU 版本请参考如下命令安装

        安装 CPU 版本的命令为：
        ::

            python -m pip install paddlepaddle==2.6.0 -i https://mirror.baidu.com/pypi/simple

            或

            python -m pip install paddlepaddle==2.6.0 -i https://pypi.tuna.tsinghua.edu.cn/simple


    (2). **GPU 版本** ：如果您想使用 GPU 版本请参考如下命令安装

        注意：

            * 需要您确认您的 GPU 满足上方列出的要求

        ::

            python -m pip install paddlepaddle-gpu==2.6.0 -i https://mirror.baidu.com/pypi/simple

            或

            python -m pip install paddlepaddle-gpu==2.6.0 -i https://pypi.tuna.tsinghua.edu.cn/simple


    请确认需要安装 PaddlePaddle 的 Python 是您预期的位置，因为您计算机可能有多个 Python。根据您的环境您可能需要将说明中所有命令行中的 python 替换为具体的 Python 路径。

8. 验证安装

    使用 python 进入 python 解释器，输入 import paddle ，再输入 paddle.utils.run_check()。

    如果出现 PaddlePaddle is installed successfully!，说明您已成功安装。

9. 更多帮助信息请参考：

    `Linux 下的 PIP 安装 <pip/linux-pip.html>`_

    `macOS 下的 PIP 安装 <pip/macos-pip.html>`_

    `Windows 下的 PIP 安装 <pip/windows-pip.html>`_


**第二种安装方式：使用源代码编译安装**

- 如果您只是使用 PaddlePaddle ，建议使用 **pip** 安装即可。
- 如果您有开发 PaddlePaddle 的需求，请参考：`从源码编译 <compile/fromsource.html>`_


..  toctree::
    :hidden:

    pip/frompip.rst
    conda/fromconda.rst
    docker/fromdocker.rst
    compile/fromsource.rst
    install_Kunlun_zh.md
    install_ROCM_zh.md
    install_mlu_cn.md
    install_NGC_PaddlePaddle_ch.rst
    Tables.md
