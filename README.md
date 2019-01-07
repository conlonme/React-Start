# Setup Environment for React
## Code Downloads
### Install VS Code
VS Code isn't a pre-requisite but, is generlaly viewed as the most complete code editor for web-based software development today. That being said, feel free to use your own preference.
[Download VS Code here ](https://code.visualstudio.com/ "Visual Studio Code")
### Install Node JS
Node JS is a javascript runtime engine built using [Chrome's v8 Engine](https://developers.google.com/v8/ "Google’s open source high-performance JavaScript and WebAssembly engine, written in C++"). Crucially, it includes [NPM](https://www.npmjs.com/) which allows for the download and dependency management of a variety of packages requried to develop.
### Install GIT
[GIT](https://git-scm.com/) allows you to manage your code effectively, as well as push development changes up to a server (handy for both backup and code collaboration).
## Code Configuration
### On VS Code on Windows (Skip if this isn't you)
VS Code provides access to a terminal command prompt. By default, on Windows, that is either CMD or Powershell (depending on how young/old the system is). Consider changing this to GIT (GITBash for Windows). Access User settings by clicking **Ctrl** + **P** and search for **terminal.integrated.shell.windows** which can be modified to read **C:\\Program Files\\Git\\bin\\bash.exe** (if this doesn't work, check you have the correct GIT Bash location for your specific computer), You may need to close and restart VS Code for this to take effect.
## Installation and Setup
### Create a Directory
First of all, create a directory on your computer where you will store the files for your project. Then, open it up within VS code. (Alternatively, open VS code and select **File** -> **Open Folder** and create your folder where you want it).
### Open up a Terminal
Use the Terminal menu option to get a terminal running.
### Run GIT
Type **git init** to have GIT watch this folder for changes.
### Run NPM
Type **npm init -y** to create a default package.json file for your project
### Setup Webpack
Webpack bundles your files from your development area (referred to as **source** and often named **src**) to the completed area (known as **distribution** and termed **dist**).
To being, we use **NPM** to download Webspack, so use the terminal tp type **npm install --save-dev webpack webpack-cli**. From this,you'll notice that a new folder (called **node_modules**) has been created, this is where the various dependent programs we download are going to be stored. You'll also notice that the **package.json** file has been amended by NPM to reflect that we need these two downloads (**webpack** and **webpack-cli**).
Lastly, if you have GIT enabled, this has also now resulted in all of those downloaded files being marked as changed (because they didn't exist before). But, we don't want to perform the task of watching these files (that's what NPM can do for us) so we want to exclude them from our GIT watching.
When installing **webpack**, some basic settings are assumed so that it works "out of the box" - we'll configure it slightly later on.
### GIT Ignore
You should note (if using VS Code and GIT for Version Control) that GIT currently has 1000's of files it is currently monitoring. To instruct GIT to ignore the **node_modules** folder, create a file called **.gitignore** and add a single line to it as **/node_modules/**. Afterwards, expect GIT to only be watchign around 4 files. Job done!
### Install Babel
We are going to be programming using very modern javascript technologies but not every user of your system will be using a browser capable of understanding the latest tech and we don't want to exclude anyone. Babel will convert our javascript code to a standard version of Javascript to makeit compatible with many more browsers. More specifically, Babel transforms javascript from ES2015 and beyond to ES5 - see [Babel](https://babeljs.io/) for further info.
From the Terminal,run **npm i @babel/core babel-loader @babel/preset-env @babel/preset-react --save-dev** (the switch **i** after **npm** means install)
#### Was Babel installed?
To verify this, open up the **package.json** file and check the entries under **devDependnecies**. As the name suggests, **devDependencies** are files that your project **depends** on for **development** but not necessarily **production**.
#### The .babelrc file
Now that Babel is installed (and you've confirmed that from the step above), you need to configure it. To do this, create a new file called **.babalrc**
Within the file, copy/paste the following text:
```
{
  "presets": ["@babel/preset-env", "@babel/preset-react"]
}
```
#### The webpack.config.js file
So, now we have Babel installed, the default configuration (some assumed basics) for **Webpack** just isn't going to cut it, so we'll need some extras. To do this, create a file called **webpack.config.js** and paste the follwoing code:
```
var path = require("path");
module.exports = {
    entry: `./src/index.js`,
    output: {
        path: path.resolve(__dirname,"dist"),
        filename: 'bundle.js'
    },
    mode: "production",
    module: {
      rules: [
        {
          test: /\.(js|jsx)$/,
          exclude: /node_modules/,
          use: {
            loader: "babel-loader"
          }
        }
      ]
    }
  };
```
## It's time for React !!
Still with the Terminal, run
```
npm i react react-dom prop-types --save-dev
```
## Amend the package.json file
To make running webpack more convenient, open up **package.json** and replace:
```
"test": "echo \"Error: no test specified\" && exit 1"
```
with
```
"build": "webpack"
```
## Now, it's time to Code!
Well, that's it - we should now be all installed and running. Just a few basic items to get started now;
### Setup of some files and folders.
+ Create a directory called **src**
+ Inside **src** create a file called **index.js**
+ Inside **index.js** paste the following code:
```
console.log("Hello World");
```
+ Create a directory called **dist**
+ Inside **dist** create **index.htm**
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <h1>Hello World</h1>
    <div id="app"></div>
    <script src="bundle.js"></script>
</body>
</html>
```