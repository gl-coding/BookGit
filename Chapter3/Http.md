# Http



##Urllib

```python
#encoding=utf8
import jsons
for urllib
import urllib2

data_global = {"info": "world"}
url_addr    = "http://127.0.0.1:8000"

def client_urllib():
    data_json  = json.dumps(data_global)
    client_url = url_addr
    request    = urllib2.Request(client_url)
    request.add_header('content-TYPE', 'application/json')
    f = urllib2.urlopen(request, data=data_json)
    print f.read()
    return f.read()

client_urllib()
```

##Requests

```python
#encoding=utf8
import jsons
import requests

data_global = {"info": "world"}
url_addr    = "http://127.0.0.1:8000"

def client_requests():
    client_url = url_addr
    data_json  = json.dumps(data_global)   #dumps：将python对象解码为json数据
    r_json = requests.post(client_url, data_json)
    print(r_json.text)
    return r_json.text

client_requests()
```

##Webpy

```python
#encoding=utf8
import web

urls = (
     '/', 'hello'
)
app = web.application(urls, globals())

class hello:
    def GET(self):
        info = web.input().info
        return info

    def POST(self):
        info = web.data()
        print type(info)
        return info

if __name__ == "__main__":
    app.run()
```

启动脚本

```bash
python server_webpy.py 8000
```

##Flask

```python
from flask import Flask, request
app = Flask(__name__)

@app.route("/get")
def hello():
    return "Hello World!"

@app.route('/post',methods=["POST"])
def get_tasks():
    if request.method=='POST':
        username=request.form['name']
        return username

if __name__ == "__main__":
    app.run(host='0.0.0.0', port=8000)
```

##Tornado

``` python
import tornado.ioloop
import tornado.web

class GetHandler(tornado.web.RequestHandler):
    def get(self):
        res = self.get_argument("args")
        self.write("hello, " + res)

class PostHandler(tornado.web.RequestHandler):
    #process for post json
    def post(self):
        res = self.request.body
        print res
        self.write(res)

application = tornado.web.Application([
    (r"/", PostHandler),
    (r"/test", GetHandler),
    ])

if __name__ == '__main__':
    application.listen(8000)
    tornado.ioloop.IOLoop.instance().start()
```

2.2.3 性能对比、应用