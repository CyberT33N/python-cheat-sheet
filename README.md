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
```shell
# The version of Anaconda may be different depending on when you are installing`
curl -O https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
sh Miniconda3-latest-Linux-x86_64.sh
# and follow the prompts. The defaults are generally good.`
```


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

### Install
```shell
curl https://pyenv.run | bash

# Add to ~/.bashrc & ~/.zshrc
export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"

# restart shell
```


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

### Ubuntu
```shell
- pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
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

# Dependencies

<br><br>

## Install dependencies from project
```bash
git pull https://github.com/SociallyIneptWeeb/AICoverGen

cd AICoverGen

# This Project need python 3.9
pyenv shell 3.9

# In order to install the specific dependencies for the project and not system wide we create an virtual environment
python3 -m venv AICoverGenENV
source AICoverGenENV/bin/activate

# Install dependencies from this file
pip install -r requirements.txt
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
