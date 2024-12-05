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

## Miniconda

<br><br>

### Install
- https://docs.anaconda.com/miniconda/install/#quick-command-line-install
```
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm ~/miniconda3/miniconda.sh

source ~/miniconda3/bin/activate

conda init --all
```









<br><br>
<br><br>
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
- https://github.com/CyberT33N/pytorch-cheat-sheet/blob/main/README.md

























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

# Virtual environment
- In order to not install dependencies globally but instead specific for your project we create virtual environments

<br><br>

## Create env
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

## Deactivate env
```shell
deactivate
```












<br><br>
______________________________________
______________________________________
<br><br>






# Dependencies

## Upgrade dependency
```
pip install --upgrade huggingface_hub
```

<br><br>

## Install dependency globally
```shell
sudo apt install pipx
pipx install nvitop
pipx ensurepath
```


<br><br>

## requirements.txt
Create requirements.txt
```txt
accelerate
argh
dacite
demucs
diffusers==0.9.0
flask
flask_cors
numpy
pillow>=9.1.0
plotly
pydub
pysoundfile
scipy
soundfile
sox
streamlit>=1.18.0
torch
torchaudio
torchvision
transformers
```

And then run:
```shell
python -m pip install -r requirements.txt
```





























<br><br>
______________________________________
______________________________________
<br><br>




# import

## import local dependency
```python
import os
import torch
from PIL import Image
from transformers import AutoProcessor, AutoModelForVision2Seq

# Überprüfe, ob die GPU verfügbar ist
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
if device.type == 'cuda':
    print("GPU wird verwendet:", torch.cuda.get_device_name(0))
else:
    print("GPU nicht verfügbar, CPU wird verwendet.")

# Kosmos-2 Model und Processor laden
kosmos_path = "/home/user/Projects/ai/resources/transformers/kosmos-2-patch14-224"
model = AutoModelForVision2Seq.from_pretrained(kosmos_path).to(device)  # Verschiebe das Modell auf die GPU
processor = AutoProcessor.from_pretrained(kosmos_path)
```












<br><br>
______________________________________
______________________________________
<br><br>

# Machine Learning
- https://github.com/CyberT33N/machine-learning-cheat-sheet/blob/main/README.md










































































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
