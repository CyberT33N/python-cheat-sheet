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

# Environment manager

<br><br>




## Miniconda
- https://github.com/CyberT33N/conda-cheat/blob/main/README.md#miniconda






<br><br>
<br><br>


## uv
- https://github.com/CyberT33N/uv-cheat-sheet/blob/main/README.md#ubuntu







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
- https://github.com/CyberT33N/pyenv-cheat-sheet/blob/main/README.md




































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

<details><summary>Click to expand..</summary>
    
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


</details>
























<br><br>
<br><br>
___
<br><br>
<br><br>

# Utils



<details><summary>Click to expand..</summary>

# Screenshot Script
- Take screenshot of python app

<details><summary>Click to expand..</summary>


# Dependencies for Screenshot Script


## Required Python Packages
- pillow - Main imaging library for creating and saving screenshots
- pygetwindow - For capturing window coordinates on Windows
- xdotool - Linux tool for window management and identification
- ImageMagick - Linux tool with 'import' command for direct window capture

## Already in requirements.txt
- pillow
- pygetwindow

## System Dependencies (Linux)
- xdotool - `sudo apt-get install -y xdotool`
- ImageMagick - Usually pre-installed on many Linux distros, provides the 'import' command

## Optional Dependencies
- python-gi (PyGObject) - For GTK-based window detection fallback on Linux

Das Script nutzt mehrere Methoden, um das Fenster zu finden und zu fotografieren:
1. Primär: ImageMagick's `import` Befehl (Linux)
2. Sekundär: xdotool für Fenstererkennung (Linux)
3. Windows: pygetwindow
4. macOS: AppleScript

Im Notfall wird ein Vollbild-Screenshot erstellt, wenn keine der Methoden erfolgreich ist.



```python
#!/usr/bin/env python3
import subprocess
import time
import os
from datetime import datetime
import sys
from PIL import ImageGrab
import tkinter as tk

def capture_using_import(output_path):
    """
    Capture active window using the 'import' command from ImageMagick.
    Returns: True if successful, False otherwise
    """
    try:
        # First activate the window (optional, may already be active)
        subprocess.run("xdotool windowactivate $(xdotool getactivewindow)", shell=True)
        time.sleep(0.5)  # Give it a moment to activate
        
        # Use the import command to capture the active window
        # -window root captures the entire screen, but we'll use 'import -window "$(xdotool getactivewindow)"'
        # to capture only the active window
        command = f'import -window "$(xdotool getactivewindow)" "{output_path}"'
        result = subprocess.run(command, shell=True)
        
        if result.returncode == 0 and os.path.exists(output_path):
            print(f"Successfully captured window using import command to: {output_path}")
            return True
    except Exception as e:
        print(f"Error using import command: {e}")
    
    return False

def capture_active_window_with_gtk():
    """
    Capture the active window using GTK on Linux
    Returns: (x, y, width, height) or None if failed
    """
    try:
        # Try using GDK to get active window info
        from gi.repository import Gdk
        
        # Get default screen and active window
        display = Gdk.Display.get_default()
        screen = display.get_default_screen()
        active_window = screen.get_active_window()
        
        if active_window:
            # Get geometry
            x, y, width, height = active_window.get_geometry()
            # Get position
            root_x, root_y = active_window.get_root_origin()
            return (root_x, root_y, width, height)
    except Exception as e:
        print(f"GTK window capture failed: {e}")
    
    return None

def start_app_and_take_screenshot(delay=5):
    """
    Start the main.py app and take a screenshot after a specified delay.
    
    Args:
        delay (int): Number of seconds to wait before taking screenshot
    """
    print(f"Starting main.py application...")
    
    # Get the absolute path to the main directory
    main_dir = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))
    main_script = os.path.join(main_dir, "main.py")
    
    # Start the main.py in a separate process
    process = subprocess.Popen([sys.executable, main_script], 
                              stderr=subprocess.PIPE)
    
    # Wait for the specified delay to let the app initialize
    print(f"Waiting {delay} seconds for the application to initialize...")
    
    # Check if process terminated early (indicating an error)
    for _ in range(delay):
        time.sleep(1)
        if process.poll() is not None:
            # Process has terminated
            _, stderr = process.communicate()
            print(f"Error: Application failed to start properly:")
            print(stderr.decode())
            return
    
    # Take screenshot
    try:
        timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
        screenshot_dir = os.path.join(main_dir, "screenshots")
        
        # Create screenshots directory if it doesn't exist
        if not os.path.exists(screenshot_dir):
            os.makedirs(screenshot_dir)
            
        screenshot_path = os.path.join(screenshot_dir, f"app_screenshot_{timestamp}.png")
        
        # Find the app window
        if sys.platform == "linux" or sys.platform == "linux2":
            # Try first using the 'import' command from ImageMagick (best for window captures on Linux)
            screenshot_taken = False
            
            # Check if import command is available
            if subprocess.run("which import", shell=True, stdout=subprocess.PIPE).returncode == 0:
                print("Trying to capture using import command...")
                screenshot_taken = capture_using_import(screenshot_path)
            
            # If import command failed or not available, try xdotool method
            if not screenshot_taken:
                window_geometry = None
                
                # Try using xdotool
                try:
                    # List of possible window titles/patterns to search for
                    window_titles = [
                        "VoiceTyper Pro",
                        "Voice Typer",
                        "VoiceTyper",
                        "customtkinter",
                        ".*Voice.*",  # Regex pattern to match any window with Voice in the title
                        ".*Typer.*"   # Regex pattern to match any window with Typer in the title
                    ]
                    
                    window_id = None
                    # Try each window title until we find a match
                    for title in window_titles:
                        try:
                            result = subprocess.check_output(f"xdotool search --name '{title}'", shell=True).decode().strip()
                            if result:
                                window_id = result.split('\n')[0]  # Take the first window if multiple found
                                print(f"Found window with title containing '{title}': {window_id}")
                                break
                        except subprocess.CalledProcessError:
                            continue
                    
                    if not window_id:
                        # Last resort: try to find any new window that appeared in the last 'delay' seconds
                        print("Couldn't find specific window, trying to activate it...")
                        subprocess.run("xdotool windowactivate $(xdotool getactivewindow)", shell=True)
                        time.sleep(1)  # Give it a moment to activate
                        window_id = subprocess.check_output("xdotool getactivewindow", shell=True).decode().strip()
                    
                    if window_id:
                        # Get window geometry
                        try:
                            window_info = subprocess.check_output(f"xdotool getwindowgeometry {window_id}", shell=True).decode()
                            
                            # Parse position and size
                            position_line = [line for line in window_info.split('\n') if "Position" in line][0]
                            size_line = [line for line in window_info.split('\n') if "Geometry" in line][0]
                            
                            x, y = map(int, position_line.split(':')[1].strip().split(','))
                            width, height = map(int, size_line.split(':')[1].strip().split('x'))
                            
                            # Store window geometry
                            window_geometry = (x, y, width, height)
                        except Exception as e:
                            print(f"Error getting window geometry with xdotool: {e}")
                except Exception as e:
                    print(f"Error finding window with xdotool: {e}")
                
                # If xdotool failed, try GTK method
                if window_geometry is None:
                    print("Trying GTK method for window capture...")
                    try:
                        window_geometry = capture_active_window_with_gtk()
                    except Exception as e:
                        print(f"GTK window capture failed: {e}")
                
                # If we have window geometry, take screenshot of that specific region
                if window_geometry:
                    x, y, width, height = window_geometry
                    
                    # Add a small padding to ensure we get the entire window including borders
                    x = max(0, x - 5)
                    y = max(0, y - 5)
                    width += 10
                    height += 10
                    
                    # Capture the specific region
                    screenshot = ImageGrab.grab(bbox=(x, y, x+width, y+height))
                    screenshot.save(screenshot_path)
                    print(f"Window screenshot saved to: {screenshot_path}")
                    screenshot_taken = True
                
                # If all methods failed, take full screenshot
                if not screenshot_taken:
                    print("Window detection failed, taking full screenshot instead")
                    screenshot = ImageGrab.grab()
                    screenshot.save(screenshot_path)
                    print(f"Full screenshot saved to: {screenshot_path}")
                
        elif sys.platform == "win32":
            # For Windows
            import pygetwindow as gw
            try:
                # Try different window titles
                window_titles = ['VoiceTyper Pro', 'Voice Typer', 'VoiceTyper']
                window = None
                
                for title in window_titles:
                    windows = gw.getWindowsWithTitle(title)
                    if windows:
                        window = windows[0]
                        print(f"Found window with title: {title}")
                        break
                
                if window:
                    # Add small padding to ensure we get the entire window
                    left = max(0, window.left - 5)
                    top = max(0, window.top - 5)
                    right = window.right + 5
                    bottom = window.bottom + 5
                    
                    screenshot = ImageGrab.grab(bbox=(left, top, right, bottom))
                    screenshot.save(screenshot_path)
                    print(f"Window screenshot saved to: {screenshot_path}")
                else:
                    print("Window not found, taking full screenshot instead")
                    screenshot = ImageGrab.grab()
                    screenshot.save(screenshot_path)
                    print(f"Full screenshot saved to: {screenshot_path}")
            except Exception as e:
                print(f"Error finding window: {e}")
                screenshot = ImageGrab.grab()
                screenshot.save(screenshot_path)
                print(f"Full screenshot saved to: {screenshot_path}")
        elif sys.platform == "darwin":
            # For macOS
            try:
                # Use applescript to get window position and size
                script = """
                tell application "System Events"
                    set frontApp to name of first application process whose frontmost is true
                    tell process frontApp
                        set appWindow to first window
                        set {x, y} to position of appWindow
                        set {width, height} to size of appWindow
                        return x & "," & y & "," & width & "," & height
                    end tell
                end tell
                """
                result = subprocess.check_output(["osascript", "-e", script]).decode().strip()
                x, y, width, height = map(int, result.split(','))
                
                # Add small padding
                x = max(0, x - 5)
                y = max(0, y - 5)
                width += 10
                height += 10
                
                screenshot = ImageGrab.grab(bbox=(x, y, x+width, y+height))
                screenshot.save(screenshot_path)
                print(f"Window screenshot saved to: {screenshot_path}")
            except Exception as e:
                print(f"Error finding window: {e}")
                screenshot = ImageGrab.grab()
                screenshot.save(screenshot_path)
                print(f"Full screenshot saved to: {screenshot_path}")
        else:
            # Fallback to full screen for other platforms
            screenshot = ImageGrab.grab()
            screenshot.save(screenshot_path)
            print(f"Full screenshot saved to: {screenshot_path}")
        
        # Ask user if they want to close the app
        response = input("Do you want to close the application? (y/n): ")
        if response.lower() == 'y':
            process.terminate()
            print("Application terminated.")
        else:
            print("Application left running. You can close it manually.")
            print("The script will now exit, but the app will continue running.")
    except Exception as e:
        print(f"Error taking screenshot: {e}")
        process.terminate()

if __name__ == "__main__":
    # You can modify the delay (in seconds) if needed
    start_app_and_take_screenshot(5) 
```
    
</details>

</details>
