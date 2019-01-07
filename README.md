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
## Clone this Repository
Using the Terminal, use the **git clone** command followed by this repository's URL **https://github.com/conlonme/React-Start** to download.
## Setup Dependent Files
Using the Terminal, run **npm install** to fetch all the specified software that has been noted in the **package.json** file.
## Test It
Run **npm run build** which should amend the **dist/bundle.js** file if all is working well.
# GOOD LUCK
