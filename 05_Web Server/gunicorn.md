Running an application in gUnicorn 

```
gunicorn main:app
```

Where main is the file name and app is the component name

```python
main.py
from flask import Flask, request

app = Flask(__name__)

@app.route('/')
def hello():
	return 'Hello, World'

if __name__=='__main__':
	app.run()
```

You can add additional workers by using the -w X option

```
gunicorn main:app -w 2
```

#### Version
```
gunicorn -version
```