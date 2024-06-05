# Installation hints

Some notes on installation of various tools, as part of the Carney Computational Fluency Short Course at Brown University.  *These are not comprehensive instructions*, and are intended only to provide suggestions and point to online resources. Contact course staff if you need help.

## Python

We suggest installing the [Anaconda distribution](https://www.anaconda.com/products/distribution) as a good starting place for learning to use python for science (note the tiny "Skip Registration" button if you do not want to give your email address). There are leaner ways to install python, but for most scientists the convenience is more important than the size.

`Anaconda Navigator` is a specialized launcher app that comes installed with the Anaconda distribution, but you can use python without it. You may or may not prefer this particular GUI interface to start new projects.

Installing Anaconda will also install the general tool `conda`, which handles package management and virtual environments.

## Making an account on GitHub

[GitHub](https://github.com) is the biggest online platform for sharing code repositories, but it is not the only one, and you can use the version control tool `git` without using GitHub (there is no formal relationship between the tool itself and the online platforms). However, you will likely want to make an account on GitHub in order to be able to "push" code from your computer and/or contribute to other projects. We will assume you have a GitHub account, which you can make through the link.

## Shells, command lines, terminals

We will often make reference to typing commands into a "shell" or a "command line" or a "terminal". 

On **Mac** you should use the Terminal application, which you can find by searching in Spotlight, or opening `Applications > Utilities > Terminal`. You should not need to install anything.

**Linux** distributions (e.g. Ubuntu) also generally have a Terminal application. You should not need to install anything.

If you are on **Windows**, we recommend using [PowerShell](https://learn.microsoft.com/en-us/powershell/scripting/what-is-windows-powershell); try running PowerShell from the Start menu, and if it does not work, follow the link for installation instructions.

When you open a shell or terminal application, you should get a window with a prompt, waiting for you to type commands.

## Git

`git` is by far the most dominant version control system, and we will discuss it extensively in the short course. General information can be found at [https://git-scm.com](https://git-scm.com), including installation instructions for different OS and documentation. 

### Check if `git` is installed

Before attempting to install `git`, check if you already have it. On Mac or Linux open a terminal and type:
```shell
which git
```
On Windows open PowerShell and type
```shell
where.exe git
```
If a path to a git executable is returned, you may already have it installed and can skip the next subsection. However, you should still try an alternative way to check by opening a shell and typing
```shell
git --version
```
You will see a clean message with version number if `git` is installed, or an error message similar to `Command not found` if not. On Macs, this command may show a warning that more installation is required; follow the instructions.

### Install `git`

For **Mac** installation we suggest using the version that comes with `Xcode` (though see below on GitHub Desktop). A direct way to install the `Xcode` command line tools is to open a terminal and type
```shell
xcode-select --install
```
This can take a while, and it may prompt you for more information. Alternatively, you can install `Xcode` using the App Store (*not* going to the webpage) under the top left Apple menu. This will also take a while, and use up more disk space. `Xcode` is a massive package with a lot of tools to develop software for Apple products beyond the command line tools. However, this approach is "native", includes other useful tools (like the `clang` compiler), provides software updates, etc. If you would rather have a leaner manual install of just `git`, see the SCM link below.

Many *Linux* distributions already have a version of `git` installed, or can do so through the OS's package manager.

For *Windows*, one can follow the instructions to install a third party GUI in the next paragraph, or install [Git for Windows](https://git-scm.com/download/win) from the SCM site.

Various third parties offer graphical interfaces, for example [GitHub Desktop](https://desktop.github.com), that wrap around the core `git` tool. This may be the preferred option for **Windows**, and can be used on Mac or Linux if you would like to have a GUI interface.

There are further installation options at the [git-scm downloads](https://git-scm.com/downloads) page. Also note that many IDEs provide ways to use `git` internally; you can set these up, but will still want to have a way to access `git` directly for the course.

## R

You do not need R for the short course, but if you would like to install it, we suggest installing [RStudio](https://posit.co/products/open-source/rstudio/), which is an IDE that wraps around the core R computational kernel.

## Matlab

You do not need Matlab for the short course, but it remains a popular application in brain science, and we will refer to it from time to time. As a commercial, closed source application, Matlab requires a paid license, and you should check your home institution for student software availability.




