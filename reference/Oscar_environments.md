# Setting up a conda environment on Oscar

Using Oscar's OpenOnDemand is typically much easier than setting up older interfaces, such as ssh. However, there is an additional step to getting notebooks working in custom virtual environments, due to the automated way the notebook is launched (not from typing `jupyter lab` in a terminal with the desired environment activated).

In order to make the environment available, first create it, by typing the following in OOD's Terminal app:
```
conda create -n <ENV_NAME> <YOUR_PACKAGES>
```
making sure to include `jupyter` among the packages. You can of course alternatively use an environment file, as discussed in the course and the [virtual environment reference](Virtual_environments.md), but the environment file must include jupyter.

Then activate the environment, and "associate" the new environment with the ipykernel that runs underneath the Jupyter interface:
```
conda activate <ENV_NAME>
python -m ipykernel install --user --name=<ENV_NAME>
```

When you go back to OOD's Dashboard, select "Basic Jupyter Notebook with Anaconda", and enter the environment name <ENV_NAME> in the first text box (called "Conda Env"). In the Jupyter Lab launcher, you should see a notebook icon with your environment name under it; that is the service to launch.

If you launched a notebook instead, look for the kernel name in the top right (it usually says something like `Python3`). If you click it, you should see a drop down menu with other options, include your desired environment.

