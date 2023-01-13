# Node.js & npm

Node does not come built in to Mac, so we need to install it. First, we'll install `npm`, the 'Node package manager'. In VS code, inside of your `zsh` terminal. We will install `Node.js` and `npm` by running the following command:

```zsh
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
```zsh
    #create a folder
    mkdir nodetest

    #create a file
    touch nodetest/hello.js

    #open file and log "Hello World!"
    code nodetest/hello.js

    #on hello.js
    console.log("Hello World!");

    #on zsh terminal
    node hello.js

    #we should see the following on the terminal
    Hello World!
```
