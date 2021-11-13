# Code Snippet


### Return JSON Response
```python

from flask import Flask, jsonify

app = Flask()

@app.route('/')
def hello():
    return jsonify(message="Hello, Muni!")


if __name__ == '__main__':
    app.run()
    
```

### Response with Status Code

```python

from flask import Flask, jsonify

app = Flask()

@app.route('/')
def hello():
    return jsonify(message="Hello, Muni!")
    
@app.route('/not_found')
def not_found():
    return jsonify(message="That resource was not found!"), 404


if __name__ == '__main__':
    app.run()
    
```
