# Installfest


## Topics Covered / Goals
- Get your local machine set up to start the course
- Exploring your IDE (VSCode)
- Be able to navigate your computer using the command line
- Create and manage git repositories using the command line

## Lesson

### Computer Setup (Mac, Linux, & Windows)
Before we get started, just know that this will be chaos. Your goal is to get a working environment. Please follow along closely!
- [Slack](https://slack.com/downloads) - for all communication purposes
- [Zoom](https://zoom.us/support/download)
- Sign up for [Operation Code](https://operationcode.org/join)


### CLI (Command Line Interface) Intro

Review the following BASH commands:
- pwd
- ls, ls -a
- cd, ., .., ~, / (different places to cd to)
- mkdir (make ~/projects for all codeplatoon assignments)
- touch
- cp, cp -r
- mv
- rm, rm -r, rm -rf
- rmdir
- sudo
- clear, cmd+k
- less (useful by itself, also used by git diff)
  - `<spacebar>` moves down a page
  - `b` moves up a page
  - `q` quits
- vim (just learn how to quit. used by git commit)
  - press `<esc>` to enter "normal mode"
  - from normal mode, press `:` to enter "ex mode"
  - from ex mode, type `wq` to save and quit, or `q!` to quit without saving
  

### Git Intro

- `ls -a` (nothing here)
- `git status` (not a repo)
- `git init` 
- `ls -a` (see .git folder)
- `git status`
- `touch work.txt`
- `git add .`
- `git commit -m 'i did work'` (use -m to add the message inline, or you'll find yourself in vim)
- `git log` (uses `less` to show the commit history)
- `git remote add origin https://github.com/username/reponame` (the name is arbitrary, but origin is VERY conventional)
- `git remote rm origin` (in case you messed up)
- `git remote -v` (maybe you messed up, but aren't sure)
- `git push origin master`
- `git pull origin master`
- `git clone https://github.com/username/reponame` (now you can start today's exercises)

## Visual Studio Code

There are many IDEs (integrated development environments) out there that developers can use. For our class, we're going to be using Visual Studio Code, a free IDE created by Microsoft. By default, VSCode is a powerful, flexible editor that supports many different coding languages. However, VSCode is also highly extensible, with a rich ecosystem of plugins. 

`Here are the ONLY extensions we will use to build applications with VSCode:`

| JavaScript | Python    | HTML & CSS| Django | React.js |
| :-------- | :------- | :-------- |:------- |:------- |
| [JavaScript (ES6) code snippets](https://marketplace.visualstudio.com/items?itemName=xabikos.JavaScriptSnippets) | [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) |[HTML Boilerplate](https://marketplace.visualstudio.com/items?itemName=sidthesloth.html5-boilerplate)|[Django](https://marketplace.visualstudio.com/items?itemName=batisteo.vscode-django) |[ES7 React/Redux/GraphQL/React-Native snippets](https://marketplace.visualstudio.com/items?itemName=rodrigovallades.es7-react-js-snippets)|
| [Prettier - JavaScript formatter](https://marketplace.visualstudio.com/items?itemName=bysabi.prettier-vscode-standard)| [Python Extension Pack](https://marketplace.visualstudio.com/items?itemName=donjayamanne.python-extension-pack)|[HTML CSS Support](https://marketplace.visualstudio.com/items?itemName=ecmel.vscode-html-css)| [Django](https://marketplace.visualstudio.com/items?itemName=bigonesystems.django)|[React code snippets](https://marketplace.visualstudio.com/items?itemName=hazer.ReactCodeSnippets)|
| [Bracket Pair Colorization Toggler](https://marketplace.visualstudio.com/items?itemName=dzhavat.bracket-pair-toggler) | [Python Indent](https://marketplace.visualstudio.com/items?itemName=KevinRose.vsc-python-indent)|[Live Server]( https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) |[Django Snippets](https://marketplace.visualstudio.com/items?itemName=bibhasdn.django-snippets)|[React Bootstrap 4 Snippets](https://marketplace.visualstudio.com/items?itemName=Himel.react-bootstrap4)|

## Assignments
- [99 Bottles](https://github.com/sierraplatoon/algo-99-bottles) in JS
- [Deaf Grandma](https://github.com/sierraplatoon/algo-deaf-grandma) in JS
- [Terminal Commands In Depth](https://github.com/sierraplatoon/misc-command-line) ...nothing to submit here but necessary reading
- [Incoming Student Survey](https://docs.google.com/forms/d/e/1FAIpQLSePRzeiSCe1hqzud7btr--Xxm791zqCe_RqA_9mGxEIUN_IwQ/viewform)
