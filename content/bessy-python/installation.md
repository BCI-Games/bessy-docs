This tutorial will walk you through the process of setting up a Miniconda environment on your computer. If you have already installed Miniconda (or Anaconda) then you can skip to Step 3: Create a Conda Environment.

## Step 1: Download Miniconda
Miniconda is a lightweight version of Anaconda, a popular package manager and environment manager for Python. Follow the steps below to install Miniconda on your computer:

1. Go to the [Miniconda website](https://docs.conda.io/en/latest/miniconda.html)
2. Download the appropriate installer for your operating system (Windows, macOS, or Linux).
   * *For **macOS**, choose the version appropriate for your chipset (macOS Intel x86 or macOS Apple M series). **To determine your chipset**, go to "About this Mac". The information will be listed beside "Chip".*
3. Choose the installer for Python 3.9 or later.


## Step 2: Install Miniconda
Once you have downloaded the Miniconda installer, follow these steps to install it:

### For Windows:
1. Double-click the downloaded `.exe` file to launch the installer.
2. Click "Next" on the Welcome screen.
3. Read the license agreement and accept it if you agree.
4. Choose "Just Me" when asked to select an install location.
5. Leave the default installation path as it is (usually in the user's home directory) and click "Next."
6. *(optional but recommended)* On the next screen, select "Add Miniconda3 to my PATH environment variable" to use Conda and Python from the Command Prompt or PowerShell.
7. Click "Install" to begin the installation.
8. Once the installation is complete, click "Next" and then "Finish" to close the installer.

### For macOS:
1. Open a terminal window.
2. Navigate to the directory where you downloaded the Miniconda installer.
3. Run the installer script:
   ```bash
   bash Miniconda3-latest-MacOSX-arm64.sh
   ```
4. Follow the on-screen instructions, read the license agreement, and accept it if you agree. If you are unsure about any setting, accept the defaults. You can change them later.
5. Choose the installation location. The default location is usually in your home directory, and you can press `Enter` to confirm it.
6. When asked if you want to initialize Miniconda3, type `yes` and press `Enter`.
7. Close and reopen your terminal to use the newly installed Miniconda.

### For Linux:
1. Open a terminal window.
2. Navigate to the directory where you downloaded the Miniconda installer.
3. Make the installer script executable by running the following command (replace `Miniconda3-latest-Linux-x86_64.sh` with the actual filename):
   ```bash
   chmod +x Miniconda3-latest-Linux-x86_64.sh
   ```
4. Run the installer script:
   ```bash
   ./Miniconda3-latest-Linux-x86_64.sh
   ```
5. Follow the on-screen instructions, read the license agreement, and accept it if you agree. If you are unsure about any setting, accept the defaults. You can change them later.
6. Choose the installation location. The default location is usually in your home directory, and you can press `Enter` to confirm it.
7. When asked if you want to initialize Miniconda3, type `yes` and press `Enter`.
8. Close and reopen your terminal to use the newly installed Miniconda.

## Step 3: Create a Conda environment
Now that you have Miniconda installed, you can create a new Conda environment named "bessy" using Python 3.9:

1. Open a terminal or command prompt.
2. Create the "bessy" environment with Python 3.9:
   ```bash
   conda create -n bessy python=3.9
   ```
   This command creates a new environment named "bessy" (-n flag) and installs Python version 3.9 in it.

   Note: If this step fails, it is likely that miniconda was not added correctly to your PATH. If this is the case, there are many online tutorials showing "How to add miniconda to PATH", you can alternatively run these commands from the Anaconda Prompt if you don't want to add miniconda to PATH.
3. Activate the "bessy" environment:
   ```bash
   conda activate bessy
   ```
   When activated, your command prompt will change to indicate that you are now in the "bessy" environment.
4. Now, you can install packages and run Python scripts within the "bessy" environment without affecting your system-wide Python installation.

## Step 4: Install BCI Essentials Python
The library can either be installed from pip directly, or as a locally editable package.
```sh
pip install bci-essentials
```

To use the latest version, you must first clone the project repository:
```sh
git clone https://github.com/kirtonBCIlab/bci-essentials-python
```
Then, from the `bci-essentials-python` directory, install the project as a package in editable mode:
```sh
cd bci-essentials-python
conda activate bessy
pip install -e .
```

If any `pip` packages fail to install, try installing them manually using conda (e.g., `conda install mne-lsl`).

## Step 5: Celebrate!!
That's it! You have successfully installed Miniconda and created a Conda environment named "bessy" with Python 3.9. You have filled this environment with all the dependencies required to run BCI Essentials on your computer! You can now work within this environment for your Python projects without interfering with other installations on your computer. Remember to activate the environment whenever you want to work in it and deactivate it when you're done.

## Deactivating your Conda Environment
To deactivate the "bessy" environment and return to your base environment, simply run:
```bash
conda deactivate
```