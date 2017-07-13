# Windows Environment Setup

_A quick and dirty summary for a python programming windows environment setup borrowed from [Lisa Tagliaferri's](https://www.digitalocean.com/community/tutorials/how-to-install-python-3-and-set-up-a-local-programming-environment-on-windows-10) excellently clear tutorial:_

#### Set Policy

```
$ Set-ExecutionPolicy -Scope CurrentUser

$ RemoteSigned
```
_Confirm_
```
$ Get-ExecutionPolicy -List
```

#### Setup Chocolately!
```
$ $script = New-Object Net.WebClient

$ $script | Get-Member

$ $script.DownloadString("https://chocolatey.org/install.ps1")
```
_Install_
```
$ iwr https://chocolatey.org/install.ps1 -UseBasicParsing | iex
```
_upgrade_
```
$ choco upgrade chocolatey
```
_Nano if you please_
```
$ choco install -y nano
```
#### Python
```
$ choco install -y python3
```
_Check python install_
```
$ refreshenv
$ python -V
```
_Upgrade yo pip_
```
$ python -m pip install --upgrade pip
```

#### Optional - Virtual Environment Installation

_Setting up a programming environment provides us with greater control over our Python projects and over how different versions of packages are handled. This is especially important when working with third-party packages._

_You can set up as many Python programming environments as you want. Each environment is basically a directory or folder in your computer that has a few scripts in it to make it act as an environment._

_Choose which directory you would like to put your Python programming environments in, or create a new directory with mkdir, as in:_
```
$ mkdir Environments
$ cd Environments
```
_Once you are in the directory where you would like the environments to live, you can create an environment by running the following command:_
```
$ python -m venv my_env
```
_Using the python command, we will run the venv library module to create the virtual environment that in this case we have called my_\__env._

_Essentially, venv sets up a new directory that contains a few items which we can view with the ls command:_
```
$ ls my_env
```

_Together, these files work to make sure that your projects are isolated from the broader context of your local machine, so that system files and project files don’t mix. This is good practice for version control and to ensure that each of your projects has access to the particular packages that it needs._

_To use this environment, you need to activate it, which you can do by typing the following command that calls the activate script in the Scripts directory:_
```
$ my_env\Scripts\activate
```
_Your prompt will now be prefixed with the name of your environment, in this case it is called my_\__env:_

_This prefix lets us know that the environment my_\__env_ _is currently active, meaning that when we create programs here they will use only this particular environment’s settings and packages._

[Source](https://www.digitalocean.com/community/tutorials/how-to-install-python-3-and-set-up-a-local-programming-environment-on-windows-10)

#### virtualenvwrapper

```
$ pip install virtualenvwrapper-win
```
_Activate Shell Functions_

_Get path_

```
$ which virtualenvwrapper.sh
```

_Add the following to shell startup file:_

```
export WORKON_HOME=$HOME/.virtualenvs   # optional
export PROJECT_HOME=$HOME/projects      # optional
source /usr/local/bin/virtualenvwrapper.sh
```
