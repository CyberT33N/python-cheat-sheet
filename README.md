# Python Cheat Sheet
Python Cheat Sheet with the most needed stuff..





# Install

<br><br>

## Ubuntu 23.04

### Python 3.9 - Using pyenv
- https://github.com/CyberT33N/python-cheat-sheet/?tab=readme-ov-file#install-3
```
sudo apt-get update
sudo apt-get install python3-pip libbz2-dev ibncurses5-dev libffi-dev libreadline-dev libssl-dev libsqlite3-dev tk-dev liblzma-dev

pyenv install 3.9
```



<br><br>

### Python Latest
```
sudo apt install python3 python3-pip
```












<br><br>
______________________________________
______________________________________
<br><br>

# Package manager

<br><br>

## Anaconda

<br><br>

### Install 

<br><br>

#### Ubuntu 24.04 - Python 3.11
```shell
sudo apt-get install libgl1-mesa-glx libegl1-mesa libxrandr2 libxrandr2 libxss1 libxcursor1 libxcomposite1 libasound2 libxi6 libxtst6


wget https://repo.anaconda.com/archive/Anaconda3-2024.10-1-Linux-x86_64.sh
chmod +x Anaconda3-2024.10-1-Linux-x86_64.sh
bash Anaconda3-2024.10-1-Linux-x86_64.sh
```
- Select yes when it asks to modify shell

<br><br>

#### Ubuntu 23.04 - Python 3.11
```shell
wget https://repo.anaconda.com/archive/Anaconda3-2023.09-0-Linux-x86_64.sh
chmod +x Anaconda3-2023.09-0-Linux-x86_64.sh
bash Anaconda3-2023.09-0-Linux-x86_64.sh
```







<br><br>
<br><br>



## pip

<br><br>

### Install
```
sudo apt install python3-pip
```















<br><br>
______________________________________
______________________________________
<br><br>

# Python manager

<br><br>

## pyenv
- https://github.com/pyenv/pyenv?tab=readme-ov-file#installation

<br><br>

### Install
```shell
curl https://pyenv.run | bash

# Add to ~/.bashrc & ~/.zshrc
export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"

# restart shell
```

<br><br>

#### Install specific python version
```shell
pyenv install 3.9
```

<br><br>

#### Switch specific python version
- https://github.com/pyenv/pyenv?tab=readme-ov-file#switch-between-python-versions
```shell
pyenv shell <version> -- select just for current shell session
pyenv local <version> -- automatically select whenever you are in the current directory (or its subdirectories)
pyenv global <version> -- select globally for your user account
```





















<br><br>
______________________________________
______________________________________
<br><br>


# pytorch
- https://pytorch.org/get-started/locally/
- PyTorch ist eine mächtige Open-Source-Maschinenlernbibliothek, die von Facebook AI entwickelt wurde. Sie wird besonders für die Implementierung von Deep-Learning-Modellen genutzt. PyTorch bietet dynamisches Rechendefinieren, was bedeutet, dass du Modelle erstellen und ändern kannst, während sie ausgeführt werden.

<br><br>

## Install

<br><br>

### Ubuntu 23.04
```shell
# pip
pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118

# anaconda
conda install pytorch torchvision
conda install pytorch::torchaudio
```




















<br><br>
______________________________________
______________________________________
<br><br>

# Start project
```bash
# For Python 2:
python <filename>.py

# For Python 3:
python3 <filename>.py
```


















<br><br>
______________________________________
______________________________________
<br><br>

# virtual environment

<br><br>

## Example
```bash
git pull https://github.com/SociallyIneptWeeb/AICoverGen

cd AICoverGen

# This Project need python 3.9
pyenv local 3.9

# In order to install the specific dependencies for the project and not system wide we create an virtual environment
python3 -m venv AICoverGenENV
source AICoverGenENV/bin/activate

# Install dependencies from this file
pip install -r requirements.txt

git pull

# Download models
python src/download_models.py

# Run UI
python src/webui.py
```

To restart the project later again from new terminal just use again:
```shell
source AICoverGenENV/bin/activate
python src/webui.py
```






















<br><br>
______________________________________
______________________________________
<br><br>

# Machine Learning

## GPU
- https://cloud.google.com/compute/gpus-pricing#gpu-pricing

### Using Consumer GPUs for Deep Learning
```
While consumer GPUs are not suitable for large-scale deep learning projects, these processors can provide a good entry point for deep learning. Consumer GPUs can also be a cheaper supplement for less complex tasks, such as model planning or low-level testing. However, as you scale up, you’ll want to consider data center grade GPUs and high-end deep learning systems like NVIDIA’s DGX series (learn more in the following sections).

In particular, the Titan V has been shown to provide performance similar to datacenter-grade GPUs when it comes to Word RNNs. Additionally, its performance for CNNs is only slightly below higher tier options. The Titan RTX and RTX 2080 Ti aren’t far behind.

NVIDIA Titan V

The Titan V is a PC GPU that was designed for use by scientists and researchers. It is based on NVIDIA’s Volta technology and includes Tensor Cores. The Titan V comes in Standard and CEO Editions.

The Standard edition provides 12GB memory, 110 teraflops performance, a 4.5MB L2 cache, and 3,072-bit memory bus. The CEO edition provides 32GB memory and 125 teraflops performance, 6MB cache, and 4,096-bit memory bus. The latter edition also uses the same 8-Hi HBM2 memory stacks that are used in the 32GB Tesla units.

NVIDIA Titan RTX

The Titan RTX is a PC GPU based on NVIDIA’s Turing GPU architecture that is designed for creative and machine learning workloads. It includes Tensor Core and RT Core technologies to enable ray tracing and accelerated AI.

Each Titan RTX provides 130 teraflops, 24GB GDDR6 memory, 6MB cache, and 11 GigaRays per second. This is due to 72 Turing RT Cores and 576 multi-precision Turing Tensor Cores.

NVIDIA GeForce RTX 2080 Ti

The GeForce RTX 2080 Ti is a PC GPU designed for enthusiasts. It is based on the TU102 graphics processor. Each GeForce RTX 2080 Ti provides 11GB of memory, a 352-bit memory bus, a 6MB cache, and roughly 120 teraflops of performance.
```

### Best Deep Learning GPUs for Large-Scale Projects and Data Centers
```
The following are GPUs recommended for use in large-scale AI projects.

NVIDIA Tesla A100

The A100 is a GPU with Tensor Cores that incorporates multi-instance GPU (MIG) technology. It was designed for machine learning, data analytics, and HPC.

The Tesla A100 is meant to be scaled to up to thousands of units and can be partitioned into seven GPU instances for any size workload. Each Tesla A100 provides up to 624 teraflops performance, 40GB memory, 1,555 GB memory bandwidth, and 600GB/s interconnects.

NVIDIA Tesla V100

The NVIDIA Tesla V100 is a Tensor Core enabled GPU that was designed for machine learning, deep learning, and high performance computing (HPC). It is powered by NVIDIA Volta technology, which supports tensor core technology, specialized for accelerating common tensor operations in deep learning. Each Tesla V100 provides 149 teraflops of performance, up to 32GB memory, and a 4,096-bit memory bus.

NVIDIA Tesla P100

The Tesla P100 is a GPU based on an NVIDIA Pascal architecture that is designed for machine learning and HPC. Each P100 provides up to 21 teraflops of performance, 16GB of memory, and a 4,096-bit memory bus.

NVIDIA Tesla K80

The Tesla K80 is a GPU based on the NVIDIA Kepler architecture that is designed to accelerate scientific computing and data analytics. It includes 4,992 NVIDIA CUDA cores and GPU Boost™ technology. Each K80 provides up to 8.73 teraflops of performance, 24GB of GDDR5 memory, and 480GB of memory bandwidth.

Google TPU

Slightly different are Google’s tensor processing units (TPUs). TPUs are chip or cloud-based, application-specific integrated circuits (ASIC) for deep learning. These units are specifically designed for use with TensorFlow and are available only on Google Cloud Platform.

Each TPU can provide up to 420 teraflops of performance and 128 GB high bandwidth memory (HBM). There are also pod versions available that can provide over 100 petaflops of performance, 32TB HBM, and a 2D toroidal mesh network.

Learn more in our guide about TensorFlow GPUs.
```





## Setup

### Ubuntu 23.04
- You need a GPU with more than 4GB RAM. In my case 1050 TI was not enough..
```shell
# 1. ----- Install nvidia driver - https://github.com/CyberT33N/linux-cheat-sheet/blob/main/README.md#install--update ----- 
sudo apt-get purge 'nvidia*'
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-driver-525 nvidia-settings
sudo reboot



# 2. ----- install Cuda & cuDNN - https://github.com/CyberT33N/linux-cheat-sheet/blob/main/README.md#cuda--cudnn ----- 
sudo apt update
sudo apt install build-essential

# check if it worked
gcc --version
g++ --version

sudo apt install nvidia-cuda-toolkit nvidia-cuda-toolkit-gcc nvidia-cudnn

# Check if it worked
nvcc --version



# 3. ---- Install python & pip ----
sudo apt install python3 python3-pip



# 4. ---- Install pyenv ----
curl https://pyenv.run | bash

# Add to ~/.bashrc & ~/.zshrc
export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"

# restart shell



# 5. ---- Install Pytorch ----
conda install pytorch torchvision
conda install pytorch::torchaudio
```




# gcloud - compute engine
- **Make always sure to suspend your VM if you do not use it to not waste money**

### guide
- https://www.youtube.com/watch?v=Tl8esVqEQZU&list=PLgTTUdxnNfyQNKUTYyI-2CL_bXkfprTnk&index=1


## 1. Create project
- https://console.cloud.google.com/projectcreate?


## 2. Create VM

### a) Ready VM with everything installed
- https://medium.com/google-cloud/how-to-run-deep-learning-models-on-google-cloud-platform-in-6-steps-4950a57acfa5

Search for "Deep Learning VM"
  - Start

Deployment name: deeplearning-1
Zone: us-central1-c <-- Does not matter
  - If you get later error "The zone does not have enough resources" try other zone e.g. asia



Machine type: n1-highmem-2 (2 vCPU, 13GB RAM) <-- **Will work but for some cases not enough if you can use n1-highmem-2 with 26GB RAM**
GPU Type: NVIDIA T4 - 1 CPU
- Check install NVIDIA GPU Driver
Framework: TensorFlow 2.13 (CUDA 11.8, Python 3.10)

Uncheck "Access to Jupyter Lab"
- We use SSH

Boot disk type: Standard Persistent Disk
Boot disk size: 1000GB





### b) Custom VM

 Compute Engine -> VM Instances -> Create Instance
- https://console.cloud.google.com/compute/instances

Name: deep-learning-1
Region: us-central1 (lowa) <-- Cheapest
Zone: us-central1-c <-- Does not matter

GPU: NVIDIA T4 (cheaper) / NVIDIA Tesla K80 (recommended but more expensive)
Amount GPU: 1

Machine type: n1-highmem-2 (2 vCPU, 13GB RAM) <-- **Will work but for some cases not enough if you can use n1-highmem-2 with 26GB RAM**

Boot:
  - Public Images:
    - OS: Deep Learning on Linux
    - Version: Deep Learning VM with CUDA 11.8 M115
    - Disk Space: 500GB (Maybe 100GB is enough..)
      - default space type

Firewall:
- You can keep everything unchecked. If needed you can create an ssh tunnel to port-forward and GUI to your localhost on your host machine. Only enable HTTP&HTTPS Traffic if you want to create access from the internet

```shell
gcloud compute instances create deep-learning-1 --project=deep-learning-tests-411921 --zone=us-central1-a --machine-type=n1-highmem-2 --network-interface=network-tier=PREMIUM,stack-type=IPV4_ONLY,subnet=default --maintenance-policy=TERMINATE --provisioning-model=STANDARD --service-account=470007060618-compute@developer.gserviceaccount.com --scopes=https://www.googleapis.com/auth/devstorage.read_only,https://www.googleapis.com/auth/logging.write,https://www.googleapis.com/auth/monitoring.write,https://www.googleapis.com/auth/servicecontrol,https://www.googleapis.com/auth/service.management.readonly,https://www.googleapis.com/auth/trace.append --accelerator=count=1,type=nvidia-tesla-t4 --create-disk=auto-delete=yes,boot=yes,device-name=deep-learning-1,image=projects/ml-images/global/images/c0-deeplearning-common-gpu-v20240111-debian-11-py310,mode=rw,size=1000,type=projects/deep-learning-tests-411921/zones/us-central1-a/diskTypes/pd-standard --no-shielded-secure-boot --shielded-vtpm --shielded-integrity-monitoring --labels=goog-ec-src=vm_add-gcloud --reservation-affinity=any
```




## 3. gcloud CLI

### a) Install

#### Ubuntu 23.04
```shell
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates gnupg curl sudo

curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo gpg --dearmor -o /usr/share/keyrings/cloud.google.gpg

echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" | sudo tee -a /etc/apt/sources.list.d/google-cloud-sdk.list

sudo apt-get update && sudo apt-get install google-cloud-cli

# If you get error "The repository 'https://packages.cloud.google.com/apt cloud-sdk InRelease' is not signed.""
curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key --keyring /usr/share/keyrings/cloud.google.gpg add -

```


### b) Create an SSH connection to your machine
```
gcloud compute ssh --project deep-learning-tests-411921 --zone asia-east1-c deeplearning-1-vm -- -L 8080:localhost:8080
```

### c) Jupyter Notebook
- http://localhost:8080/














































































<br><br>
______________________________________
______________________________________
<br><br>

# printf

## f-strings
```python
self.n_cpu = cpu_count()
print(f"cpu_count(): {self.n_cpu}")
```










































<br><br>
______________________________________
______________________________________
<br><br>

# FAQ

## Error "This environment is externally managed"
- https://askubuntu.com/a/1469197/1461683
    
    There's a good article on OMGUbuntu about this: [3 Ways to Solve Pip Install Error on Ubuntu 23.04][1]
    
    Here's the summary. There are three ways to approach this problem:
    
    # 1. Use a repo version
    
    For instance, if you want to install the `requests` Python library, you can install it using APT instead, like this:
    
        sudo apt install python3-requests
    
    This will install this library system-wide.
    
    Not all packages available on PyPI have been packaged and included in the Debian/Ubuntu repositories, so this method won't work for some packages.
    
    # Or: 2. Create a virtual environment using `venv` or `virtualenv`
    
    Make sure `venv` is installed by running:
    
        sudo apt install python3-venv
    
    To create a new virtual environment in a directory named `env`, run:
    
        python3 -m venv env
    
    To activate this virtual environment (which modifies the `PATH` environment variable), run this:
    
        source env/bin/activate
    
    Now you can install a library like `requests` in this virtual environment:
    
        pip install requests
    
    The files will get installed under the `env/` directory.
    
    If you want to leave the virtual environment, you can run:
    
        deactivate
    
    If you don't want to run `source env/bin/activate` and `deactivate`, then you can run the executable by prefixing its path, like this:
    
         $ env/bin/pip install requests
         $ env/bin/python3
         >>> import request
         >>> help(requests)
    
    # Or: 3. Use `pipx`
    
    [pipx][2] lets you install and run Python applications in isolated environments. This is the recommend way to install PyPI packages that represent command-line applications.
    
    To install pipx, run:
    
         sudo apt install pipx
    
    pipx needs `~/.local/bin/` to be in your PATH. You can automatically modify your shell configuration (such as `~/.bashrc`) to modify PATH appropriately by running:
    
         pipx ensurepath
    
    Now you can install a package from PyPI, like this:
    
         pipx install pycowsay
    
    And you can run the command that you just installed, like this:
    
    ```
    $ pycowsay Mooo!
    
      -----
    < Mooo! >
      -----
       \   ^__^
        \  (oo)\_______
           (__)\       )\/\
               ||----w |
               ||     ||
    ```
    
    As you can see, pipx installed a symlink in `~/.local/bin/` to the executable in a virtual environment:
    
    ```
    $ ls -l ~/.local/bin/pycowsay
    lrwxrwxrwx 1 flimm flimm 50 May 24 11:19 /home/flimm/.local/bin/pycowsay -> /home/flimm/.local/pipx/venvs/pycowsay/bin/pycowsay*
    ```
    
    # Or: 4. Pass `--break-system-packages` flag:
    
    If you want to ignore the warning, you can pass the `--break-system-packages` flag:
    
        pip install --break-system-packages --user <foobar>
    
    This method is not recommended, because you may find yourself with mysterious broken installations of Python packages months or years later, after you've forgotten that you used `--break-system-packages` and installed other conflicting Python packages.
    
      [1]: https://www.omgubuntu.co.uk/2023/04/pip-install-error-externally-managed-environment-fix
      [2]: https://pypa.github.io/pipx/
