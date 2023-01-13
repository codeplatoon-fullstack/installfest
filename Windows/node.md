# Node

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