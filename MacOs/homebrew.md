# Homebrew

Homebrew is a package manager for MacOS. We can install it by running the following:

```sh
    /bin/zsh -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
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
