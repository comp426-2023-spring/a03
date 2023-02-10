# Assignment 03: Create a module-based command line Node.js package (with CLI)

This assignment will help you learn to create an installable Node.js module package. You'll also provide a command line interface with it. 

## DO NOT CLONE THIS REPOSITORY DIRECTLY FROM THE TEMPLATE REPO

Use the personalized repository that is generated when you follow the GitHub classroom link instead: https://classroom.github.com/a/p57R-IU9

**_If you clone this repo directly, it will not be added to the organization as an individual repo associated with your account and you will not be able to push to it._**

## Description

The purpose of this assignment is to create an installable Node.js module package.

The package you create will contain a module (or multiple modules) as well as configuration and scripts to allow the user to run `node-rps` and `node-rpsls` after instaling. 

The package will contain command line games of "[Rock Paper Scissors](https://en.wikipedia.org/wiki/Rock_paper_scissors)" (`node-rps`) and the more advanced version, "[Rock, Paper Scissors Lizard Spock](https://bigbangtheory.fandom.com/wiki/Rock,_Paper,_Scissors,_Lizard,_Spock)"  (`node-rpsls`).

## Setup

1. After you've cloned your repository, run `npm init` and follow it through, adding and changing information as needed. 
2. Set package name to `node-rpsls`. 
2. Set the `main` file to be `./lib/rpsls.js`
3. Set the license to match the license in the repository.
4. Once your `package.json` file is created, set two `bin` files as `"node-rps": "./bin/rps-cli.js"` and `"node-rpsls-cli.js": ""`.
5. Install dependencies. You'll need minimist for this assignment to parse command line arguments.
6. Create directories `bin` and `lib` inside the root of the directory.
7. Create `rpsls.js` inside the `lib` directory. This is going to be the main file and also where you will put your exported RPS and RPSLS function(s). 
8. Create `rps-cli.js` and `rpsls-cli.js` inside the `bin` directory. These are going to be the files that run when you link/install the package and run `node-rps` and `node-rpsls`, respectively.
9. Put the appropriate shebang in the `./bin/*-cli.js` files. 
10. Make sure that the `./bin/*-cli.js` files are executable (i.e. run `chmod +x ./bin/*-cli.js`). 

## Requirements

Structural requirements for this assignment package:

1. Importable modules for RPS and RPSLS using ES `import` method.
2. A a command line interface for RPS and RPSLS.

Functional requirements for this assignment package:

1. Two versions of the game (RPS and RPSLS) in one package.
2. If the command or function is called without an argument, it should return only the shot for one player, e.g. `{"player":"rock"}`.
3. If the command or function is called with an argument, it should return the results of a game between a player and an opponent, e.g. `{"player":"rock","opponent":"scissors","result":"lose"}`.
4. If you supply any argument other than those the individual function is expecting, the user should be presented with an error and a suggestion of the available options (e.g. "rock", "paper", "scissors" for RPS and "rock", "paper", "scissors", "lizard", "spock" for RPSLS). 
5. Each command should echo its own help text with usage examples when invoked with `-h`.

### Module

Your module should be importable using the following or similar:

```
import { rps } from "/lib/rpsls.js"
import { rpsls } from "/lib/rpsls.js"
```

Or, once installed:

```
import { rps } from 'node-rpsls'
import { rpsls } from 'node-rpsls'
```

You will want the package from this assignment to be installable for a04 as well, so think about that. Read this for more info about importing: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import

#### Logic and design

It is entirely up to you how you decide to create the logic of these two games and their underlying functions, but you will want to follow a few basic principles.

For example:

An importable `rps()` function in `./lib/rpsls.js` should ideally return an object with form similar to this:

```
{
  player: "rock"
}
```

But that same function should not return `lizard` or `spock` because those are out of range for the Rock Paper Scissors game.

An importable `rpsls()` function, on the other hand, would return any of the elements in this array: `[ "rock","paper","scissors","lizard","spock"]`

You should probably also structure your functions so that if an argument is supplied, then the function would return the result of a game between the user/player and an opponent. Like this: 

```
let shot = "Spock"
rpsls(shot)
```

```
{
  player: "Spock",
  opponent: "rock",
  result: "lose"
}
```

The command line interface will be used to pass values to the arguments in your function.

There are [a lot](https://rocambille.github.io/en/2019/07/30/how-to-roll-a-dice-in-javascript/) [of examples](https://codepen.io/Pyremell/pen/eZGGXX/) [of how](https://www.geeksforgeeks.org/building-a-dice-game-using-javascript/) to simulate/emulate dice rolling using JavaScript online. Make use of them and adapt them for your purposes. As long as you write an exportable function that can take the three arguments above, you should be good to go.

### CLI

Your command line interface should take three arguments with the following defaults:

1. `--sides`: the number of sides of the die you are rolling (default to 6 sides).
2. `--dice`: the number of dice you are rolling (default to 2 dice).
3. `--rolls`: the number of times the dice are rolled (default to 1 time).

Output should be in JSON and look like this: 

```
{"sides":6,"dice":2,"rolls":1,"results":[6]}
```

The returned JSON should include:

1. the number of sides for your dice (they will all be assumed to be the same),
2. the number of dice you are rolling,
3. the number of times you roll the dice, and
4. the total number of the dice added together.

An example for running your CLI script:

```
roll-dice --sides=10 --dice=2 --rolls=3
```

And an example output:
```
{"sides":10,"dice":2,"rolls":3,"results":[4,25,30]}
```

> HINT: Use `JSON.stringify()` to convert the output of your function to JSON. https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify

### Resources

https://www.theserverside.com/tutorial/Tutorial-Coding-a-simple-Rock-Paper-Scissors-application-in-JavaScript

https://learnersbucket.com/tutorials/js-projects/rock-paper-scissor-lizard-spock-game-in-javascript/

https://github.com/partha7978/Rock-Paper-Scissors-Lizard-Spock

https://hackernoon.com/how-to-create-rock-paper-scissors-spock-lizard-in-javascript-991k36hy

https://codepen.io/763004/pen/pPGGyP

https://stackoverflow.com/questions/22623331/rock-paper-scissors-lizard-spock-in-javascript

### Example online games

https://rpsls.net/ - This one lets you play an opponent at a unique URL or a random opponent. 

