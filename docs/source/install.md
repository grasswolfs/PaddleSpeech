# Installation
There are 3 ways to use `PaddleSpeech`. According to the degree of difficulty, the 3 ways can be divided into **Easy**, **Medium** and **Hard**. You can choose one of the 3 ways to install `PaddleSpeech`.

| Way | Function                                                     | Support|
| :---- | :----------------------------------------------------------- |:----|
| Easy     | (1) Use command line functions of PaddleSpeech. <br> (2) Experience PaddleSpeech on Ai Studio. | Linux, Mac，Windows |
| Medium     | Support major function，such as using the` ready-made `examples and using PaddleSpeech to train your own model.                                           | Linux |
| Hard     | Support full function of Paddlespeech，including training n-gram language model, montreal-forced-aligner and so on. And you are more able be a developer! | Ubuntu |


## Prerequisites
- Python >= 3.7
- PaddlePaddle latest version (please refer to the [Installation Guide] (https://www.paddlepaddle.org.cn/documentation/docs/en/beginners_guide/index_en.html))
- C++ compilation environment
- Hip: For Linux and Mac, do not use command `sh` instead of command `bash` in installation document.

## Easy: Get the Basic Function (Support Linux, Mac and Windows)
- If you are newer to `PaddleSpeech` and want to experience it easily without your own machine. We recommend you to use [AI Studio](https://aistudio.baidu.com/aistudio/index) to experience it. There is a step-by-step tutorial for `PaddleSpeech` and you can use the basic function of `PaddleSpeech` with a free machine. 
- If you want to use the command line function of Paddlespeech, you need to complete the following steps to install `PaddleSpeech`. For more information about how to use command line function , you can see the [cli](https://github.com/PaddlePaddle/PaddleSpeech/tree/develop/paddlespeech/cli).
### Install Conda
Conda is a management system of the environment. You can go to [minicoda](https://docs.conda.io/en/latest/miniconda.html)  (select a version py>=3.7) to download and install the conda.
And then Install  conda dependencies for `paddlespeech` :

```bash
conda install -y -c conda-forge sox libsndfile bzip2
```
### Install C++ Compilation Environment 

(If you already have C++ compilation environment, you can miss this step.)

#### Windows
You need to install the `Visual Studio` to make the C++ compilation environment.

#### Mac
```bash
brew install gcc
```
#### Linux
```bash
#  centos
sudo yum install gcc gcc-c++
```
```bash
# ubuntu
sudo apt install build-essential
```
```bash
# Others
conda install -y -c gcc_linux-64=8.4.0 gxx_linux-64=8.4.0
```

### Install PaddleSpeech 
You can use the following command:
```bash
pip install paddlepaddle paddlespeech
```


## Medium: Get the Major Function (Support Linux)
If you want to get the major function of  `paddlespeech`. There are 4 steps you need to do.

### Install Conda
Conda is a management system of the environment. You can go to [minicoda](https://docs.conda.io/en/latest/miniconda.html) to select a version (py>=3.7) and install it by yourself or you can use the following command:
```bash
# download the miniconda
wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
# install the miniconda
bash Miniconda3-latest-Linux-x86_64.sh -b
# conda init
$HOME/miniconda3/bin/conda init
# activate the conda
bash
```
Then you can create an conda virtual environment using the following command:
```bash
conda create -y -p tools/venv python=3.7
```
Activate the conda virtual environment:
```bash
conda activate tools/venv
```
Install  conda dependencies for `paddlespeech` :
```bash
conda install -y -c conda-forge sox libsndfile swig bzip2
```
### Install C++ Compilation Environment 
(If you already have C++ compilation environment, you can miss this step.)
Do not forget to install `gcc` and `gxx` on your system.
You can choose to use the scripts below to install them.

```bash
#  centos
sudo yum install gcc gcc-c++
```
```bash
# ubuntu
sudo apt install build-essential
```
```bash
# Others
conda install -y -c gcc_linux-64=8.4.0 gxx_linux-64=8.4.0
```
(Hip: Do not use the last script if you want to install by **Hard** way):
### Install PaddlePaddle
You can choose the `PaddlePaddle` version based on your system. For example, for CUDA 10.2, CuDNN7.5 install paddlepaddle-gpu 2.2.0:
```bash
python3 -m pip install paddlepaddle-gpu==2.2.0
```
### Install PaddleSpeech 
You need to `git clone` this repository and install  `paddlespeech`  by the following commands，then you can use the `ready-made` examples in `paddlespeech` :
```bash
https://github.com/PaddlePaddle/PaddleSpeech.git
cd PaddleSpeech
pip install .
```
## Hard: Get the Full Function (Support Ubuntu)
### Prerequisites
- Ubuntu >= 16.04.
- choice 1: working with `Ubuntu` Docker Container.
- choice 2: working on `Ubuntu` with `root` privilege. 

To avoid the trouble of environment setup, running in Docker container is highly recommended. Otherwise, if you work on `Ubuntu` with `root` privilege, you can still complete the installation.

### Choice 1: Running in Docker Container (Recommand)
Docker is an open-source tool to build, ship, and run distributed applications in an isolated environment. A Docker image for this project has been provided in [hub.docker.com](https://hub.docker.com) with all the dependencies installed. This Docker image requires the support of NVIDIA GPU, so please make sure its availability and the [nvidia-docker](https://github.com/NVIDIA/nvidia-docker) has been installed.

Take several steps to launch the Docker image:
- Download the Docker image

For example, pull paddle 2.2.0 image:
```bash
nvidia-docker pull registry.baidubce.com/paddlepaddle/paddle:2.2.0-gpu-cuda10.2-cudnn7
```
- Clone this repository
```bash
git clone https://github.com/PaddlePaddle/PaddleSpeech.git
```
- Run the Docker image

```bash
sudo nvidia-docker run --net=host --ipc=host --rm -it -v $(pwd)/PaddleSpeech:/PaddleSpeech registry.baidubce.com/paddlepaddle/paddle:2.2.0-gpu-cuda10.2-cudnn7 /bin/bash
```
- Enter PaddleSpeech directory.
```bash
cd /PaddleSpeech
```
Now you can execute training, inference and hyper-parameters tuning in  Docker container.

### Choice 2: Running in Ubuntu with Root Privilege
- Install `build-essential` by apt
```bash
sudo apt install build-essential
```
- Clone this repository
```bash
git clone https://github.com/PaddlePaddle/PaddleSpeech.git
# Enter the PaddleSpeech dir
cd PaddleSpeech
```
### Install the Conda
```bash
# download and install the miniconda
pushd tools
bash extras/install_miniconda.sh
popd
# use the "bash" command to make the conda environment works
bash
# create an conda virtual environment
conda create -y -p tools/venv python=3.7
# Activate the conda virtual environment:
conda activate tools/venv
# Install the conda packags
conda install -y -c conda-forge sox libsndfile swig bzip2 libflac bc
```
### Install PaddlePaddle
Make sure you have GPU and the paddlepaddle version is right. For example, for CUDA 10.2, CuDNN7.5 install paddle 2.2.0:

```bash
python3 -m pip install paddlepaddle-gpu==2.2.0
```
### Install PaddleSpeech in Developing Mode
```bash
pip install -e .[develop]
```
### Install the Kaldi (Optional)
```bash
pushd tools
bash extras/install_openblas.sh
bash extras/install_kaldi.sh
popd
```

