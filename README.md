## Anaconda and Snakemake Setup & Installation
Follow these steps to set up the environment on a Linux system or HPC.

### 1. Install Anaconda
Download and run the installer for your architecture.

For x86_64:

```Bash
curl -O https://repo.anaconda.com/archive/Anaconda3-2025.12-2-Linux-x86_64.sh

bash Anaconda3-2025.12-2-Linux-x86_64.sh -b
```
For ARM64:

```Bash
curl -O https://repo.anaconda.com/archive/Anaconda3-2025.12-2-Linux-aarch64.sh

bash Anaconda3-2025.12-2-Linux-aarch64.sh -b
```
Note: The -b flag runs the installation in batch mode (automatically accepts terms).

### 2. Initialize Conda
After installation, initialize your shell and restart your terminal:

```Bash
source ~/anaconda3/bin/activate
conda init
```
### 3. Configure Channels & Install Snakemake
We use a dedicated environment to avoid dependency conflicts. We prioritize conda-forge and bioconda as required for bioinformatics tools.

```Bash
# Add required channels
conda config --add channels conda-forge
conda config --add channels bioconda
conda config --set channel_priority strict
```
```Bash
# Create and activate the environment
conda create -n snakemake snakemake -y
conda activate snakemake
```
### 4. Verify Installation

```Bash
snakemake --version
```
