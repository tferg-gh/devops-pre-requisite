History

Previously websites were simple, plain text pages with links and images made with html and css. JavaScript allowed us to make more modern, intelligent and interactive websites that we see today.

When we talk about websites we can think of them in two parts, the client-side and the server-side. Front end and back end. The client-side is what the users see, while the server-side is like the database. 

JavaScript frameworks were typically only on the Client-side and back end was usually coded in something like Java, Python or Ruby. 

Client-side Frameworks:
- jQuery
- Angular.JS
- React.JS
- Vue.JS
- Ember.JS
- Backbone.JS

Node.JS brought javascript to the back end.

Node.JS is a free and opensource server-side javascript environment. You can use it to develop applications such as webservers using javascript. 

An important feature that distinguishes Node.JS from other tools is its ability to handle many concurrent connections by implementing a non-blocking IO model (#research)

Installation

Instructions for how to install Node.JS is on their website. If you're downloading and installing it via a command line you'll want to go to the NodeSource github page

https://github.com/nodesource/distributions

Once installed you can check the version using the command: `node -v`

Running a file in Node.JS using the command is very straight forward. You just have to type `node /PATH/To/File.js` 

Typically files with .js are written in javascript

Node Package Manager (NPM)

When you install Node.JS you also install the public package manager NPM. You can check the version using the command `npm -v`

NPM is a public repository where devlopers can upload their projects and make them available to everyone. 

You can search for a package in the repository by using the `npm seach <search term>` command where the search term is whatever name or part of a name you're looking for. 

When you've found a package you want to download, you can install it using the command `npm install <package name>`

This will install the package under node_modules in your current working directory.  The application name will be the folder the application is installed under and will include files like the license, readme and package.json file. The source code will be in the lib folder. Note the package.json file contains the metadata about the application including the dependencies. 

To import a package into an existing project you simply need to include it as so:

``` javascript
var file = require("file");

file.mkdirs("/tmp/dir1")
```

Node.JS will attempt to load the package from the local node_modules directory before referring to the global directory. 

You can view the paths and the order Node.JS will check them by running the below command:

```
node -e "console.log(module.paths)"
```

Adding the -g option when you're running the npm install command will install the package globally. 

There are two kinds of modules, Built-in Modules and External Modules. When you install Node.JS it also installs all the built-in modules such as:

- fs - To handle filesystem
- http - to host an HTTP server
- os - to work with the operating system
- events - to handle events
- tls - to implement TLS and SSL
- url - to parse URL strings

These are located under `/usr/lib/node_modules/npm/node_modules`

External Modules are downloaded and installed from the package manager and are typically stored in `/usr/lib/node_modules` if they're global. 

Some popular external modules include:

- express - Fast, unopinionated, minimalist web framework
- react - To create user interfaces
- debug - To debug applications
- async - To work with asynchornous JS
- lodash - To work with arrays, objects, strings etc.

Applications will have a list of dependencies in the package.json file which outlines the name and version of the applications. These packages may also have their own dependencies. 