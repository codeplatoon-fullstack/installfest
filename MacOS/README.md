# MacOS Installfest

## Prerequisites

- Make sure you have an Apple ID
- Make sure you already have created an account with Github
- Ensure that you're running the most recent operating system. You can check your version by going to:

```
System Settings -> General -> Software Update
```

## What we'll cover

We are going to install everything that you will need for this course. Please do this in order!

1. Terminal
2. Visual Studio Code & `code`
3. Package Management
4. Python
5. Node
6. Git
7. Alisases
8. PostgreSQL
9. VSCode Extensions

## Terminal

MacOS has a default terminal application called Terminal. This will suffice, but if you are looking for a more customizable alternative [iterm2](https://iterm2.com/) is a popular choice.

Modern macs will default to using `zsh` as your main shell, and the next instruction will guarantee it even if you are on an older mac, so we will assume this default throughout the instructions.

### oh-my-zsh

Whether you're on an older or modern Mac, we recommend you download a piece of software call [oh-my-zsh](https://ohmyz.sh/). This will guarantee you are indeed using zsh, will give you terminal colors for free, and will prepopulate a file called `.zshrc` which customizes how your shell runs, and we will need to make some adjustments here to make everything work.

This command is more easily copy/pasted from [oh-my-zsh's own site](https://ohmyz.sh/#install) but it is reproduced below:

```bash
$ sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

> It isn't important to understand the details but `sh` is a specific shell (the default on older macs) and `curl` is a program that allows us to install a file from a url.

After this runs you should notice your terminal has colors now. There is also a file call `.zshrc` in your home directory (`~`) now, and we will return to this in a moment.

## Visual Studio Code & `code`

There are many IDEs (integrated development environments) out there that developers can use. For our class, we're going to be using Visual Studio Code, a free IDE created by Microsoft. VSCode is a powerful, flexible editor that supports many different coding languages. VSCode is also highly extensible, with a rich ecosystem of plugins.

This installs the Command Line Tools package via the Terminal application. This is to ensure you have it installed correctly and in the correct path.

- Download [Visual Studio Code](https://code.visualstudio.com/download) and click on the Mac installer. This will hopefully figure it out on its own but the version it picks will differ based on if your computer has an Intel chip or the more modern Apple Silicon chipset, so if you run into errors at this step this is likely the reason why.
- Once VSCode is successfully installed, please ensure that VSCode could be found inside your Applications folder. If it isn't in your `Applications`, it will be located under `Downloads`. Grab the VSCode application and drag it into your `Applications` folder.
- Open VSCode and open the `Command Palette` by pressing (Cmd + Shift + P)
- Type `shell command` into the Command Palette and click on the following option: `Shell Command: Install 'code' command in PATH`
- Close VSCode
- This will allow you to open VSCode from the terminal using the command `code` like so:

```bash
# to simply open VSCode from the command line, type 'code'
$ code
# to open a specific file, specify it as the first argument to `code`
$ code myfile.txt
# to open the current folder
$ code .
```

Test that this `code` command actually works before moving on. You may need to close and reopen your terminal.

> A note about extensions: You are free to install any/all extensions you find on the VSCode marketplace as they suit you and we will be recommending some throughout the course. That said, I want to strongly advise you to _not_ install any AI code-completion tool like Github Copilot or Micrsoft's IntelliCode. Your goal in this course is to learn to program and these tools tend to interfere with that process by giving you regular autocompletion options that are not accurate solutions to the problem at hand. These tools have their place, but it is generally a bad habit to copy/paste code you do not understand yourself and these tools make that a seamless process, so please do avoid them for the duration of this course.

## Package Management

[Homebrew](https://brew.sh/) is a package manager for MacOS. You can install it by running the following command (more easily copy/pasted from their website):

```bash
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

> It isn't important to understand the details but `bash` is a specific shell (the default on older macs) and `curl` is a program that allows us to install a file from a url.

It is not necessary that you read the output but **Homebrew will be installing XCode Command Line Tools first if you do not already have it. This is required for git and other command line programs.** This might take a fair bit of time (up to 15 minutes), but it's a welcome improvement from the previous solution of downloading all of XCode (Apple's one stop shop for doing development on a Mac) which is far larger (up to 3 hours).

Let's check if we've installed homebrew correctly. You may need to close and reopen your terminal first.

```bash
$ brew
```

If you see a list of further options it is working. If you are getting a message that the command is not found something went wrong.

Homebrew is going to do a lot of work for us in that it manages our software versions, so always ensure that it's up-to-date and that it's healthy. First run:

```bash
# grabs a list of all the current packages you can install
$ brew update
```

then:

```bash
$ brew doctor
```

`brew doctor` may tell you a lot of stuff and if it's complex you will want to reach out to one of us. We're ideally shooting for a message like this:

```bash
$ brew doctor
# Your system is ready to brew.
```

Warnings are good to read but are not mandatory to fix, so continue on for now and reach out if you hit a snag down the line.

#### Confirm XCode Command Line Tools is Installed

Finally, let's check that XCode Command Line Tools has been installed.
```bash
$ clang --version
```

You should see a message with version information and a directory path showing where clang is installed. clang is a C compiler installed by XCode Command Line tools. If we are able to run it to check it's version, that tells us XCode Command Line Tools has been successfully installed. 

If you do not see any message, try [installing XCode Commmand Line Tools manually]([XCode Command Line Tools](https://mac.install.guide/commandlinetools/4.html):
```bash
$ xcode-select --install
```

Then try the previous verification step. If that does not work, reach out for help.


### Modifying `~/.zshrc`

A recent MacOS update altered things slightly so that, even though Homebrew has been installed correctly, the place where it installs software will not be 'picked up' by default anymore. To fix this, let's open and modify the file `~/.zshrc` which allow you to customize how your shell is configured on startup. Open it with:

```bash
$ code ~/.zshrc
```

Because we downloaded `oh-my-zsh` earlier, this file should already be prepopulated, with a lot of comments (lines starting with `#`) and a few actual lines of code. This is in a language called `bash` or 'shell script' and you aren't expected to understand it, so copy/pasting will suffice.

At the very top of this file we are going to add a line that will update our `PATH` variable. `PATH` is a global variable throughout the entire shell that defines what folders to look in when searching for pre-existing commands. Homebrew by default adds it's downloads to a folder called `/usr/local/bin`, but this isn't already on the `PATH`, so let's add it. At the top of the file add the line below, then save:

```bash
export PATH=$PATH:/usr/local/bin
```

Now close VSCode and restart your terminal.

> Alternatively, you don't need to close your terminal but you can run the below command to force your terminal to rerun `~/.zshrc`
>
> ```bash
> $ source ~/.zshrc
> ```

## Python

Python3 actually comes pre-installed on modern Macs but you won't be able to control the version of this copy, so we are going to use Homebrew to get a copy we do have complete control over. First, run the following code below and note the output:

```bash
$ which python3
```

`which` is a command that tells us where a given command is located in the filesystem. The result should be '/usr/bin/python3'.

Now, install an up-to-date version of Python3 from your terminal by running:

```bash
$ brew install python
```

Test that you have the correct version asscoiated with the command `python3` by running the code below:

```bash
$ which python3
```

The result should be '/usr/local/bin/python3'. If it's not, speak to an instructor or TA because your Homebrew installations are not being correctly picked up.

This install should also include python's package manager, `pip`. To test this enter the command:

```bash
$ python3 -m ensurepip
```

If it wasn't, the above command will download it. Now type:

```bash
$ pip3
```

As long as the `pip3` command is recognized, you are good.

### Python Virtual Environment

Python uses the concept of a 'virtual envrionment' to install packages through pip uniquely for a given project. Create a new project with a Python virtual environment like so:

```bash
$ python3 -m venv test_project
```

If it works this will create a new folder in your current directory called 'test_project'. Inside that folder we should see a bin folder holding an `activate` script, a `pip` script, and several others. Ensure both the `activate` and `pip` scripts are present. Do so with:

```bash
$ ls test_project/bin
```

To delete the `test_project` folder at this point type:

```bash
rm -rf test_project
```

## Node

In this section, we'll use Homebrew to install `npm`, the default package manager for node. We'll then use `npm` to install `n`, which is a tool to help manage different versions of `node`. Lastly, we'll use `n` to install the latest stable version of `node`.

```bash
# use apt to install npm
$ brew install npm
# use npm to install n (-g means globally, as opposed to in a specific project/folder)
$ sudo npm install -g n
# use n to install the latest stable version of node
$ sudo n stable
```

Close and reopen your terminal if necessary and test that both the commands `node` and `npm` are recognized.

## `git`

Git may or may not be install by default on your system, but to make sure use `brew` to install it.

```bash
$ brew install git
```

Next, we'll configure Git with sensible defaults:

```bash
$ git config --global user.name "<YOUR_NAME>"
$ git config --global user.email "<YOUR_EMAIL>"
```

We also want to make sure that when committing we open the commit message prompt in VSCode (default will be `vim` and you will not like it):

```bash
git config --global core.editor code
```

You can confirm git is configured correctly by running

```bash
$ git config --global -l
```

You should see that your username, email, and editor are all listed.

### Github and `gh`

Github's preferred way you interact with it now is a command line tool called `gh`. First, you will need a github account to continue, then, in your terminal type:

```bash
$ brew install gh
```

Once downloaded type:

```bash
$ gh auth login
```

and follow the wizard steps to complete the authentication process (the default choices are what you want). When done you should be able to clone a repo like so:

```bash
$ gh repo clone codeplatoon-fullstack/installfest
```

This will install that repo in your current directory. Assuming this is successful if you want to delete it afterwards type:

```bash
$ rm -rf installfest
```

## Alisases

We are going to modify `~/.zshrc` again so that we don't need to type `python3` but just `python` to invoke the correct program. This is a small change but it's a way of making it clear what your 'default' version is on a platform, and also an opportunity to discuss the concept of aliases.

Open `~/.zshrc` in VSCode like so:

```bash
$ code ~/.zshrc
```

VSCode should open the document. At the bottom of the file add the lines:

```bash
alias python='python3'
alias pip='pip3'
```

Aliases are what they sound like, simply a new name that points to an existing command. If you are ever in doubt what a given alias points to type:

```bash
which <COMMAND>
```

If `<COMMAND>` is an alias, it will tell you what it points to. If `<COMMAND>` is a real command it will tell you what its full path is in the file system.

These aliases won't automatically be applied in your current terminal, but they will take effect in any new terminal windows you open. Alternatively if you don't want to close/open your terminal you can force the terminal to re-read the newly updated file with:

```bash
$ source ~/.zshrc
```

## PostgreSQL

### The Recommended Way
By far the easiest way to install PostgreSQL on Mac OS X is the the excellent [postgresapp](https://postgresapp.com/). This should set up postgres to be used from the command line and also gives you a GUI if desired. **We highly recommend installing this way on Mac.**

### Installing with Package Manager (Not Recommended).
If you have a specific reason to, here is how to install PostgreSQL using a package manager.

We will now install PostgreSQL by running the following command:

```bash
$ brew install postgresql
```

Start a PostgreSQL instance (in the background) like so:

```bash
$ brew services restart postgresql@14
```

To enter PostgreSQL we will switch our shell user to one named `postgres`, and then we can enter the running PostgreSQL instance.

```bash
# connect to the running PostgreSQL instance as the user 'postgres'
$ psql postgres
```

If your terminal now looks like it does below, you have succesfully installed PostgreSQL:

```
postgres=#
```

To exit out of this enviroment type

```
postgres=# \q
```

## VSCode Extensions

### Python

Open VSCode and create a new file called `example.py`. This will be enough for VSCode to prompt you to download it's official Python extension. If this doesn't happen for whatever reason, you can select the extension tab on the left pane and search for 'python' and download the one made by Microsoft (it should be the top result). You will know this was succesful if afterwords you can write some simply Python code like:

```py
print("hello")
```

and when you hover over the print function with your mouse pointer VSCode gives you some intellisense (essentially in-line documentation about what that bit of code does).

### Live Share

Live Share is another official Microsoft extension that will allow us as instructors and TAs to collaborate with you VSCode in real-time, which can be very helpful when troubleshooting a tricky bug. Search the extensions store for 'Live Share' and make sure it is published by Microsoft and download it. We won't expect you to set it up at this point but it is good enough to have it already installed for now.
