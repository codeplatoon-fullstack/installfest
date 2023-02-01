# MacOS Installfest

## prerequisites

- Make sure you have an Apple ID
- Download XCode from the Mac App Store (this can take a very long time, and is large)
- Ensure that you're running the most recent operating system. You can check your version by going to:

```
System Settings -> General -> Software Update
```

## What we'll cover

We are going to install everything that you will need for this course. Please do this in order!

1. XCode
2. Visual Studio Code & `code`
3. Package Management
4. Python
5. Node
6. Git
7. Alisases
8. PostgreSQL

## XCode

MacOS has a default terminal application called Terminal. This will suffice, but if you are looking for an alternative [iterm2](https://iterm2.com/) is a popular choice.

Run the following command in the terminal.

```bash
$ xcode-select --install
```

## Visual Studio Code & `code`

There are many IDEs (integrated development environments) out there that developers can use. For our class, we're going to be using Visual Studio Code, a free IDE created by Microsoft. VSCode is a powerful, flexible editor that supports many different coding languages. VSCode is also highly extensible, with a rich ecosystem of plugins.

This installs the Command Line Tools package via the Terminal application. This is to ensure you have it installed correctly and in the correct path.

- Download [Visual Studio Code](https://code.visualstudio.com/download) and click on the Mac installer. This will hopefully figure it out on its own but the version it picks will differ based on if your computer has an Intel chip or the more modern Apple Silicon for the CPU, so if you run into errors at this step this is likely why.
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
```

Test that this `code` command actually works before moving on. You may need to close and reopen your terminal.

> A note about extensions: You are free to install any/all extensions you find on the VSCode marketplace as they suit you and we will be recommending some throughout the course. That said, I want to strongly advise you to _not_ install any AI code-completion tool like Github Copilot or Tabnine. Your goal in this course is to learn to program and these tools tend to interfere with that process by giving you regular autocompletion options that are not accurate solutions to the problem at hand. These tools have their place, but it is generally a bad habit to copy/paste code you do not understand yourself and these tools make that a seamless process, so please do avoid them for the duration of this course.

## Package Management

[Homebrew](https://brew.sh/) is a package manager for MacOS. You can install it by running the following command:

```bash
$ /bin/zsh -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

> It isn't important to understand the details but `zsh` is a specific shell (the default on modern macs but older ones might use bash) and `curl` is a program that allows us to install a file from a url.

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

`brew doctor` may tell you a lot of stuff and if its complex you will want to reach out to one of us. We're ideally shooting for a message like this:

```bash
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

```bash
$ python3 -m ensurepip
```

followed by:

```bash
$ pip3
```

As long as the `pip3` command is recognized, you are good.

### Python Virtual Environment

Python uses the concept of a 'virtual envrionment' to install packages through pip uniquely for a given project. Create a new project with a Python virtual environment like so:

```bash
$ python3 -m venv test_project
```

If it works this will create a new folder in your current directory called 'test_project'. Enter into it with:

```bash
$ cd test_project
```

Inside that folder we should see a bin folder holding an `activate` script, a `pip` script, and several others. Ensure both the activate and pip scripts are present. Do so with:

```bash
$ cd bin
$ ls
```

If you would like to delete it at this point type:

```bash
cd ../..
rm -rf test_project
```

## Node

In this section, we'll use `apt` to install `npm`, the default package manager for node. We'll then use `npm` to install `n`, which is a tool to help manage different versions of `node`. Lastly, we'll use `n` to install the latest stable version of `node`.

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

Git may or may not be install by defaullt on your system, but to make sure use `brew` to install it.

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

You can confirm git is configured correctly by running `git config --global -l`. You should see that your username, email, and editor are all listed.

### Github and `gh`

Github's preferred way you interact with it now is a command line tool called `gh`. First, you will need a github account to continue, then, in your terminal type:

```bash
$ brew install gh
```

Once downloaded type:

```bash
$ gh auth login
```

and follow the wizard steps to complete the authentication process. When done you should be able to close a repo like so:

```bash
$ gh repo clone codeplatoon-fullstack/installfest
```

This will install that repo in your current directory. Assuming this is successful if you want to delete it afterwards type:

```bash
$ rm -rf installfest
```

## Alisases

Every time you open your terminal a special file will automatically be read from to do any necessary 'setup' type work. Assuming the terminal you are using is `zsh` this file will be called `.zshrc`. If you are using `bash` (the default on older macs) it will be `.bash_profile`. If you are unsure what terminal you are running type:

```bash
$ echo $SHELL
```

Open this file in VSCode like so:

```bash
$ code ~/.zshrc
```

or alternatively if you are running `bash`:

```bash
$ code ~/.bash_profile
```

VSCode should open the document. If you didn't have a `.zshrc` or `.bash_profile` before, it'll be empty. Either way, paste the code below at the bottom of your profile:

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

You will still be logged in as the user 'postgres' even after this step, so either close the terminal outright or press `Ctrl-D` to return to the regular terminal environment you began in.

## Resources for Troubleshooting

- [Use VScode with `code`](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line)
- [Homebrew](https://brew.sh)
- [Node and Homebrew](https://changelog.com/posts/install-node-js-with-homebrew-on-os-x)
- [Python and Homebrew](https://docs.python-guide.org/starting/install3/osx/)
- [Alias in .zshrc](https://dev.to/stuartcreed/how-to-add-aliases-to-your-terminal-on-mac-os-53dl)
- [PostgreSQL and Homebrew](https://www.moncefbelyamani.com/how-to-install-postgresql-on-a-mac-with-homebrew-and-lunchy/)
