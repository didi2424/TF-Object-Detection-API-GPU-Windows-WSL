 <a name="readme-top"></a>

<!-- The Basics -->
## The Basics

This repository is a tutorial for how to use Tensorflow's Object Detection API (boxes Classsifier) to train an image into object detection classifier on Windows 11 as Host. also when we use Tensorflow 2.11 is not support GPU inside Windows anymore we can use Ubuntu on Windows as our main host.


This README.md describes every step required to get going with your custom object detection classifier :

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#the-basics">The Basics</a>
    </li>
    <li>
    <a href="#about-the-project">About The Project</a>
    <ul>
        <a href="#build-with"> Build With </a>
    </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#environment-in-windows">Environment in Windows</a></li>
        <li><a href="#environment-in-ubuntu-on-windows-wsl">Environment in Ubuntu on Windows _(WSL)_</a></li>
      </ul>
    </li>
    <li><a href="#notebook-description">Notebook Description</a></li>

  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## About The Project

The purpose of this tutorial is to explain how to train you custom Convolutional Neural Network Object Detection Classifier with your custom image and Models that Tensorflow Provide, Also in this tutorial you will use a powerfull 'Jupyter Notebook' for interface and connect to your 'Ubuntu On Windows' At the end of this tutorial, you will have a program that can identify object with draw boxes around specific objects in pictures, videos, or in the webcam feed.

Serveral Good Tutorial avaliable in github for how to use Tensorflow Object Detection API. Hovewer in this tutorial that use Tensorflow version 2.11. Tensorflow >= 2.11 will no longger supported on Windows for GPU usage. Tensorflow for future version seems using Linux for supported GPU usage.  
If you don't like to dual boot this is good tutorial for you ❤️

<p align="right">(<a href="#readme-top">back to top</a>)</p>






<!-- GETTING STARTED -->
## Getting Started

Tensorflow's GPU allows your PC to use the graphic card to provide extra processing power while training the dataset and the models, so it will be used for this tutoral, in the air GPU provide faster training dataset than CPU. Nowday Tensorflow => 2.11 is not supporting Windows to use a GPU. So, you are need 'Ubuntu on Windows' to solve this.


<!-- Environment in Windows -->


### Environment on Windows 10/11
* [![Windows][Windows]][Windows-url]
* [![Nvidia][Nvidia]][Nvidia-url]
* [![Ubuntu][Ubuntu]][Ubuntu-url]

_Enable you windows WSL_
1. Click Start on your windows and search Windows Features
2. in the Windows Features Find And Enable
   ```sh
   Enable Virtual Machine Platfrom
   Enable Windows WSL
   ```
3. Click Ok 



_Downloads Ubuntu on Windows_
1. Click Start on your windows and search Microsoft Store
2. on search bar Microsoft Store
   ```sh
   Ubuntu on Windows
   ```
3. Click Get

4. After downloading and instaling Ubuntu on Windows Apps will appear in _Start Menu_
5. First time you open Ubuntu on Windows you need to configure the ubuntu name and password.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- Environment in Ubuntu on Windows WSL -->
### Environment in Ubuntu on Windows WSL

* [![Miniconda][Miniconda]][Miniconda-url]
* [![Python][Python]][Python-url]
* [![Tensorflow][Tensorflow]][Next-url]
* [![Nvidia][Nvidia]][Nvidia-url]
* [![Jupyter-Notebook][Jupyter-Notebook]][Jupyter-Notebook-url]


_Install Miniconda 3 inside WSL_
1. Open your WSL and Command
   ```sh
   sudo apt-get update
   sudo apt-get install wget
   ```
2. Download Miniconda for Linux and install
   ```sh
   wget https://repo.anaconda.com/miniconda/Miniconda3-py38_23.1.0-1-Linux-x86_64.sh
   sh ./Miniconda3-py39_4.12.0-Linux-x86_64.sh
   ```
3. Wait until installation is finished
4. After Miniconda installation is done you need make an env (in this tutorial we named env to 'tfod') with python 3.8.10
   ```sh
   conda create --name tfod python=3.8.10 -y
   conda deactivate
   ```

6. Activate the env 
   ```sh
   conda activate tfod
   ```
7. Install CudaToolkit and Cudnn
   ```sh
   conda install -c conda-forge cudatoolkit=11.2 cudnn=8.1.0 -y
   ```
8. Nividia-Tensorrt
   ```sh
   pip install nvidia-pyindex
   pip install nvidia-tensorrt==7.2.3.4
   pip install pycocotools==2.0.2
   pip install tensorflow-addons==0.19.0
   
   ```
5. Install Cuda Driver for Windows WSL
   ```sh
   wget https://developer.download.nvidia.com/compute/cuda/repos/wsl-ubuntu/x86_64/cuda-wsl-ubuntu.pin
   sudo mv cuda-wsl-ubuntu.pin /etc/apt/preferences.d/cuda-repository-pin-600
   wget https://developer.download.nvidia.com/compute/cuda/12.1.0/local_installers/cuda-repo-wsl-ubuntu-12-1-local_12.1.0-1_amd64.deb
   sudo dpkg -i cuda-repo-wsl-ubuntu-12-1-local_12.1.0-1_amd64.deb
   sudo cp /var/cuda-repo-wsl-ubuntu-12-1-local/cuda-*-keyring.gpg /usr/share/keyrings/
   sudo apt-get update
   sudo apt-get -y install cuda
   ```
9. Configure The system paths you must deactive conda environment to setup Configure The System Paths
   ```sh
   cd $CONDA_PREFIX
   mkdir -p $CONDA_PREFIX/etc/conda/activate.d
   echo 'export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$CONDA_PREFIX/lib/' > $CONDA_PREFIX/etc/conda/activate.d/env_vars.sh
   echo ln -s $CONDA_PREFIX/lib/python3.8/site-packages/tensorrt/libnvinfer.so.8  $CONDA_PREFIX/lib/libnvinfer.so.7
   echo ln -s $CONDA_PREFIX/lib/python3.8/site-packages/tensorrt/libnvinfer_plugin.so.8 $CONDA_PREFIX/lib/libnvinfer_plugin.so.7
   ``` 
    Why ? when installing tensorrt we need configure the system paths, otherwise tensorrt cannot open share object file, So run command below to configure system paths. system paths will be automatically configured when you activate your conda environment 

   <h3> NOTICE !!! </h3>
    to see if configure the system paths is correct 

    ```sh
    nano $CONDA_PREFIX/etc/conda/activate.d/env_vars.sh
    ```
10. Deactivate and Activate again the conda env
    ```sh
    conda deactivate
    conda activate tfod
    ```
11. Install Jupyter Notebook for our Interface to the env
    ```sh
    conda install jupyter notebook -y
    pip install label-studio
    ``` 
12. Run Jupyter notebook
    ```sh
    jupyter notebook
    ```
<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Notebook Description

### 1. Install Tensorflow Object API using Jupyter Notebook Interface

Everything you need, Build With ❤️ This notebook contain to Download, install Tensorflow Object Detection API. After you done to install, verification the installation so Tensorflow Object Detection ready to use.

### 2. Create Label Map And TF record file

After installation you need to build labelmap file with .pbtxt format file. in this notebook you need to change variable class of object that match with your coco dataset format. 

.record format file is tensorflow simple format for storing a sequence of binary file 
because training with Tensorflow Object Detection API need a .record file. You need to build a .record file with this notebook, unzip dataset from image-studio into image directory, so notebook can run auto export of your .record file based on your custom dataset also this .record file for training proccess.

understanding result.json using pycocotools and pylabel library 

### 3. Config And Training 

Okay for now you have a labelmap.pbtxt and .record file from previous notebook.
from pretrained model that you download in notebook 1, you need configuration the pipeline.config and save into your Workspace Directory. after you have your pipeline.config inside Workspace Directory. Let's Rock your GPU 💃💃💃, Train your Costum Dataset and Costum Models with Powerfull GPU Engine. 

### 4. Test Object Detection

Finally you have to test 🧪 your training data with an images  
with this notebook, notebook will call for training data that you have done in the previous notebook. Object Detection will identify object with draw boxes around specific objects in pictures 🖼️

also in this notebook you will get a TFlite file for future project example to use on Tensorflow Lite Android

<img
  src="https://github.com/didi2424/TF-Object-Detection-API-GPU-Windows-WSL/blob/main/Notebook%20Preview%20Output/output_counter_single_image.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/github_username/repo_name.svg?style=for-the-badge
[contributors-url]: https://github.com/github_username/repo_name/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/github_username/repo_name.svg?style=for-the-badge
[forks-url]: https://github.com/github_username/repo_name/network/members
[stars-shield]: https://img.shields.io/github/stars/github_username/repo_name.svg?style=for-the-badge
[stars-url]: https://github.com/github_username/repo_name/stargazers
[issues-shield]: https://img.shields.io/github/issues/github_username/repo_name.svg?style=for-the-badge
[issues-url]: https://github.com/github_username/repo_name/issues
[license-shield]: https://img.shields.io/github/license/github_username/repo_name.svg?style=for-the-badge
[license-url]: https://github.com/github_username/repo_name/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/linkedin_username
[product-screenshot]: images/screenshot.png
[Next.js]: https://img.shields.io/badge/next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white
[Next-url]: https://nextjs.org/
[Tensorflow]: https://img.shields.io/badge/Tensorflow-000000?style=for-the-badge&logo=Tensorflow&logoColor=orange
[Tensorflow-url]: https://www.tensorflow.org/
[Python]: https://img.shields.io/badge/Python-000000?style=for-the-badge&logo=Python&logoColor=blue
[Python-url]: https://www.python.org/
[Ubuntu]: https://img.shields.io/badge/Ubuntu-000000?style=for-the-badge&logo=Ubuntu&logoColor=orange
[Ubuntu-url]: https://ubuntu.com/wsl
[Nvidia]: https://img.shields.io/badge/Nvidia-000000?style=for-the-badge&logo=Nvidia&logoColor=green
[Nvidia-url]: https://ubuntu.com/wsl
[Jupyter-Notebook]: https://img.shields.io/badge/Jupyter/Notebook-000000?style=for-the-badge&logo=Jupyter&logoColor=orange
[Jupyter-Notebook-url]: https://jupyter.org/
[Windows]: https://img.shields.io/badge/Windows/WSL-000000?style=for-the-badge&logo=windows&logoColor=blue
[Windows-url]: https://jupyter.org/
[miniconda]: https://img.shields.io/badge/Miniconda-000000?style=for-the-badge&logo=Anaconda&logoColor=green
[miniconda-url]: https://jupyter.org/

