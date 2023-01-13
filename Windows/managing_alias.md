# Adding an Alias

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
