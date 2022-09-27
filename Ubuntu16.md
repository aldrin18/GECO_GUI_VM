### 1. Setting up the conda environment: `artic-ncov2019`
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


### 2. Copying `git` repo
Since they are private repo, create your [Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) in your github account.

The following repo must be placed in the `home` directory...
```
git clone https://PERSONALACCESSTOKEN@github.com/Ivan-Sotelo/geco_gui.git
```
while this one must be placed inside `/mnt/c/apps`. Create `apps` if it is not yet present.
```
git clone -b automated https://PERSONALACCESSTOKEN@github.com/fgmp/ncov2019-artic-nf-GECO.git
```


### 3. Editing configuration files
- In the `ncov2019-artic-nf-GECO/conf/redcap.config`, replace `redcap_url` with `https://geco.ritm-edc.net/redcap/api/` and the `redcap_token` with `YOURWORKING_REDCAP_TOKEN`
- In the system's `/etc/hosts` file, add `192.168.20.33 geco.ritm-edc.net` above the IPv6 capable hosts
