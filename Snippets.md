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
