### 1. Setting the `wsl` environment

- Check available distro using the following command: `wslconfig.exe /l`

- Set `Ubuntu` as the default distro when running `wsl` using the following command: `wslconfig.exe /s Ubuntu`


### 2. Setting the display environment for the `GUI`

- Install [VcXsrv](https://sourceforge.net/projects/vcxsrv/)

- Launch `vcxsrv` using `XLaunch.exe` with the following settings:
  ```
    Multiple windows
    Displant number: -1
    Start no client
    Clipboard checked
    Primary Selection checked
    Native opengl checked
    Disable access control checked
  ```
- Determine IP using the following command: `route.exe print | grep 0.0.0.0 | head -1 | awk '{print $4}'`
- Add the following line in the `.bashrc` file, `export DISPLAY=IP:.0.0`. </br>
  Example: `export DISPLAY=192.168.20.230:0.0`

- Change Windows firewall setting </br>
	In command prompt, enter `wf.msc` to display `Windows Defender Firewall with Advanced Security`. </br>
	Select the `Inbound Rules` section on the left and find rows of `VcXsrv windows xserver`. </br>
	Select only those that have `Block` on the `Action` column and change this into `Allow` by double clicking on that row and select `Allow the connection`. </br>

- Test run </br>
  Using `wsl`, install `x11-apps` using `sudo apt-get install x11-apps` then run `xeyes`. </br>
	A window should appear with a pair of eyes following the mouse pointer.


### 3. Setting up the conda environment: `artic-ncov2019`
- Install **miniconda** using the following command
```
curl -sL "https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh" > "Miniconda3.sh"
bash Miniconda3.sh
```
- Install `mamba` for faster environment creation
```
conda install -c conda-forge mamba
```
- Install the `ARTIC nCoV-2019` data and software repository
```
git clone --recursive https://github.com/artic-network/artic-ncov2019.git
```
- Create conda environment from the downloaded repository using `mamba`
```
mamba env create -f artic-ncov2019/environment.yml
```
- Activate the newly created environment, `artic-ncov2019`, and install additional package.
```
conda activate artic-ncov2019
pip install PySimpleGUI
```


### 4. Copying `git` repo
Since they are private repo, create your [Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) in your github account.

The following repo must be placed in the `home` directory...
```
git clone https://PERSONALACCESSTOKEN@github.com/Ivan-Sotelo/geco_gui.git
```
while this one must be placed inside `/mnt/c/apps`. Create `apps` if it is not yet present.
```
git clone -b automated https://PERSONALACCESSTOKEN@github.com/fgmp/ncov2019-artic-nf-GECO.git
```
