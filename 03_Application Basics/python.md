Python is a free and open source programming language. Python applications require the python interpretor to run.

#### Installing Python
Some distributions of Linux come with Python pre-installed. If you need to install it use the below depending on the version: 

``` Debian/Ubuntu
sudo apt install python3 

OR

sudo apt install python2
```

#### Versions in Python
Python has two versions, Python 2 for legacy applications and Python 3 is the up-to-date version. 

There were changes that occurred between 2 and 3 that made applications written on 2 incompatible with 3.  

You can have both versions installed on the same host and when you run commands you need to make sure you're running them for the correct versions. 

#### Check version
```
python2/3 -V
```

#### Running an application
Applications written in python have the extension .py
```
python2/3 app.py
```

#### Terminating an application
```
pkill python

OR

pkill -f name-of-script
```

#### Installing packages
When you install Python, the package manager [[PIP]] is also installed. To install a package use:
```
pip2/3 install <package_name>
```
Each version has it's own version of PIP so if you're running versions 2 and 3 on the same host you will need to make sure to run the correct PIP command. 

#### Package directory
When you install a package it is installed in one of the below directories depending on the version and architecture
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

To view the directories Python is using to store packages you can use:
```
python2/3 -c "import sys; print(sys.path)"
```

To veiw the directory the package has been installed under use:
```
pip show <package_name>
```

#### Using a package in an application
When a Python module or package is imported, __name__ is set to the module’s name. Usually, this is the name of the Python file itself without the .py extension
```python
from flask import Flask, request

app = Flask(__name__)

@app.route('/')
def hello():
	return 'Hello, World'

if __name__=='__main__':
	app.run()
```

#### Package dependencies
Some packages will require dependcies to run. Typically applications will tell you what packages to install and you can view the requirement in the **pip show** command. 

#### Installing dependencies
An easy way to install the dependencies is to use list the applications and their versions in a requirements.txt file. Then to install them use:
```
pip install -r requirements.txt
```

#### Package Versions
It is best practice to specify the version for each dependency in the requirements file so new versions don't break your application. 

To specify a version use:
```
Flask==0.10.1

Jinja2==2.7.3
```

#### Upgrade a package
Sometime you may need to upgrade a package. To do this use:
```
pip install flask --upgrade
```

#### Uninstall a package
```
pip uninstall flask
```

[[flask]]
[[gunicorn]]
