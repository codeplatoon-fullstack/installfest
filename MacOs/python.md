# Python

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
