# **Python Application Development Using Pipenv** #
 <!--images-->
![Getting Started](pipenv1.png)

**Pipenv** is a packaging tool for Python that solves some common problems associated with the typical workflow using pip, virtualenv, and the good old requirements.txt.
In addition to addressing some common issues, it consolidates and simplifies the development process to a single command line tool. Pipenv is a tool that aims to bring the best of all packaging worlds (bundler, composer, npm, cargo, yarn, etc.) to the Python world. Windows is a first–class citizen, in our world. It automatically creates and manages a virtualenv for your projects, as well as adds/removes packages from your Pipfile as you install/uninstall packages. It also generates the ever–important Pipfile.lock, which is used to produce deterministic builds.

The problems that Pipenv seeks to solve are multi-faceted:
-	You no longer need to use pip and virtualenv separately. They work together.
-	Managing a requirements.txt file can be problematic, so Pipenv uses the upcoming Pipfile and Pipfile.lockinstead, which is superior for basic use cases.
-	Hashes are used everywhere, always. Security. Automatically expose security vulnerabilities.
-	Give you insight into your dependency graph (e.g. $ pipenv graph).
-	Streamline development workflow by loading .env files.
### **Installation** ###
If you're on MacOS, you can install Pipenv easily with Homebrew:
```{r, engine='shell', count_lines}
$ brew install pipenv
```
Or, if you're using Ubuntu 17.10:
```{r, engine='shell', count_lines}
$ sudo apt install software-properties-common python-software-properties
$ sudo add-apt-repository ppa:pypa/ppa
$ sudo apt update
$ sudo apt install pipenv
```
Otherwise, just use pip:
```{r, engine='shell', count_lines}
$ pip install pipenv
```

### **Features** ###
-	 Enables truly deterministic builds, while easily specifying only what you want.
-	 Generates and checks file hashes for locked dependencies.
-	 Automatically install required Pythons, if pyenv is available.
-	 Automatically finds your project home, recursively, by looking for a Pipfile.
-	 Automatically generates a Pipfile, if one doesn't exist.
-	 Automatically creates a virtualenv in a standard location.
-	 Automatically adds/removes packages to a Pipfile when they are un/installed.
-	 Automatically loads .env files, if they exist.

The main commands are install, uninstall, and lock, which generates a Pipfile.lock. These are intended to replace ```pip install``` usage, as well as manual virtualenv management (to activate a virtualenv, run ```pipenv shell```).

### **Basic Concepts** ###
-	 A virtualenv will automatically be created, when one doesn't exist.
-	 When no parameters are passed to install, all packages [packages] specified will be installed.
-	 To initialize a Python 3 virtual environment, run  ```pipenv --three```.
-	 To initialize a Python 2 virtual environment, run ```pipenv --two```.

##### Other Commands #####
-	 ```shell``` will spawn a shell with the virtualenv activated.
-	 ```run``` will run a given command from the virtualenv, with any arguments forwarded (e.g. ```pipenv run python```).
-	 ```check``` asserts that PEP 508 requirements are being met by the current environment.
-	 ```graph``` will print a pretty graph of all your installed dependencies.

### **Shell Completion** ###
For example, with fish, put this in your  ~/.config/fish/completions/pipenv.fish:
``` eval (pipenv --completion) ```

Alternatively, with bash, put this in your .bashrc or .bash_profile:
``` eval "$(pipenv --completion)" ```

Magic shell completions are now enabled! There is also a fish plugin, which will automatically activate your subshells for you. Fish is the best shell. You should use it. 
Pipenv is primarily meant to provide users and developers of applications with an easy method to setup a working environment. 