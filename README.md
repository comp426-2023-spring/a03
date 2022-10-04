# Assignment 03: Create a module-based line Node.js package (with CLI)

This assignment will help you learn to create an installable Node.js module package. You'll also provide a command line interface with it. 

## DO NOT CLONE THIS REPOSITORY DIRECTLY

Use the GitHub classroom link instead: 

**_If you clone this repo directly, it will not be added to the organization as an individual repo associated with your account and you will not be able to push to it._**

## Description

The purpose of this assignment is to create an installable Node.js module package.

## Setup

1. After you've cloned your repository, run `npm init` and follow it through, adding and changing information as needed. 
2. Set package name to `node-dice`. 
2. Set the `main` file to be `./lib/roll.js`
3. Set the license to match the license in the repository.
4. Once your `package.json` file is created, set the `bin` file to be `"roll-dice": "./bin/cli.js"`
5. Install dependencies. You'll need minimist for this assignment to parse command line arguments.
6. Create directories `bin` and `lib` inside the root of the directory.
7. Create `roll.js` inside the `lib` directory. This is going to be the main file and also where you will put your dice-rolling function(s). 
8. Create `cli.js` inside the `bin` directory. This is going to be the file that runs when you link/install the package and run `roll-dice`.
9. Put the appropriate shebang in the `./bin/cli.js` file. 
10. Make sure `./bin/cli.js` is executable (i.e. run `chmod +x ./bin/cli.js`). 

## Requirements

