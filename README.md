# Vite Scaffolding

## Vite instalation
First of all, we need to install the vite package to start creating projects. This we can do in two different ways: 
  - Standard installation: ```sudo apt-get install create-vite```
  - By creating a new vite project directly: ```npm init vite```.
If done this way,we'll get this message: 

![vite-installation](./assets/vite-installation.jpg)

To which we'll want to say yes, and after installing it a menu will appear, where we can choose our prefered options: 

![vite-installer-options](./assets/vite-installer-options.jpg)


But if we did the standard installation, now we need to execute ```npm init vite``` to get the scaffolding done.

Once the project is created we just have to follow the instructions to move into the folder and install the dependencies.

## Directory structure

A common structure could be this one: 
```
.
├── dist
├── package.json
├── package-lock.json
├── README.md
└── src
    ├── assets
    │   ├── asset1.svg
    │   └── asset2.jpg
    ├── css
    │   └── style.css
    ├── js
    │   └── main.js
    └── index.html

```

So a fast-way to get this structure done could be by deleting all the files that vite created except the ```package.json - package-lock.json - the node-modules - .gitignore``` and executing this on the terminal: 
```
mkdir -p dist src/{css,js,assets}
touch src/js/index.js src/css/index.css src/index.html
```

At this point we have the project scaffolding done.

## CSS Linter - Stylelint

### Installation

```npm i -D stylelint stylelint-config-standard```

### Configuration
#### Create config file
```touch .stylelintrc```

#### Config file content

```
{
  "extends": "stylelint-config-standard",
  "rules": {
    "declaration-colon-newline-after": "always-multi-line",
    "selector-type-no-unknown": null,
    "property-no-unknown": [
      true,
      {
        "ignoreProperties": [
          "content-visibility"
        ]
      }
    ],
    "selector-nested-pattern": "^&",
    "no-descending-specificity": null,
    "no-eol-whitespace": null,
    "declaration-empty-line-before": null
  }
} 
```

#### Script to run stylelint

We create a script in the ```package.json``` like this one: 
```
"stylelint": "npx stylelint src/css/index.css"
```

So if we execute ```npm run stylelint``` we'll get the linter's errors if existing.

## JS Linter - ESlint

To be continued...

## Deployment - Github Pages

To deploy our project we'll use the [gh-pages package](https://www.npmjs.com/package/gh-pages).

### Installation
To install this development dependency in our project, we have to execute: 

```npm i -D gh-pages``` 

### Deployment script
After our repository is initialized and propperly linked to our remote repository, we can add a new script for the development:     

``` "deploy": "gh-pages -d ../dist"```

So now we just have to build our project and deploy it to Github Pages: 

```npm run build && npm run deploy```