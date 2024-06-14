# Setting up a conda environment on Oscar

Using Oscar's OpenOnDemand (OOD) is typically much easier than setting up older interfaces, such as ssh. However, there is an additional step to getting notebooks working in custom virtual environments, due to the automated way the notebook is launched (not from typing `jupyter lab` in a terminal with the desired environment activated).

## Reloading `conda` from `miniconda`

Loading an anaconda module will make the standard conda command available, but it will not work properly on Oscar. Instead, CCV instructions say to load the streamlined version of the installer called `miniconda`. From the OOD Dashboard, open the "**Oscar Shell**" app, which should put you in a terminal after you enter login credentials. Then type:
```
module load miniconda3/23.11.0s
source /oscar/runtime/software/external/miniconda3/23.11.0/etc/profile.d/conda.sh
```
After this, the `conda` command should work as normal.

## Setting up the environment

If you have already made an environment, skip to the next paragraph (note the environment must contain `jupyter`). To make a new environment available, first create it via the shell:
```
conda create -n <ENV_NAME> <YOUR_PACKAGES>
```
making sure to include `jupyter` among the packages. You can of course alternatively use an environment file, as discussed in the course and the [virtual environment reference](Virtual_environments.md), but the environment file must include `jupyter`.

Then activate the environment, and "associate" the new environment with the ipykernel that runs underneath the Jupyter interface:
```
conda activate <ENV_NAME>
python -m ipykernel install --user --name=<ENV_NAME>
```

## Using the environment when launching Jupyter 

Go back to OOD's Dashboard, select "**Basic Jupyter Notebook with Anaconda**", and enter the environment name <ENV_NAME> in the first text box (called "Conda Env"). In the Jupyter Lab launcher, you should see a notebook icon with your environment name under it; that is the service to launch.

If you launched a notebook instead, look for the kernel name in the top right of the notebook (it usually says something like `Python3`). If you click the label, you should see a menu with other kernel options, including your new environment.
