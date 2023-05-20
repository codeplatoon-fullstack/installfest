# Installing Python on Ubuntu Linux

Python comes built in with Ubuntu but to ensure that we have the must up to date version, let's run the following commands:

```bash
$ sudo apt install python3
$ sudo apt install python3-pip
$ sudo apt install python3-setuptools
```

> Note: if you ever need to install multiple packages simultaneously, apt install supports this like so:
>
> ```bash
> $ sudo apt install python3 python3-pip python3-setuptools
> ```
>
> This is just a matter of convenience though, installing the packages as separate commands will result in the same outcome.

Test that you can run the commands `python3` and `pip3`. For `pip3` you will simply see some output indicating it's usage, but as long as it recognizes the command as existing you are good. As per usual you may need to close and reopen your terminal to see these working.

### Python Virtual Environment

Python uses the concept of a 'virtual environment' to install packages through pip uniquely for a given project. In order to make creating such environments possible first install the necessary tool:

```bash
$ sudo apt install python3.10-venv
```

Now create a new project with a Python virtual environment like so:

```bash
$ python3 -m venv test_project
```

If it works this will create a new folder in your current directory called 'test_project'. Inside that folder we should see a bin folder holding an `activate` script, a `pip` script, and several others. Ensure both the `activate` and `pip` scripts are present. Do so with:

```bash
$ ls test_project/bin
```

If you would like to delete it at this point type:

```bash
rm -rf test_project
```
