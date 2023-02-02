# MacOS Installfest

## Prerequisites

- Make sure you have an Apple ID
- Make sure you already have created an account with Github
- Ensure that you're running the most recent operating system. You can check your version by going to:

```
System Settings -> General -> Software Update
```

- We will repeat this step in the XCode section if not already done, but if you can search the App Store for XCode and start downloading it now, as this can be a time consuming step.

## What we'll cover

We are going to install everything that you will need for this course. Please do this in order!

1. Terminal
2. XCode
3. Visual Studio Code & `code`
4. Package Management
5. Python
6. Node
7. Git
8. Alisases
9. PostgreSQL
10. VSCode Extensions

## Terminal

MacOS has a default terminal application called Terminal. This will suffice, but if you are looking for a more customizable alternative [iterm2](https://iterm2.com/) is a popular choice.

Modern macs will default to using `zsh` as your main shell, so we will assume this throughout the instructions, but if `bash` is the default on your system we will note when that difference matters. If you are in doubt what shell you are using type this into your terminal and note the result:

```zsh
$ echo $SHELL
```

## XCode

- If you don't already have it installed, go to the App Store, search for XCode, and install it. This can take a very long time, and is quite large but unfortunately necessary to do software development on a mac.

Once Xcode is installed (you may be prompted to restart first) run the following command in the terminal.

```zsh
$ xcode-select --install
```

You may also be prompted to first accept the xcode license agreement, which will require you to input:

```zsh
$ sudo xcodebuild -license
```

and then when prompted to type 'agree' followed by enter.

> A note on the `sudo` command: Some commands (especially ones involved in downloading new software) require elevated permission compared to what a regular user normally posesses. This is a somewhat advanced topic to go into detail about, but the basic solution to temporarily elevating one's permissions is to use the command `sudo`. `sudo` stands for Super User DO and is a way of temporarily elevating the current user's permissions by first prompting them for their password (it's the same password you use to login).

## Visual Studio Code & `code`

There are many IDEs (integrated development environments) out there that developers can use. For our class, we're going to be using Visual Studio Code, a free IDE created by Microsoft. VSCode is a powerful, flexible editor that supports many different coding languages. VSCode is also highly extensible, with a rich ecosystem of plugins.

This installs the Command Line Tools package via the Terminal application. This is to ensure you have it installed correctly and in the correct path.

- Download [Visual Studio Code](https://code.visualstudio.com/download) and click on the Mac installer. This will hopefully figure it out on its own but the version it picks will differ based on if your computer has an Intel chip or the more modern Apple Silicon chipset, so if you run into errors at this step this is likely the reason why.
- Once VSCode is successfully installed, please ensure that VSCode could be found inside your Applications folder. If it isn't in your `Applications`, it will be located under `Downloads`. Grab the VSCode application and drag it into your `Applications` folder.
- Open VSCode and open the `Command Palette` by pressing (Cmd + Shift + P)
- Type `shell command` into the Command Palette and click on the following option: `Shell Command: Install 'code' command in PATH`
- Close VSCode
- This will allow you to open VSCode from the terminal using the command `code` like so:

```zsh
# to simply open VSCode from the command line, type 'code'
$ code
# to open a specific file, specify it as the first argument to `code`
$ code myfile.txt
# to open the current folder
$ code .
```

Test that this `code` command actually works before moving on. You may need to close and reopen your terminal.

> A note about extensions: You are free to install any/all extensions you find on the VSCode marketplace as they suit you and we will be recommending some throughout the course. That said, I want to strongly advise you to _not_ install any AI code-completion tool like Github Copilot or Tabnine. Your goal in this course is to learn to program and these tools tend to interfere with that process by giving you regular autocompletion options that are not accurate solutions to the problem at hand. These tools have their place, but it is generally a bad habit to copy/paste code you do not understand yourself and these tools make that a seamless process, so please do avoid them for the duration of this course.

## Package Management

[Homebrew](https://brew.sh/) is a package manager for MacOS. You can install it by running the following command (more easily copy/pasted from their website):

```zsh
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

> It isn't important to understand the details but `bash` is a specific shell (the default on older macs) and `curl` is a program that allows us to install a file from a url.

Let's check if we've installed homebrew correctly. You may need to close and reopen your terminal first.

```zsh
$ brew
```

If you see a list of further options it is working. If you are getting a message that the command is not found something went wrong.

Homebrew is going to do a lot of work for us in that it manages our software versions, so always ensure that it's up-to-date and that it's healthy. First run:

```zsh
# grabs a list of all the current packages you can install
$ brew update
```

then:

```zsh
$ brew doctor
```

`brew doctor` may tell you a lot of stuff and if it's complex you will want to reach out to one of us. We're ideally shooting for a message like this:

```zsh
$ brew doctor
# Your system is ready to brew.
```

Warnings are good to read but are not mandatory to fix, so continue on for now and reach out if you hit a snag down the line.

## Python

MacOS will have a `python` command installed by default but it will be Python 2.7, which we do not use in this course and as of January 2023 is no longer even supported.

Install an up-to-date version of Python3 from your terminal by running:

```zsh
$ brew install python
```

test that you now have a command called `python3` installed. Later we will make is so typing `python` invokes this command.

This install should also include python's package manager, `pip`. To test this enter the command:

```zsh
$ python3 -m ensurepip
```

followed by:

```zsh
$ pip3
```

As long as the `pip3` command is recognized, you are good.

### Python Virtual Environment

Python uses the concept of a 'virtual envrionment' to install packages through pip uniquely for a given project. Create a new project with a Python virtual environment like so:

```zsh
$ python3 -m venv test_project
```

If it works this will create a new folder in your current directory called 'test_project'. Inside that folder we should see a bin folder holding an `activate` script, a `pip` script, and several others. Ensure both the activate and pip scripts are present. Do so with:

```zsh
$ ls test_project/bin
```

If you would like to delete it at this point type:

```zsh
rm -rf test_project
```

## Node

In this section, we'll use `apt` to install `npm`, the default package manager for node. We'll then use `npm` to install `n`, which is a tool to help manage different versions of `node`. Lastly, we'll use `n` to install the latest stable version of `node`.

```zsh
# use apt to install npm
$ brew install npm
# use npm to install n (-g means globally, as opposed to in a specific project/folder)
$ sudo npm install -g n
# use n to install the latest stable version of node
$ sudo n stable
```

Close and reopen your terminal if necessary and test that both the commands `node` and `npm` are recognized.

## `git`

Git may or may not be install by defaullt on your system, but to make sure use `brew` to install it.

```zsh
$ brew install git
```

Next, we'll configure Git with sensible defaults:

```zsh
$ git config --global user.name "<YOUR_NAME>"
$ git config --global user.email "<YOUR_EMAIL>"
```

We also want to make sure that when committing we open the commit message prompt in VSCode (default will be `vim` and you will not like it):

```zsh
git config --global core.editor code
```

You can confirm git is configured correctly by running

```zsh
$ git config --global -l
```

You should see that your username, email, and editor are all listed.

### Github and `gh`

Github's preferred way you interact with it now is a command line tool called `gh`. First, you will need a github account to continue, then, in your terminal type:

```zsh
$ brew install gh
```

Once downloaded type:

```zsh
$ gh auth login
```

and follow the wizard steps to complete the authentication process (the default choices are what you want). When done you should be able to clone a repo like so:

```zsh
$ gh repo clone codeplatoon-fullstack/installfest
```

This will install that repo in your current directory. Assuming this is successful if you want to delete it afterwards type:

```zsh
$ rm -rf installfest
```

## Alisases

Every time you open your terminal a special file will automatically be read from to do any necessary 'setup' type work. Assuming the terminal you are using is `zsh` this file will be called `.zshrc`. If you are using `bash` (the default on older macs) it will be `.bash_profile`. If you are unsure what terminal you are running type:

```zsh
$ echo $SHELL
```

Open this file in VSCode like so:

```zsh
$ code ~/.zshrc
```

or alternatively if you are running `bash`:

```zsh
$ code ~/.bash_profile
```

VSCode should open the document. If you didn't have a `.zshrc` or `.bash_profile` before, it'll be empty. Either way, paste the code below at the bottom of your profile:

```zsh
alias python='python3'
alias pip='pip3'
```

Aliases are what they sound like, simply a new name that points to an existing command. If you are ever in doubt what a given alias points to type:

```zsh
which <COMMAND>
```

If `<COMMAND>` is an alias, it will tell you what it points to. If `<COMMAND>` is a real command it will tell you what its full path is in the file system.

These aliases won't automatically be applied in your current terminal, but they will take effect in any new terminal windows you open. Alternatively if you don't want to close/open your terminal you can force the terminal to re-read the newly updated file with:

```zsh
$ source ~/.zshrc
```

## PostgreSQL

We will now install PostgreSQL by running the following command:

```zsh
$ brew install postgresql
```

Start a PostgreSQL instance (in the background) like so:

```zsh
$ brew services restart postgresql@14
```

To enter PostgreSQL we will switch our shell user to one named `postgres`, and then we can enter the running PostgreSQL instance.

```zsh
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
