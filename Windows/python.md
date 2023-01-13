# Python

In VS code, inside of your `bash` terminal. We will install `python`
by running the following command

```bash
    sudo apt intall python3
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
    #if the above command gives you an error and you are on Windows 11 run the following
    #sudo apt install python3.10-venv

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