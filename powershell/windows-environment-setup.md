# Windows Environment Setup

'Set Policy

Set-ExecutionPolicy -Scope CurrentUser
  RemoteSigned

Get-ExecutionPolicy -List

'Setup Chocolately!

$script = New-Object Net.WebClient

$script | Get-Member

$script.DownloadString("https://chocolatey.org/install.ps1")
'Install
iwr https://chocolatey.org/install.ps1 -UseBasicParsing | iex

'Upgrade

choco upgrade chocolatey

'Nano if you please

choco install -y nano

'Python if you please

choco install -y python3

'Check python install
refreshenv
python -V

'Get some pip
python -m pip install --upgrade pip


'Optional - Virtual Environment Installation

Setting up a programming environment provides us with greater control over our Python projects and over how different versions of packages are handled. This is especially important when working with third-party packages.

You can set up as many Python programming environments as you want. Each environment is basically a directory or folder in your computer that has a few scripts in it to make it act as an environment.

Choose which directory you would like to put your Python programming environments in, or create a new directory with mkdir, as in:

mkdir Environments
cd Environments

Once you are in the directory where you would like the environments to live, you can create an environment by running the following command:

python -m venv my_env
Using the python command, we will run the venv library module to create the virtual environment that in this case we have called my_env.

Essentially, venv sets up a new directory that contains a few items which we can view with the ls command:

ls my_env

Together, these files work to make sure that your projects are isolated from the broader context of your local machine, so that system files and project files don’t mix. This is good practice for version control and to ensure that each of your projects has access to the particular packages that it needs.

To use this environment, you need to activate it, which you can do by typing the following command that calls the activate script in the Scripts directory:

my_env\Scripts\activate
Your prompt will now be prefixed with the name of your environment, in this case it is called my_env:


This prefix lets us know that the environment my_env is currently active, meaning that when we create programs here they will use only this particular environment’s settings and packages.
