## Anaconda and Snakemake Setup & Installation
Follow these steps to set up the environment on a Linux system or HPC.

### 1. Install or Update Anaconda
Download and run the installer. We use the -u flag to ensure that if Anaconda is already present, it updates correctly rather than throwing an error for your architecture.

For x86_64 (Standard Intel/AMD):
```Bash
curl -O https://repo.anaconda.com/archive/Anaconda3-2025.12-2-Linux-x86_64.sh

bash Anaconda3-2025.12-2-Linux-x86_64.sh -b -u
```
For ARM64 (Apple Silicon/Graviton):
```Bash
curl -O https://repo.anaconda.com/archive/Anaconda3-2025.12-2-Linux-aarch64.sh

bash Anaconda3-2025.12-2-Linux-aarch64.sh -b -u
```
> Note: The -b flag automates the install, and -u updates any existing installation at ~/anaconda3.

### 2. Initialize the Environment
Refresh your shell to recognize the conda command:
```Bash
source ~/anaconda3/bin/activate
conda init
```
Close and reopen your terminal after running this.

### 3. Setup Channels & Snakemake
We use a dedicated environment and strict channel priorities to ensure tool compatibility. We prioritize conda-forge and bioconda as required for bioinformatics tools.

```Bash
# Set up bioinformatics channels
conda config --add channels conda-forge
conda config --add channels bioconda
conda config --set channel_priority strict

# Create the environment (installs Snakemake and dependencies)
conda create -n snakemake snakemake -y

# Activate the environment
conda activate snakemake
```
### 4. Verify Installation

```Bash
snakemake --version
```

Installation Complete: You are now ready to run the pipeline; return to the **[NOSE README](https://github.com/Novel-sp)** to begin with Module 1.
