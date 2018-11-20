
# Node.js - Introduction & workshop

![](https://www.shareicon.net/data/128x128/2015/10/06/112725_development_512x512.png)

## How do I install Node.js? 🔧
If you've already installed Node.js, skip to **[What is Node.js?](https://hackmd.io/v21ZUoeaTgGxwl2mKXf51A?both#What-is-Nodejs-Deciphering-the-definition)** further down.
If you haven't already done so, now's the time to install it. 
### :small_blue_diamond: The easy way:
Go to https://nodejs.org/en/download/ and download the appropriate version for your OS (i.e. Windows, Linux/Ubuntu etc., Mac).

### :small_orange_diamond: The geeky way:
Open a terminal/bash/shell and copy-paste the appropriate command for your OS.
* **On Ubuntu 18.04**
    Ubuntu, Linux etc. come with a version of Node.js in their default repos, so the first thing you need to do is update it. Note that you should type `nodejs` for this purpose, *not* simply `node`.
    
    Open a terminal window and make sure that you are logged in as a user with elevated privileges, i.e. as a **sudo user** (if you don't know how to do this, check [this guide](https://linuxize.com/post/how-to-create-a-sudo-user-on-ubuntu/)). 
    
    In your terminal, type:
    `$ sudo apt update`
    then, to install both Node and npm
    `$ sudo apt install nodejs npm`
    
    Check that all is good by typing
    `$ nodejs -v`
    and 
    `$ npm -v`
    to verify the versions you've just installed.
    
    Should you ever want to remove Node.js, you can either type
    `$ sudo apt remove nodejs`
    to uninstall Node but keep the configuration files (in case you want to re-install it) or
    `$ sudo apt purge nodejs`
    and
    `$ sudo apt autoremove`
    to remove Node completely and get rid of any packages that came automatically with it.
* **On MacOS**
    If you have Homebrew, type:
    `$ brew install node`
    This should install both Node and npm


## What is Node.js? Deciphering the definition :flashlight:
:small_orange_diamond: Node.js is a system that creates an interface between the front and the back end.  Node.js as such is written mainly in C and C++ but it translates JavaScript into machine code. Although it was originally developed for back-end programming and is still primarily associated with back-end tasks, it is [a misconception](https://blog.npmjs.org/post/101775448305/npm-and-front-end-packaging) to assume that npm is only used on the server side: npm is also used for front-end tasks and front-end packages, such as [ESLint](https://eslint.org/) and [webpack](https://webpack.js.org/), are among the most popular npm downloads.
:small_orange_diamond: Node.js is a system that creates an interface between the front and the back end.  Node.js as such is written mainly in C and C++ but it translates JavaScript into machine code. 
:small_orange_diamond: You'll almost certainly use **npm**, Node.js's de facto package manager - a practically inextricable part of Node - for both back-end and front-end tasks.Although it was originally developed for back-end programming and is still primarily associated with back-end tasks, it is [a misconception](https://blog.npmjs.org/post/101775448305/npm-and-front-end-packaging) to assume that npm is only used on the server side: npm is also used for front-end tasks and front-end packages, such as [ESLint](https://) and webpack, are among the most popular npm downloads.
 
:small_orange_diamond:  Until recently, the official definition on the [Node.js](https://nodejs.org/en/) website ran as follows:
> Node.js® is a JavaScript runtime built on Chrome’s V8 JavaScript engine.
>     Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient.
>     Node.js’ package ecosystem, npm, is the largest ecosystem of open source libraries in the world.

Let's break it down:
> Node.js® is a JavaScript runtime built on Chrome’s V8 JavaScript engine.

:small_orange_diamond: This means that Node.js is basically a software stack that allows you to use JavaScript to write applications. This runtime environment includes the V8 engine. A JS engine is code that processes and translates other code from one programming language into another. The first JS engine, nicknamed 'SpiderMonkey', was created for Netscape and was written in C++ and a much updated version now powers Firefox. Microsoft's JS engine is called 'Chakra', while Node.js runs on V8, the JS engine that was developed for and powers Chrome.

What the V8 engine does when it receives JavaScript code is parse it; i.e. run through it, check it for syntax errors, and, if it's executable, read it from top to bottom and convert it into machine code. 

:small_orange_diamond: Twenty-first century coders hardly ever write programmes directly in machine code, which looks like this:

![](http://www.dataserve-retro.co.uk/contents/media/zx-spectrum-basic-example%20175h.jpg)

:small_orange_diamond: Node.js is based on a non-blocking I/O (input-output) model, which enables it to handle multiple concurrent connections, even though it makes use of just a single main thread, known as the 'event loop' and a mere four additional 'worker' threads - [more on those](https://hackmd.io/TH-RSOxxR4CoKdRIuOO2ww#So-does-Nodejs-run-on-a-single-thread) when we talk about the event loop in more detail. 

Traditional models that don't make use of Node.js or equivalent platforms, such as Elixir, either create a new thread for every client or wait for an operation to complete before the computer can execute the next one along a thread.


In contrast, Node.js can deal with anything from a few hundred to a few hundred thousand requests per second (and I've read reports of Node handling 1,000,000 requests/second), depending on what tasks we ask it to handle.

![](https://cdn-images-1.medium.com/max/828/1*4LsfQ0ZbZkapHDR8eTYp4g.png)
###### [Image source](https://medium.com/the-node-js-collection/why-the-hell-would-you-use-node-js-4b053b94ab8e): 'Why the Hell Would You Use Node.js?'

:small_orange_diamond:  How does Node.js manages to juggle multiple tasks at what appears to be the same time? The answer is, through the [asynchronous event loop](https://hackmd.io/TH-RSOxxR4CoKdRIuOO2ww#) and a type of functions known as 'callbacks'. Let's look at the last line of the definition first:

>     Node.js’ package ecosystem, npm, is the largest ecosystem of open source libraries in the world.
>     

:small_orange_diamond: These open-source libraries are known as 'packages' and _npm_ is Node's default package manager. Let's look at both of those in more detail.


## Packages, modules, npm ...
Often 'packages' and 'modules' are used interchangeably, but there is a slight difference between the two.


### :small_blue_diamond: What is a Node.js package?
Node.js **packages** (usually referred to as 'npm packages') are the equivalent of plug-ins, or browser extensions and add-ons. So a Node.js package is basically a bundle of code that extends Node's capabilities in some way.

The name and version of each and every one of the packages you install (in most cases locally, i.e. in your project's directory) with the command `npm install` or `npm i` are logged into the project's `package.json` file. We will talk more about the `package.json` a little later.

A few examples: at [the time of writing](https://gist.github.com/anvaka/8e8fa57c7ee1350e3491), 

* [lodash](https://www.npmjs.com/package/lodash) is one of the most popular npm packages, with an amazing 7,383,321 weekly downloads

* [express](https://www.npmjs.com/package/express) has a whopping 2,578,156 weekly downloads

* [react](https://www.npmjs.com/package/react) has a very impressive 1,323,257 weekly downloads

* [npm](https://www.npmjs.com/package/npm), the npm package that (a little confusingly) is also the the name of the most popular Node.js package manager has an average of 477,724 weekly downloads.

In contrast,

* [reset.css](https://www.npmjs.com/package/reset.css) has a mere 1,087 weekly downloads
... while
* [doggy.css](https://www.npmjs.com/package/doggy.css/) has just 5 weekly downloads.

:chart_with_upwards_trend: If you're curious about npm rankings, check out [these stats](https://gist.github.com/anvaka/8e8fa57c7ee1350e3491).

### :small_orange_diamond: What is a Node.js module?
A `module` is any bundle of code that you need to `require` in a file in order to load and use it. 

* Both `require` and `module` are the names of **core npm packages** that come with Node.js, so you don't need to install them separately - that is, you don't need to 'require' them. They are also the commands you use to load and use packages and modules in your files.

* The vast majority of npm packages are loaded with `require`, which is why they are also modules. However, you also use `require` to use JavaScript files that live in a local folder. These files are also modules. 

* The code in the example below is what you would typically find at the top of a file named `app.js`. In this example, `express` is the popular Express package, `handlebars` is an optional Express package (think of it as an Express add-on), while `index.js` is a file in the `controllers` subfolder, which, as the `./` indicates, lives in the same folder as the `app.js` file in which you're requiring all those modules.

```
const express = require('express');
const handlebars = require('express-handlebars');
const controllers = require('./controllers/index.js');
```


### :small_blue_diamond: What is npm?
There's at least one package for almost every imaginable thing you might want to do with JavaScript and npm is the *name* of this massive repository and of the *package* that you need to install to access this repository and also the core part of the *command* you'll often use in node to install, uninstall and run those packages. 

The basic commands for doing these are quite intuitive (NB omit the <> and replace 'package name' with the package's actual name).

### :small_orange_diamond: *How* do I install npm packages?

#### Install all packages globally :globe_with_meridians:
`npm install --global`
or
`npm i -g`
In most projects, you won't want to use either of these commands; see why [below](https://hackmd.io/v21ZUoeaTgGxwl2mKXf51A?both#-Where-do-I-install-Nodejs-packages).

#### Install all packages locally :house: 
* To install them as *dependencies*, `cd` to the root directory of the project and in terminal type:
`$ npm install`
or 
`$ npm i`

* To install them as *devDependencies*:
`$ npm install --save-dev`


### :small_blue_diamond: How do I uninstall npm packages?
* To remove it from the _node_modules_ folder, but not from the package.json:
`npm uninstall <package name>`

* To remove a package from both the _node_modules_ folder and from the 'dependencies' section of the package.json:
`npm uninstall <package name> --save`

* To remove a package from both the _node_modules_ folder and from the 'devDependencies' section of the package.json:
`npm uninstall <package name> --save-dev`

* To remove a globally installed package:
`npm -g uninstall <package name> --save` 

### :small_orange_diamond: Example: how to install and uninstall *nodemon*
Let's look at how we can install and uninstall `nodemon`, a popular npm package that  detects the changes you make in your files and restarts your Node.js application automatically.

* To install `nodemon` globally (not recommended), go to your terminal and type:

` $ npm install -g nodemon`

* To install it locally as a dev dependency (recommended), navigate to the roog directory of the project in which you want to use it and type:

`npm install --save-dev nodemon`

Once you have installed the package locally, you need to start your server once with `nodemon`, so that it then updates the browser automatically whenever you make any changes. You will also have the option or using nodemon to restart the server manually (see instructions in your terminal when you first run your app with nodemon).

If you want to run a server saved in a file called `server.js` in your root folder and to have your server listen to port 4000, type this command in your terminal:

`nodemon ./server.js localhost 4000`

Make sure that you adjust the path, depending on where your file is located.

* To uninstall `nodemon` globally:

`npm -g uninstall nodemon --save`

* To uninstall `nodemon` from your dev dependencies:

`npm uninstall nodemon --save-dev`


### :small_blue_diamond: *Where* do I install Node.js packages?
You can install them either locally, i.e. in a project directory, or globally, i.e. make them available to every Node-based project on your machine.

As a rule of thumb, you should install Node packages **locally**. The main reason for this recommendation is that not all versions of all packages are compatible with each other, so you'll often need a specific version of the same package in one project and a different one in another project for your code to work. 

:warning: If you install packages **globally**, you are likely to end up implementing the same version in every project on your machine, which could break your applications or make it impossible for you to work on collaborative projects that require a different version from yours.

### :small_orange_diamond: Where do I install a *local* package?
In the directory where your project lives. In your terminal, make sure that you `cd` to that directory (often that'll be a local GitHub repo) then type
`$ npm install <name-of-the-package-here>`

### :small_blue_diamond: Where do I install a *global* package?
It doesn't matter in which directory you are when you run the command for installing a package globally. Wherever you are, type
`$ npm install -g <name-of-the-package-here>`
The `-g` flag in the command below tells npm to install the relevant package where appropriate so that it is available to all your projects.

Most packages don't take up that much space on your hard drive anyway so, with relatively few exceptions (such as npm itself or nodemon), it's best to install them locally, not globally. Further down we'll see when we need to install a package as a _dependency_ or as a _devDependency_.


### :small_orange_diamond: Where do my local packages live?
In the `node_modules` folder, which is created automatically when you install packages locally.

![](https://i.imgur.com/zj8EkLr.jpg)


### :small_blue_diamond: How to check which Node packages are installed globally on your machine:

`$ npm list -g --depth 0`



## The *package.json* file
A `.json` file contains a bunch of data written in JavaScript Object Notation. The JSON syntax allows us to convert freely JavaScript objects into JSON objects and vice versa. These objects consist of data in the form of text that can be exchanged between a browser and a server. You stringify JavaScript objects to convert them into JSON and send them to the server and you parse JSON data you have received to convert them into a JavaScript object.

Now, the `package.json` that every project created with Node.js will inevitably include is what its name implies, i.e. a JSON object with data related to the packages you have installed in your project with _npm_, which is why we say that the package.json contains _metadata_. These metadata will tell anyone with whom you share your code what they need to install for the project to run at all. 

⚠️  **NB Make sure that you are in the root directory of your project before you run `npm install` or `npm i`.**

If you change any of those modules in the meantime, the changes will be recorded in the package.json of your copy of the project. Anyone else working on another copy (often a local GitHub repository) of that project will have to get the new package.json (often by pulling the master branch or fetching another branch) and running `npm install` again.

### :small_orange_diamond: Create a package.json with _npm init_
Every new project that uses Node.js needs to be initialised with the command `$ npm init`,
which creates the package.json. When you run this command, Node will ask you to provide the basic details that go right at the top of the package.json it'll create for you. While you can type and enter those details manually, you don't have to. You can press 'enter' multiple times or even type
$ npm init -y
and let Node.js fill in the gaps as best it can. You can edit the package.json file whenever you need to, e.g. to apply a fix recommended by a security alert.

### :small_blue_diamond: What information does a package.json contain?
Typically, every package.json file will contain a list of brief details about your project, similar to this one:

```
{
  "name": "my_project",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "private": true,
  "jest": {
    "testRegex": "__test__/*"
  },
  "scripts": {
    "start": "node src/server.js",    
    "client": "cd client && npm start",
    "server": "nodemon src/server.js",
    "dev":  \"npm run server\" \"npm run client\",
    "express-test": "NODE_ENV=test jest --runInBand --forceExit",
    "react-test": "cd client && npm i && npm test",
    "test": "npm run express-test && npm run react-test",
    "local-test": "npm run express-test && cd client && npm test",
    "repository": {
    "type": "git",
    "url": "git+https://github.com/fac-X/my_project.git"
  },
  "keywords": [],
  "author": "",
  "license": "MIT",
  "bugs": {
    "url": "https://github.com/fac-X/my_project/issues"
  },
  "homepage": "https://github.com/fac-X/my_project",
  "devDependencies": {
    "babel-eslint": "9.0.0",
    "eslint": "5.6.0",
    "eslint-config-node": "^4.0.0",
    "eslint-config-prettier": "^3.1.0",
    "eslint-config-recommended": "^4.0.0",
    "eslint-plugin-react": "^7.11.1",
    "jest": "^23.6.0",
    "supertest": "^3.3.0",
    "nodemon": "^1.18.4"
  },
  "dependencies": {
    "bcryptjs": "^2.4.3",
    "body-parser": "^1.18.3",
    "create-react-app": "^2.0.3",
    "env2": "^2.2.2",
    "express": "^4.16.3",
    "express-fileupload": "^1.0.0-alpha.1",
    "express-session": "^1.15.6",
    "express-validator": "^5.3.0",
    "serve-favicon": "^2.5.0"
  },
  "engines": {
    "node": "v10.10.0"
  }
}
```
* `main` specifies the primary entry point to your application (it will often be the `index.js` file) 
* `scripts` is where you specify the commands that need to be run for various purposes - e.g. to run the server. 
* `devDependencies` are the packages you need in the production phase, ie. when you're developing your application. For example, any packages you use for testing, such as Tape or Jest, will be installed as devDependencies.
* `dependencies` are the packages that are needed for your application to run. For example, if you're using Express but it's omitted from the dependencies, your application simply won't run when your project is cloned on another machine.


### :small_orange_diamond: What is that package-json.lock thing?  🔒
A newish feature that is automatically created when you install local dependencies. Its purpose is to document **precisely** which version of which package you've installed, so that the exact same version is installed whenever you or someone else runs `npm install` to reproduce your project in another location (usually on another computer). 

This is important, because using different versions of the same package for the same project can have unintended results and even break your application.

Here's an example of of what the entry for `nodemon` looks in the `package.json` and in the `package-json.lock` files:

* **package.json** entry
```
"devDependencies": {
    "nodemon": "^1.18.4",
  },
```
* **package-json.lock** entry
```
"nodemon": {
      "version": "1.18.4",
      "resolved": "https://registry.npmjs.org/nodemon/-/nodemon-1.18.4.tgz",
      "integrity": "sha512-hyK6vl65IPnky/ee+D3IWvVGgJa/m3No2/Xc/3wanS6Ce1MWjCzH6NnhPJ/vZM+6JFym16jtHx51lmCMB9HDtg==",
      "dev": true,
      "requires": {
        "chokidar": "^2.0.2",
        "debug": "^3.1.0",
        "ignore-by-default": "^1.0.1",
        "minimatch": "^3.0.4",
        "pstree.remy": "^1.1.0",
        "semver": "^5.5.0",
        "supports-color": "^5.2.0",
        "touch": "^3.1.0",
        "undefsafe": "^2.0.2",
        "update-notifier": "^2.3.0"
      }
    },
```


When you push your projects to GitHub or similar platforms, you should commit the `package-json.lock` to make it available to anyone who clones your code, so make sure you don't add it to `.gitignore`.



## OK, but I still don't see what makes Node.js so special?  :neutral_face:

### ⭐️ Node.js uses JavaScript on client and server
... and translates JavaScript into machine code. This allows us to use just one language - JavaScript - both at the front end and at the back end without needing to master other (and often more complex) languages, such as Ruby or C++.

In a nutshell, Node.js is one of the key tools that enable us to become full-stack developers with just one language: JavaScript.

### ⭐️ Node.js enables us to build scaleable applications
...and is much faster compared to e.g. Python or Ruby _and_ can handle multiple simultaneous client - server connections with plenty of throughput (i.e. input - output per time unit), which makes it possible to build scaleable applications. 

### ⭐️ Node.js is the largest repository of packages
... which extend Node's basic functionality almost unlimitedly.

### ⭐️ There's  a large Node.js community out there
... so plenty of formal and informal support, should you ever need it.

### Summing up Node's key features: 
Node.js
* is fast, compared to e.g. Python

* is easy to use

* is versatile, thanks to an enormous pool of open-source packages 

* enables us to build scaleable applications

* spans the full stack, using JavaScript for both client and server operations

* allows us to handle several tasks at the same time by means of its *single main thread* - the **event loop** - and a **threadpool** of four additional threads

* relies on callbacks, i.e. functions that are called and executed without blocking the the system.




## :orange_book: Basic reading list
A concise introduction to Node.js:
https://www.oreilly.com/library/view/node-up-and/9781449332235/ch01.html
A more in-depth, but accessible introduction to Node.js:
https://www.infoworld.com/article/3210589/node-js/what-is-nodejs-javascript-runtime-explained.html
The event loop:
https://flaviocopes.com/node-event-loop/
Node.js documentation:
https://nodejs.org/en/
Packages and modules
https://docs.npmjs.com/getting-started/packages


## :books: Sources consulted for this guide


https://nodejs.org/en/

https://www.npmjs.com/

https://docs.npmjs.com/getting-started/packages

https://developer.mozilla.org/en-US/docs/Glossary/Node.js?utm_source=wordpress%20blog&utm_medium=content%20link&utm_campaign=promote%20mdn

https://www.oreilly.com/library/view/node-up-and/9781449332235/ch01.html

https://medium.com/@krissanawat/2-ways-to-install-nodejs-on-macos-the-beginners-guide-55c457e66441

http://osxdaily.com/2018/06/29/how-install-nodejs-npm-mac/

https://nodejs.org/en/docs/guides/blocking-vs-non-blocking/

https://nodejs.org/en/docs/guides/dont-block-the-event-loop/

https://www.sitepoint.com/an-introduction-to-node-js/

https://medium.freecodecamp.org/what-exactly-is-node-js-ae36e97449f5

https://medium.com/the-node-js-collection/what-you-should-know-to-really-understand-the-node-js-event-loop-and-its-metrics-c4907b19da4c

https://medium.com/front-end-hacking/client-server-and-shared-code-846097c5260e

https://flaviocopes.com/node-event-loop/

https://hackernoon.com/in-simple-terms-backend-code-frontend-code-and-how-they-interact-2485c5a1bbd2

https://flaviocopes.com/nodejs-parse-json/

https://flaviocopes.com/npm-packages-local-global/

https://hackernoon.com/elixir-the-new-wave-or-an-elegant-niche-5e38b4de0783

http://www.dataserve-retro.co.uk/contents/en-uk/d188.html

https://www.sinclairzxworld.com/viewtopic.php?t=211

https://bluecomputerblog.com/articles/machine-code-1-bin-hex

https://cloud.google.com/appengine/docs/standard/nodejs/runtime

https://medium.com/@olinations/the-javascript-runtime-environment-d58fa2e60dd0

https://ac.els-cdn.com/S1877050916322037/1-s2.0-S1877050916322037-main.pdf?_tid=67097e85-118f-401d-a20a-7eb3d60a387c&acdnat=1541519909_8c4f3e07fa62118d39ed26c5a94e29a6
