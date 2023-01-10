# VSCode with `code`

- Download and install [Visual Studio Code](https://code.visualstudio.com/download). If you're on an M1 Mac, click on `Apple Silicon`.
- Once VSCode is successfully installed, please ensure that VSCode could be found inside your Applications folder. If it isn't in your `Applications`, it will be located under `Downloads`. Grab the VSCode application and drag it into your `Applications` folder.
- Open VSCode and open the `Command Palette` by pressing (Cmd + Shift + P)
- Type `shell command` into the Command Palette and click on the following option: `Shell Command: Install 'code' command in PATH`
- Close VSCode
- Now you can open files from your terminal in VSCode by useing the command `code`.

```bash
    code <filename>
```

## XCode

Run the following command in the terminal.

```sh
    xcode-select --install
```

This installs the Command Line Tools package via the Terminal application. This is to ensure you have it installed correctly and in the correct path.
