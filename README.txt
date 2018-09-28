curl http://127.0.0.1:5000/


#
#https://flask-restful.readthedocs.io/en/0.3.5/quickstart.html
#{
#    "hello": "world"
#}
#
import requests
res = requests.post('http://localhost:5000/api/add_message/1234', json={"mytext":"lalala"})
if res.ok:
    print (res.json())


#https://stackoverflow.com/questions/20001229/how-to-get-posted-json-in-flask

from flask import Flask
from flask_restful import Resource, Api

app = Flask(__name__)
api = Api(app)

class HelloWorld(Resource):
    def get(self):
        return {'hello': 'world'}

api.add_resource(HelloWorld, '/')

if __name__ == '__main__':
    app.run(debug=True)
from flask import Flask, request, jsonify
app = Flask(__name__)

@app.route('/api/add_message/<uuid>', methods=['GET', 'POST'])
def add_message(uuid):
    content = request.json
    print (content['mytext'])
    return jsonify({"uuid":uuid})

if __name__ == '__main__':
    app.run(host= '0.0.0.0',port=5000, debug=True)
