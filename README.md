rllab is no longer under active development, but an [alliance of researchers](https://github.com/rlworkgroup/) from several universities has adopted it, and now maintains it under the name [**garage**](https://github.com/rlworkgroup/garage).

We recommend you develop new projects, and rebase old ones, onto the actively-maintained [garage](https://github.com/rlworkgroup/garage) codebase, to promote reproducibility and code-sharing in RL research. The new codebase shares almost all of its code with rllab, so most conversions only need to edit package import paths and perhaps update some renamed functions. 

[garage](https://github.com/rlworkgroup/garage) is always looking for new users and contributors, so please consider contributing your rllab-based projects and improvements to the new codebase! Recent improvements include first-class support for TensorFlow, TensorBoard integration, new algorithms including PPO and DDPG, updated Docker images, new environment wrappers, many updated dependencies, and stability improvements.

[![Docs](https://readthedocs.org/projects/rllab/badge)](http://rllab.readthedocs.org/en/latest/)
[![Circle CI](https://circleci.com/gh/rllab/rllab.svg?style=shield)](https://circleci.com/gh/rllab/rllab)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/rllab/rllab/blob/master/LICENSE)
[![Join the chat at https://gitter.im/rllab/rllab](https://badges.gitter.im/rllab/rllab.svg)](https://gitter.im/rllab/rllab?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

# rllab

rllab is a framework for developing and evaluating reinforcement learning algorithms. It includes a wide range of continuous control tasks plus implementations of the following algorithms:


- [REINFORCE](https://github.com/rllab/rllab/blob/master/rllab/algos/vpg.py)
- [Truncated Natural Policy Gradient](https://github.com/rllab/rllab/blob/master/rllab/algos/tnpg.py)
- [Reward-Weighted Regression](https://github.com/rllab/rllab/blob/master/rllab/algos/erwr.py)
- [Relative Entropy Policy Search](https://github.com/rllab/rllab/blob/master/rllab/algos/reps.py)
- [Trust Region Policy Optimization](https://github.com/rllab/rllab/blob/master/rllab/algos/trpo.py)
- [Cross Entropy Method](https://github.com/rllab/rllab/blob/master/rllab/algos/cem.py)
- [Covariance Matrix Adaption Evolution Strategy](https://github.com/rllab/rllab/blob/master/rllab/algos/cma_es.py)
- [Deep Deterministic Policy Gradient](https://github.com/rllab/rllab/blob/master/rllab/algos/ddpg.py)

rllab is fully compatible with [OpenAI Gym](https://gym.openai.com/). See [here](http://rllab.readthedocs.io/en/latest/user/gym_integration.html) for instructions and examples.

rllab only officially supports Python 3.5+. For an older snapshot of rllab sitting on Python 2, please use the [py2 branch](https://github.com/rllab/rllab/tree/py2).

rllab comes with support for running reinforcement learning experiments on an EC2 cluster, and tools for visualizing the results. See the [documentation](https://rllab.readthedocs.io/en/latest/user/cluster.html) for details.

The main modules use [Theano](http://deeplearning.net/software/theano/) as the underlying framework, and we have support for TensorFlow under [sandbox/rocky/tf](https://github.com/openai/rllab/tree/master/sandbox/rocky/tf).

# Documentation

Documentation is available online: [https://rllab.readthedocs.org/en/latest/](https://rllab.readthedocs.org/en/latest/).

# Citing rllab

If you use rllab for academic research, you are highly encouraged to cite the following paper:

- Yan Duan, Xi Chen, Rein Houthooft, John Schulman, Pieter Abbeel. "[Benchmarking Deep Reinforcement Learning for Continuous Control](http://arxiv.org/abs/1604.06778)". _Proceedings of the 33rd International Conference on Machine Learning (ICML), 2016._

# Credits

rllab was originally developed by Rocky Duan (UC Berkeley / OpenAI), Peter Chen (UC Berkeley), Rein Houthooft (UC Berkeley / OpenAI), John Schulman (UC Berkeley / OpenAI), and Pieter Abbeel (UC Berkeley / OpenAI). The library is continued to be jointly developed by people at OpenAI and UC Berkeley.

# Slides

Slides presented at ICML 2016: https://www.dropbox.com/s/rqtpp1jv2jtzxeg/ICML2016_benchmarking_slides.pdf?dl=0

# install
```
export PYTHONPATH=/media/usaywook/rllab/:$PYTHONPATH
```

## sources.list 추가에러

```
sudo apt-get build-dep python-pygame
```
에서 아래와 같은 에러 발생
```
E: You must put some 'source' URIs in your sources.list
```
아래 명령에서 source.list deb-src 있는 부분 전부 주석해제
```
sudo vi /etc/apt/sources.list
sudo apt-get update
```
다시 source.list deb-src 있는 부분 전부 주석

## in environment.yml

python==3.5.2 -> python==3.5.*

https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow_gpu-1.0.1-cp35-cp35m-linux_x86_64.whl; 'linux' in sys_platform 
-> https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow_gpu-1.2.0-cp35-cp35m-linux_x86_64.whl; 'linux' in sys_platform 

./script/setup_linux.sh
./script/setup_mujoco.sh

/home/usaywook/.mujoco/mjpro131/bin
/home/usaywook/.mujoco/mjkey.txt

## import tensorflow
ImportError: libcudart.so.8.0: cannot open shared object file: No such file or directory
https://developer.nvidia.com/cuda-80-ga2-download-archive 설치 후
```
sudo apt-get install cuda-8.0
vi ~/.bashrc
export PATH=/usr/local/cuda-8.0/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-8.0/lib64\${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
source ~/.bashrc
nvcc --version
```
Couldn't open CUDA library libcudnn.so.5.
https://developer.nvidia.com/rdp/cudnn-archive 에서 로그인 하고 cuDNN v5.1 Library for Linux 설치
```
cd <다운로드 경로>
sudo tar -xzvf cudnn-8.0-linux-x64-v5.1.tgz
cd cuda
sudo cp include/cudnn.h /usr/local/cuda-8.0/include
sudo cp lib64/libcudnn* /usr/local/cuda-8.0/lib64
sudo chmod a+r /usr/local/cuda-8.0/lib64/libcudnn*
cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2
```
