# Basics of virtual environments

Virtual environments keep track of your code "dependencies", which is the set of other software needed to run your code, and isolate dependencies across projects so they don't conflict. If you send someone else your code without those dependencies, there's a good chance your code won't work on their system.

Rather than send someone a full copy of your operating system (which is close to what a *container* does), it is often enough to list in a very precise way (that is, precise to a computer) what other code their system might need. This is an approximate way to communicate dependencies, and sometimes fails, but has the virtue of being efficient (only a small "environment" needs to be included in your repo) and descriptive (you explicitly describe what you used, rather than send some incomprehensible mess of code).

There are really two things happening here: *package management*, which installs new software while solving for all the dependencies, and *environment* management, which keeps packages organized such that one switch between multiple, possibility mutually incompatible, sets of software.

### Using `conda` for virtual environments

If you have `conda` on your system, you can make a virtual environment with a command like
```
conda create -n fmri_analysis numpy pandas matplotlib
```
This tells `conda` to create a new virtual environment named `fmri_analysis` (that's what the `-n` otpion does), and to include in that environment the packages `numpy`, `pandas`, and `matplotlib`, assuming it can find them at expected locations online. Note `conda` will also install *all packages that those packages depend on*, and `conda` may also need to make changes to other packages already on your system, if the versions do not match. This is a complicated process, which is why most of the time we want to let the package managers sort it out if they can.

If you are currently in a virtual environment, you can make a file that describe the environment with
```
conda env export -f environment.yml
```
This will make a new file `environment.yml` (in the current working directory) that lists all the packages in the current environment. If you send that file to someone else, they can recreate your environment with
```
conda env create -f environment.yml
```
Note the `env` invocation of the "environment" module (it is included when creating from an environment file but not when creating from a command line list of packages). This create command does not include a name for the virtual environment; the name is listed inside the `environment.yml` file, and that is the name `conda` will use.

One useful pro-trick is to export a list of just the packages you actually requested, not including all the other packages `conda` installs to satisfy the dependencies:
```
conda env export --from-history -f environment_minimal.yml
```
This will also make a file that can be used with "create", but will list only the packages you explicitly requested. In the above `fmri_analysis` example, the file `environment_minimal.yml` would list just the packages  `numpy`, `pandas`, and `matplotlib`, while the file `environment.yml` would list a bewildering array of many, many packages including detailed version numbers.

We suggest including both types of environment files in your repos. The more explicit version is needed for reproducibility, but if anything goes wrong, the minimal version communicates what you intended to set up.

### Adding new packages

If an environment already exists and **it is currently activated**, you can add new packages to it with


```
conda install <PACKAGENAME>
```

Again, this will install packages in whatever the currently active environment is.

It is good practice to export a new environment file after changes, so that the file remains accurate.


### Other environment and installation choices

While `conda` is accessible and popular, there are other options to do the same kind of work. Some people have strong opinions about these sorts of things, and there are real differences between the options. Not every package is available through every package manager, some are much faster and/or efficient than others, and so on.

Th most common alternative is `pip`, which does the package management and installation part. To keep things organized in environments, one uses `venv`.

*Note*: `conda` and `pip` sometimes do not play nice together; try to avoid using them in the same environment. If you must use both (for example, because they have access to different packages), best practice is to finish all `conda` installs, and use `pip` only at the end.

More recent tools like `poetry` improve on usability and robustness, and try to slant towards *project* management instead of just *package* management.



