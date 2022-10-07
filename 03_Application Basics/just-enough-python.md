Python is a free and open source programming language. As with other languages you can write the code in any text editor. Python applications require the python interpretor to run the applications. 

The 2 different versions of Python are Python2 and Python3. 

Python2 was developed in the year 2000 and ended development in 2010. Python3 was released in 2008 and is still being developed to this day. 

Python3 had many changes and improvements over Python2, so many so that applications written in Python2 would require many changes to run in Python3. Python3 did not have backward compatibility with Python2.

Some operating systems will come pre-installed with Python3 and you can check the version by running 

`python3 --version` or `python3 -V`

You can have both Python3 and Python2 installed at the same time on a system. 

To run an application using the python interpretor simply type:

`python3 <filename>.py`

Typically applications written in python have the .py extension.

Note: installing python2 typically only requires you to specify python2 but installing python3 will often require the version as well, such as `sudo yum install python36` which would install version 3.6

When you install Python, it also installs the package manager PIP. 

PIP is version dependant, so if you install Python2 you will have pip2 installed and if you have Python3 you will have pip3. 

Installing packages using pip is the same as most other things in Linux, simply run (Note: you may need to run as sudo if you don't have su permissions)

```
pip install <package name>
```

Applications are installed under the /usr/lib or /usr/lib64 directories. They will both contain seperate folder for python2 and python3. In those folder you can find the files under the site-packages directory.

```
usr
	lib
		python2.7
			site-packages
		python3.6
			site-packages
	lib64
		python2.7
			site-packages
		python3.6
			site-packages
```

Running `pip show <package name>` will show you the directory that it is stored under as well as other information about the application.

To check the paths python will use to look for packages you can use the below command

```
python2 -c "import sys; print(sys.path)"
```

This is the default location where the python interpreter will look for packages

You can import the package into an application you are developing by adding the following to the source code:

```python
from flask import Flask, request

app = Flask(__name__)

@app.route('/')
def hello():
	return 'Hello, World'

if __name__=='__main__':
	app.run()
```

Some applications will require a large number of dependencies, you can install them one at a time, or combine them all into a single line

```
pip install flask jinja2 markupsafe
```

Or you can store all the dependencies in a file called requirements.txt (not sure if it has to be that name) and simply point to it during the install

```requirements.txt
Flask==0.10.1

Jinja2==2.7.3

MarkupSafe

Werkzeug
```

```
pip install -r requirements.txt
```

Note: If you don't specify a package version, pip will install the latest one. It's typically bet practice to hardcode the version of a package because a new change could break your application. 

To upgrade a package run the command:

```
pip install flask --upgrade
```

To uninstall a package run the command:

```
pip uninstall flask
```

There are other package managers that can be used with Python. 

The original package manager was called **easy_install** and it would use something called setuptools to package and application into a **.egg** file. Think of this like the .jar archive that java uses. 

You can either use the easy_install utility to install the package

```
easy_install install app
```

Or you could simply download the binaries and place them in a directory that python looks for dependencies. 

.eggs don't have to be unpackaged to be imported into an application. 

Another package manager is called **wheels** and this would package applications into **.whl** files. These files do need to be unpacked before you can import them into an application. You can install a package from a .whl file using pip

```
pip install app.whl
```

