# Install WSL

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