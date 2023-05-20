# Installing Git and Github CLI on Ubuntu Linux

Git may or may not be install by default on your system, but to make sure use `apt` to install it.

```bash
$ sudo apt install git
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
$ sudo apt install gh
```

Once downloaded type:

```bash
$ gh auth login
```

and follow the wizard steps to complete the authentication process. When done you should be able to clone a repo like so:

```bash
$ gh repo clone codeplatoon-fullstack/installfest
```

This will install that repo in your current directory. Assuming this is successful if you want to delete it afterwards type:

```bash
$ rm -rf installfest
```
