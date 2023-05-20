# Linux Installfest

## Prerequisites

- Make sure your system is up to date and run any 'check for updates' command that is built into the OS
- Make sure you already have created an account with Github

## What we'll cover

We are going to install everything that you will need for this course. Please do this in order!

1. Terminal
2. Visual Studio Code & `code`
3. Package Management
4. Python
5. Node
6. Git
7. Aliases
8. PostgreSQL
9. VSCode Extensions

## Terminal

If you are on Linux we are going to assume you already know what a terminal is and have one ready to go.

These instructions are going to assume that your terminal is using `bash` as the main shell, but if `zsh` is the default on your system we will note when that difference matters. If you are in doubt what shell you are using type this into your terminal and note the result:

```bash
$ echo $SHELL
```

## Visual Studio Code & `code`

There are many IDEs (integrated development environments) out there that developers can use. For our class, we're going to be using Visual Studio Code, a free IDE created by Microsoft. VSCode is a powerful, flexible editor that supports many different coding languages. VSCode is also highly extensible, with a rich ecosystem of plugins.

- Download [Visual Studio Code](https://code.visualstudio.com/download) and click on the `.deb` installer (assuming you are on Ubuntu, otherwise you are on your own).
- During install, VSCode will by default ask to add itself to your system's PATH environmental variable - keep this box checked!
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

> A note about extensions: You are free to install any/all extensions you find on the VSCode marketplace as they suit you and we will be recommending some throughout the course. That said, I want to strongly advise you to _not_ install any AI code-completion tool like Github Copilot or Microsoft's IntelliCode. Your goal in this course is to learn to program and these tools tend to interfere with that process by giving you regular autocompletion options that are not accurate solutions to the problem at hand. These tools have their place, but it is generally a bad habit to copy/paste code you do not understand yourself and these tools make that a seamless process, so please do avoid them for the duration of this course.

## Package Management

Advanced Package Tool (APT, or `apt`) is a built-in package manager for Ubuntu that handles the installation, versioning and removal of software.

The `update` command in apt will fetch a list of packages from an external source that are available for download. This list changes frequently so it's important to run the update command before installing anything to ensure you will be fetching the latest package and not an outdated one.

```bash
# update the list of external packages that are available for install
$ sudo apt update
```

## Python

See [installing Python on Ubuntu Linux.](./python.md)

## Node.js

See [Installing node.js on Ubuntu Linux](./node.md)

## `git`

See [Installing git and Github CLI on Ubuntu Linux](./git.md)

## Aliases

Every time you open your terminal a special file will automatically be read from to do any necessary 'setup' type work. Assuming the terminal you are using is `bash` this file will be called `.bashrc`. If you are using `zsh` it will be called `.zshrc`. If you are unsure what terminal you are running type:

```bash
$ echo $SHELL
```

The output of this will tell you what shell you are using, which can differ based on your flavor of Linux.

Open this file in VSCode like so:

```bash
$ code ~/.bashrc
```

VSCode should open with the `.bashrc` as the current document. Paste the code below at the bottom of your profile or under the ```# User specific aliases and functions``` comment: 

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
$ source ~/.bashrc
```

## PostgreSQL

See [Installing Postgres on Ubuntu Linux](./postgres.md)

## VSCode Extensions

### For Python

Open VSCode and create a new file called `example.py`. This will be enough for VSCode to prompt you to download it's official Python extension. If this doesn't happen for whatever reason, you can select the extension tab on the left pane and search for 'python' and download the one made by Microsoft (it should be the top result). You will know this was successful if afterwords you can write some simply Python code like:

```py
print("hello")
```

and when you hover over the print function with your mouse pointer VSCode gives you some intellisense (essentially in-line documentation about what that bit of code does).

### Live Share

Live Share is another official Microsoft extension that will allow us as instructors and TAs to collaborate with you VSCode in real-time, which can be very helpful when troubleshooting a tricky bug. Search the extensions store for 'Live Share' and make sure it is published by Microsoft and download it. We won't expect you to set it up at this point but it is good enough to have it already installed for now.
