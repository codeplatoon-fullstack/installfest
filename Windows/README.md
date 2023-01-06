
# Windows Installfest

## What we'll cover
We are going to install everything that you will need for this course. Please do this in order!

1. Visual Studio Code & `code`
2. Understanding the Unix Environment (WSL)
3. apt-get
4. Node.js & npm
5. Python
6. Adding and Alias
7. PostgreSQL

## VSCode with `code`
- Download and install [Visual Studio Code](https://code.visualstudio.com/download)
- During install, VSCode will add itself to your system's PATH environmental 
variable. This will allow you to open VSCode from the terminal by simply typing 
`code`. You can also open files in VSCode from the terminal by typing `code SOME_FILENAME`.


## Prerequesites

- Powershell open as `administrator`
- Terminal settings as developer tools
- Ensure you have 256GB of space in your C drive


## Install WSL

Now we will install WSL. Open up `Windows PowerShell` as the administrator,
give yourself permissions, and enter the following:

```bash
    #This will install and launch an Ubuntu Linux Environment

    wsl --install -d ubuntu
```

Once Ubuntu is done installing, it will ask you to provide a username and 
password. Note, this username and password is solely for this Linux distribution
and will have the abilitity to run the `sudo` command (Super User DO). `This is very
important so please ensure to remember this information`.

```bash
    #When you type in your password on the terminal nothing will show up. 
    #(This is called blind typing [You are still typing you just can't see it] also you can not use the backspace)
    
    Enter new UNIX username: <TypeInUsername>

    #Once you enter the name it will prompt for your password.

    New password:

    #then it will ask you to re-enter the password to confirm.

    Retype new password:

```

Now we want to update and upgrade our Package manager:
(You may want to run this command monthly just to ensure you're up to date with your Package manager)

```bash
    #After you run this command, you'll be propmted to enter your password,
    #This is because we will be using the sudo command.

    sudo apt update && sudo apt upgrade
    
    sudo apt-get update
```

Now we can open VS Code, on the upper menu bar click on `Terminal->New Terminal`.
Once the terminal is open type in `bash` and you'll open your WSL terminal.

```bash
    #Powershell is through the windows operating system
    PS C:\Users\<username>> bash
    
    #In WSL you'll be using Linux
    #You'll the prompt will have changed colors:
    <UnixUsername>@<YourComputer>: /mnt/c/Users/<username>$
```

The last thing we will need to do is mount WSL to share metadata:
(This will enable your computer to run hot-reloads during development)

```bash
    #Enter 
    cd ..
    #until your path on your teminal looks like this
    <UnixUsername>@<YourComputer>:/mnt

    #Now run (You wont see any changes)
    sudo umount /mnt/c

    #finally end it by running (You wont see any changes)
    sudo mount -t drvfs C: /mnt/c -o metadata

    #now go back to the original path
    cd c
    cd Users
    cd <UnixName>

    #This should be the final outcome
    <UnixUsername>@<YourComputer>: /mnt/c/Users/<username>$
```


## Installing Node, Python, and PostgreSQL

### Node

In VS code, inside of your `bash` terminal. We will install `Node.js` and `npm`
by running the following command:

```bash
    sudo apt install nodejs

    sudo apt install npm
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
    sudo apt intall python
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
    python hello.py

    #we should see the following on the terminal
    Hello World!
```

Now that we have python working, we want to test it's ability to create a virtual
environment by running the following on the `bash` terminal:

```bash
    #the following installation will give python the ability to create
    #virtual environments
    sudo apt install python3.8-venv

    #we will also want to intall pip
    sudo apt-get install python3-pip


    #now we will install virtualenv using pip
    sudo pip install virtualenv

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
    sudo apt install postgresql postgresql-contrib
```

Now we can make sure PostgreSQL is started:

```bash
    sudo service postgresql start
```

To enter PostgreSQL we will have to enter the postgres account, and then enter PostgreSQL.
```bash
    #enter the postgres account
    sudo -i -u postgres
    
    #or
    su postgres

    #enter PostgreSQL(the actual database)
    psql
```

If you'd like to check what port PostgreSQL is running in, you could type in the following on
the terminal:
```bash
    pg_lsclusters
```

A table will pop up on the terminal, under the Owner header look for postgres, then go left
you'll see the Status and after that you'll see the port. Typically the port will be 5432.

In case port 5432 is occupied by a different process run the following:

```bash
    #this will find out what is currently on port 5432 and tell you which PID belongs to you
    netstat -aon | findstr 5432
    
    #it will provide the following
    TCP    [::]:5432[::]:0                 LISTENING       18996
    
    #this will kill the current process using port 5432 
    taskkill /pid 18996 /f <desired pid>
```
