# NodeJS
> Server-side JavaScript

NodeJS is a way of running JavaScript on the server rather than in the browser. This allows you do things like simple scripts in the command-line, automation tools, games and web servers which communicate with a database.

- [NodeJS](https://en.wikipedia.org/wiki/Node.js) page on Wikipedia.
    > Node.js is an open-source, cross-platform, JavaScript runtime environment that executes JavaScript code outside of a browser.
- Repository: [nodejs/node](github.com/nodejs/node)
- Initial release: 2009

This section covers how to install and run NodeJS.

## Install

**Linux**

```sh
$ sudo apt install nodejs
```

**macOS**

```sh
$ brew install nodejs
```

## Run

### Interactive console

Start the interactive console.
```sh
$ node
```
```
Welcome to Node.js v12.1.0.
Type ".help" for more information.
>
```

Enter commands and press enter.

For example:

```javascript
> console.log('Hello!');
```

Press `CTRL`+`D` to exit the console.


## Run project scripts

### Node

How to run scripts in this project using `node`.

```sh
$ cd <PATH_TO_REPO>
$ cd 'Scripting languages/JavaScript'
$ node my_file.js
$ # e.g.
$ node iteration.js
```

### NPM

How to run arbitrary package scripts using `npm`.

Using [run-script](https://docs.npmjs.com/cli/run-script).

```sh
$ npm run-script COMMAND
$ # Alias:
$ npm run COMMAND
```

Using [npm-run](https://www.npmjs.com/package/npm-run)

```sh
$ npm-run COMMAND
```

## Node packages

### NPM

Node comes with `npm`.

This will install node packages in a folder which should be ignored in `git`, called `node_modules`.

Install packages in the current project - requires `package.json` to exist.

```sh
$ npm install
```

```sh
$ npm install PACKAGE
```

Install a package globally.

```sdh
$ npm install -g PACKAGE
```

View globally installed packages.

```sh
$ npm list
```

That is very verbose, so try this, based on [post](https://medium.com/@alberto.schiabel/npm-tricks-part-1-get-list-of-globally-installed-packages-39a240347ef0)

```sh
$ npm list -g --depth 0
├── bower@1.8.8
├── bower-away@1.1.2
├── docsify-cli@4.4.0
├── grunt-cli@1.3.2
├── http-server@0.11.1
├── npm@6.9.0
└── npx@10.2.0
```



### NVM

If you want to install multiple versions of Node and NPM on your machine, consider using NVM.

#### Setup

Follow the instructions here:

- [nvm-sh/nvm](https://github.com/nvm-sh/nvm) Github repo
- [NVM, the Easiest Way to Switch Node.js Environments on Your Machine in a Flas](https://itnext.io/nvm-the-easiest-way-to-switch-node-js-environments-on-your-machine-in-a-flash-17babb7d5f1b?gi=74712a4b1ad)

Note you will have to install `nvm` command and also update your shell RC file to ensure it is picked up.

#### Usage

After setup, you can use it to install and switch to a target Node version (and associated NPM version).

For example, here I install a new version of Node, without specifying the full version.

```sh
$ nvm install 13
Downloading and installing node v13.11.0...
...
$ nvm use 13
```

View available versions:

```
        v6.11.2
         v8.0.0
        v8.15.0
        v10.0.0
       v10.15.0
        v11.0.0
        v12.1.0
->     v13.11.0
         system
 ```   

You can switch between version in the terminal and set a global default.


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY0NzgzODY1OF19
-->