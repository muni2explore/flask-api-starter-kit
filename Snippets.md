# Code Snippet


### Return JSON Response
```python

from flask import Flask, jsonify

app = Flask(__name__)

@app.route('/')
def hello():
    return jsonify(message="Hello, Muni!")


if __name__ == '__main__':
    app.run() 
```

### Response with Status Code

```python

from flask import Flask, jsonify

app = Flask(__name__)

@app.route('/')
def hello():
    return jsonify(message="Hello, Muni!"), 200
    
@app.route('/not_found')
def not_found():
    return jsonify(message="That resource was not found!"), 404


if __name__ == '__main__':
    app.run()    
```

### Getting URL Param

```python

from flask import Flask, jsonify, request

app = Flask(__name__)

@app.route('/parameters')
def parameters():
    name = request.args.get('name')
    age = int(request.args.get('age'))
    if age < 18:
        return jsonify(message="Sorry "+name+", you are not old enough"), 401
    else:
        return jsonify(message="Welcome "+name+", you are old enough"), 401


if __name__ == '__main__':
    app.run() 
```


### URL Variables and Conversion Filters

```python
from flask import Flask, jsonify, request

app = Flask(__name__)

@app.route('/url_variables/<string:name>/<int:age>')
def url_variables(name:str, age: int):
    if age < 18:
        return jsonify(message="Sorry "+name+", you are not old enough"), 401
    else:
        return jsonify(message="Welcome "+name+", you are old enough"), 401
    

if __name__ == '__main__':
    app.run()   
```


### SQLAlchemy Setup

```python
from flask import Flask, jsonify, request
from flask_sqlalchemy import SQLAlchemy
from sqlalchemy import Column, Integer, String, Float
import os

app = Flask(__name__)
basedir = os.path.abspath(os.path.dirname(__file__))
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///'+ os.path.join(basedir, 'planets.db') 

@app.route('/url_variables/<string:name>/<int:age>')
def url_variables(name:str, age: int):
    if age < 18:
        return jsonify(message="Sorry "+name+", you are not old enough"), 401
    else:
        return jsonify(message="Welcome "+name+", you are old enough"), 401
    

if __name__ == '__main__':
    app.run()   
```
