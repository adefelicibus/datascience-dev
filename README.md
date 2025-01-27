
# Data Science personal repository

Repository for data science projects, build, deploy and docs.

# Table of contents

1. [Development environment](#devenv-id)
    
    1.1. [Install miniconda](#install-miniconda-id)

    1.2. [Virtual environments](#venv-id)


## Development environment {#devenv-id}

Create a read-to-use data science environment for Python and R on Linux-based systems.

> The simplest way is to use [Google Colab](https://colab.research.google.com/) environment.

### Install miniconda {#install-miniconda-id}

> Why miniconda?
> By using anaconda, you will install a lot of softwares on the base env and, probably, you will not use most of them. With miniconda, you have to install the minimal set of necessary softwares to work with conda.

Download the latest installer from Miniconda:

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/Miniconda3-latest-Linux-x86_64.sh
```

Execute the miniconda installer following the instructions:

```bash
bash ~/Miniconda3-latest-Linux-x86_64.sh
```

Close your terminal and open again or execute the command:

```bash
source ~/.bashrc
```

You will see a `(base)` prefix in your command line prompt. Also, you can verify the conda installation with the commands:

```bash
which conda
conda list
```

Define some useful conda configurations:

```bash
conda config --add channels conda-forge
conda config --add channels bioconda
```

Finally, install `mamba`, a improved version of conda to solve software dependencies more quickly:

```bash
conda install mamba
```

### Virtual environments {#venv-id}

Virtual environments (or `envs`) are isolated spots where you can install several tools without conflicts with others. Also, you can have different versions of the same software installed in several envs.

It is a best practices to have envs with specific softwares and tools to avoid conflicts and to create reproductive analysis.

I've created several envs with the most essentials data science tools for Python and R:

- Jupyter-lab

With jupyterlab, you have a more powerful IDE for data science development.

```bash
mamba create -n jupyterlab jupyterlab
```

After the install, you can execute jupyterlab with the command:

```bash
conda activate jupyterlab
jupyter-lab
```

A new web-browser window, or tab, will open with the jupyterlab interface.

- Python env with data science tools

Here is the most used python tools for data science, but you can install more if you like:

```bash
mamba create -n pyds python pandas matplotlib seaborn scikit-learn nb_conda_kernels ipykernel plotly polars
```

The next command is necessary to register the conda env for jupyter:
```bash
ipython kernel install --user --name=pyds
```

 - R env with data science tools

 Within jupyterlab you can have several kernels available, which means you can have different notebooks with different kernels. With this command, you can create a env with all R essentials tools for data science:

```bash
mamba create -n rds r-base r-irkernel r-irdisplay nb_conda_kernels r-tidyverse r-tidymodels
```

In order to register the R kernel to jupyter, you can use those commands:
```bash
R
IRkernel::installspec()
q()
```