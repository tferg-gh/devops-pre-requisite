Node.JS is a Javascript runtime designed to build scalable network applications. Typically Javascript was used only for client-side web pages but Node.JS brings it to the backend. 

#### Installing Node.JS
To install Node.JS with a package manager go here for instructions:
https://github.com/nodesource/distributions
``` Ubuntu/Debian
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install nodejs -y
```

#### Check version
```
node -v
```

#### Running an application
Applications written in JavaScript have the .js extension
```
node myapp.js
```

#### Package Managment
Node.JS installs the package manager **npm** on install. 

You can view the website here: https://www.npmjs.com/

#### NPM
NPM stands for Node Package Manager and it's a public repository for Node.JS packages. 

#### Check NPM Version
```
npm -v
```

#### Search the NPM respository
```
npm search <package_name>
```

#### Install a package locally using NPM
```
npm install <package_name>
```
This installs the package into your current working directory

#### Installing a package from file
If you download a node.js application from git or somewhere else, simply navigating to the directory and running:
```
npm install
```
Will install the package and dependencies.

#### Uninstall a package
``` shell
npm uninstall <package-name> # Use -g for global
```

#### Package Directory
When you install a package it installs in your current working directory under node_modules:
```
/node_modules
	/package_name
		LICENSE
		README.md
		package.json
		/lib
```

#### Package.json
This contains all the metadata about the package including the git repo and the dependencies

#### Install a global package using NPM
```
npm install <package_name> -g
```

#### Import a packge into code
``` javascript
var file = require("file");

file.mkdirs("/tmp/dir1")
```
When you import a package into your code, Node.JS will first look to the local directory for modules, then it will check the global directory

#### Check your directory order
You can check what paths Node is using and the order it checks them for modules by using:
```
node -e "console.log(module.paths)"
```

#### Built-in Modules
These are installed with Node.JS and are located here:
```
/usr/lib/node_modules/npm/node_modules
```

#### External Modules 
These are modules you install globally from something like **npm**. These are located here:
```
/usr/lib/node_modules
```

#### Dependencies
The package.json file will determine the dependencies that are installed when you install the package using the npm install command

#### Running the application
Once you've downloaded or developed the source code you can run the application either by using:
```
node app.js
```
Or, in the package.json file there may be some scripts you can run using npm depending on what you want to do
```
npm run <script_name>
```
The script name is defined at the start of the script in the package.json

Typically you don't want to run your node application like this in a production environment. It's not resilient and if the application crashes it won't come back up on it's on causing downtime. 

You want to use a process manager like [[supervisord]], [[forever]] and [[pm2]] to run the application and they'll have things like built in load balancers. 