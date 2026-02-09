### The Engine for NOSE: Why Snakemake?
NOSE operates on the logic of a DAG (Directed Acyclic Graph). 

Here is why that matters for your data:<br>
• Directed: Logic flows sequentially; downstream analytical modules (e.g., Metabolic Mapping) are automatically triggered upon the successful generation of upstream dependencies.<br>
• Acyclic: The pipeline architecture prevents circular dependencies, ensuring a deterministic path from input (FASTA) to output (CSV/TSV).<br>
• Graph-Based: Every rule represents a discrete computational node, allowing for granular error tracking and partial workflow resumption.<br>

#### Prerequisites
##### Computational Prerequisites
• Access to a Unix-like system (Linux workstation or HPC server)<br>
• Internet connectivity (required for environment setup and database downloads)<br>
• Sufficient compute resources (CPU and memory requirements vary by module)<br>

##### Software Prerequisites
• Conda (Miniconda or Anaconda) must be installed<br>
• Ability to execute bash scripts (.sh files)<br>
• All workflow execution is handled through Snakemake; no direct code modification is required.<br


#### Anaconda and Snakemake Setup & Installation
Follow these steps to set up the environment on a Linux system or HPC.

##### 1. Install or Update Anaconda
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

##### 2. Initialize the Environment
Refresh your shell to recognize the conda command:
```Bash
source ~/anaconda3/bin/activate
conda init
```
Close and reopen your terminal after running this.

#### 3. Setup Channels & Snakemake
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
##### 4. Verify Installation

```Bash
snakemake --version
```

Installation Complete: You are now ready to run the pipeline; return to the **[NOSE README](https://github.com/Novel-sp)** to begin with Module 1.
