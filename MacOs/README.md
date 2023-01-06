
# MacOs Installfest


## What we'll cover
We are going to install everything that you will need for this course. Please do this in order!

1. Visual Studio Code & `code`
2. XCode
3. Homebrew
4. Node.js 
5. Python
6. Adding an Alias
7. PostgreSQL

## Prerequesites

- Make sure you have an Apple ID
- Download XCode from Mac App Store
- Ensure that you're running the most recent operating system. You can check your version by going to "System Preferences" and clicking on "Software Update"


## VSCode with `code`

- Download and install [Visual Studio Code](https://code.visualstudio.com/download). If you're on an M1 Mac, click on `Apple Silicon`.
- Once VSCode is successfully installed, please ensure that VSCode could be found inside your Applications folder. If it isn't in your `Applications`, it will be located under `Downloads`. Grab the VSCode application and drag it into your `Applications` folder.
- Open VSCode and open the `Command Palette` by pressing (Cmd + Shift + P)
- Type `shell command` into the Command Palette and click on the following option: `Shell Command: Install 'code' command in PATH`
- Close VSCode
- Now you can open files from your terminal in VSCode by useing the command `code`.

```bash
    code <filename>
```

## XCode

Run the following command in the terminal.

```sh
    xcode-select --install
```

This installs the Command Line Tools package via the Terminal application. This is to ensure you have it installed correctly and in the correct path.


## Homebrew

Homebrew is a package manager for MacOS. We can install it by running the following:

```sh
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Let's check if we've installed homebrew correctly.

```sh
    #run the following to check where brew is located
    which brew
    #We should see the path below
    #/usr/local/bin/brew
```

Homebrew is going to do a lot of work for us in that it manages our software versions, so always ensure that it's up-to-date and that it's healthy.

```sh
    brew update
```

and

```sh
    brew doctor
```

`brew doctor` may tell you a lot of stuff… you'll want to read through each item, and attempt to resolve the issue for Homebrew. Warnings are good to read but are not mandatory to fix. We're ideally shooting for a message like this:

```sh
    brew doctor
    #Should return:
    #Your system is ready to brew.
```


## Installing Node.js, Python, and PostgreSQL

### Node.js & npm

Node does not come built in to Mac, so we need to install it. First, we'll install `npm`, the 'Node package manager'. In VS code, inside of your `bash` terminal. We will install `Node.js` and `npm` by running the following command:

```bash
   brew install npm
```

Since you might need different versions of Node for different projects, we won't be installing node directly with `npm`. Instead, we'll first install `n` (very descriptive name), which we can use to install a specific version of Node. We'll install `n` globally by using the `-g` flag, because `n` is used at the command-line for different node projects, not for individual projects. You might need administrator privileges to install node modules globally, so we put `sudo` ( (S)uper (U)ser (DO) ) at the start of the command to run it as an administrator. When you run commands with `sudo`, you'll be asked to type your user account password at the commandline. You won't see your password (or even `****`) as you type it, so make sure you type it carefully. 

```sh
    sudo npm install -g n 
```


Download the latest stable (production-ready, non-experimental) version of node.

```sh
    sudo n stable
```

After both `Node.js` and `npm` are installed we could create a folder with a file and test that
we could run JavaScript using node.
```bash
    #create a folder
    mkdir nodetest

    #create a file
    touch nodetest/hello.js

    #open file and log "Hello World!"
    code nodetest/hello.js

    #on hello.js
    console.log("Hello World!");

    #on bash terminal
    node hello.js

    #we should see the following on the terminal
    Hello World!
```

### Python

In VS code, inside of your `bash` terminal. We will install `python`
by running the following command

```bash
    brew install python
```

Now we want to create a folder with a python file 

```bash
    #creates folder
    mkdir pythonTest

    #creates file
    touch hello.py 
```

Finally, we will enter a print statement on our `hello.py` file and run python on
the command line:
```bash
    #In hello.py
    print("Hello World!")

    #in bash terminal
    python3 hello.py

    #we should see the following on the terminal
    Hello World!
```

Now that we have python working, we want to test it's ability to create a virtual
environment by running the following on the `bash` terminal:

```bash
    #now to create our virtual environment we will run the following
    python3 -m venv <name>
```

We should see a folder with the `name` you provided for your venv. Inside that
folder we should see a bin folder holding an `activate` script, a `pip` script,
and several others. (ensure both the activate and pip scripts are present if not
contanct an instructor)

### Adding an Alias
#### Using bash
To save an alias in bash we will run the following commands in our bash terminal:

```bash
    #This command will open vim and get/create a .bash_profile
    vim ~/.bash_profile
    #press the 'i' key on your keyboard to enter --INSERT-- mode. This will allow you to enter text into the .bash_profile
    #enter the following:
    alias python=python3
    #Now we can exit --INSERT-- mode by pressing the 'ESC' key on your keyboard
    #Save the file changes and exit vim by running the following:
    :wq
```

Now we can access our alias by running the next command:

```bash
    source ~/.bash_profile
```

We can now use `python3` by typing in `python` on our terminal.

#### Using zsh

To save an alias in zsh we will run the following commands in our bash terminal:

```bash
    #This command will open vim and get/create a .zshrc file
    vim ~/.zshrc
    #press the 'i' key on your keyboard to enter --INSERT-- mode. This will allow you to enter text into the .zshrc
    #enter the following:
    alias python=python3
    #Now we can exit --INSERT-- mode by pressing the 'ESC' key on your keyboard
    #Save the file changes and exit vim by running the following:
    :wq
```

Now we can access our alias by running the next command:

```bash
    source ~/.zshrc
```
We can now use `python3` by typing in `python` on our terminal.

### PostgreSQL

In VS code, inside of your `bash` terminal. We will install PostgreSQL
by running the following command:

```bash
    brew install postgresql
```

Now we can make sure PostgreSQL is started:

```bash
    brew services restart postgresql@14
```

To enter PostgreSQL we will have to enter the postgres account.
```bash
    #Enter PostgreSQL
    psql postgres
    #You should see your terminal change into:
    postgres=# 
    #To exit PostgreSQL run the following command:
    \q
```

## Resources

- [Use VScode with `code`](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line)
- [Homebrew](https://brew.sh)
- [Node and Homebrew](https://changelog.com/posts/install-node-js-with-homebrew-on-os-x)
- [Python and Homebrew](https://docs.python-guide.org/starting/install3/osx/)
- [Alias in .zshrc](https://dev.to/stuartcreed/how-to-add-aliases-to-your-terminal-on-mac-os-53dl)
- [PostgreSQL and Homebrew](https://www.moncefbelyamani.com/how-to-install-postgresql-on-a-mac-with-homebrew-and-lunchy/)
