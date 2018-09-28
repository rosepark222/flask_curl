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





server.py then do the following 


 1640  curl -X PUT http://127.0.0.1:5000/1/ -d text="flask api is teh awesomez"
 1641  curl -X PUT http://127.0.0.1:5000/1/ -d text="flask api is teh awesomez" -v 
 1642  curl -X DELETE http://127.0.0.1:5000/1/ -d text="flask api is teh awesomez" -v 
 1643  curl -X PUT http://127.0.0.1:5000/1/ -d text="flask api is teh awesomez" -v 
 1644  curl -X POST http://0.0.0.0:5000/api/add_message/1234 -d text="flask api is teh awesomez" -v 
 1645  curl -X POST http://0.0.0.0:5000/api/add_message/1234 -d json={"mytext":"lalala"}  -v 
 1646  curl -X POST http://0.0.0.0:5000/api/add_message/1234 -d '{"mytext":"lalala"}'  -v 
 1647  git add .
 1648  history


127.0.0.1 - - [28/Sep/2018 15:00:01] "POST /api/add_message/1234 HTTP/1.1" 500 -
Traceback (most recent call last):
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 2309, in __call__
    return self.wsgi_app(environ, start_response)
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 2295, in wsgi_app
    response = self.handle_exception(e)
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 1741, in handle_exception
    reraise(exc_type, exc_value, tb)
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/_compat.py", line 35, in reraise
    raise value
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 2292, in wsgi_app
    response = self.full_dispatch_request()
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 1815, in full_dispatch_request
    rv = self.handle_user_exception(e)
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 1718, in handle_user_exception
    reraise(exc_type, exc_value, tb)
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/_compat.py", line 35, in reraise
    raise value
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 1813, in full_dispatch_request
    rv = self.dispatch_request()
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 1799, in dispatch_request
    return self.view_functions[rule.endpoint](**req.view_args)
  File "/home/youngpark/tmp/flask_curl/server.py", line 7, in add_message
    print (content['mytext'])
TypeError: 'NoneType' object is not subscriptable
127.0.0.1 - - [28/Sep/2018 15:00:25] "POST /api/add_message/1234 HTTP/1.1" 500 -
Traceback (most recent call last):
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 2309, in __call__
    return self.wsgi_app(environ, start_response)
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 2295, in wsgi_app
    response = self.handle_exception(e)
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 1741, in handle_exception
    reraise(exc_type, exc_value, tb)
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/_compat.py", line 35, in reraise
    raise value
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 2292, in wsgi_app
    response = self.full_dispatch_request()
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 1815, in full_dispatch_request
    rv = self.handle_user_exception(e)
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 1718, in handle_user_exception
    reraise(exc_type, exc_value, tb)
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/_compat.py", line 35, in reraise
    raise value
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 1813, in full_dispatch_request
    rv = self.dispatch_request()
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 1799, in dispatch_request
    return self.view_functions[rule.endpoint](**req.view_args)
  File "/home/youngpark/tmp/flask_curl/server.py", line 7, in add_message
    print (content['mytext'])
TypeError: 'NoneType' object is not subscriptable




<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
  "http://www.w3.org/TR/html4/loose.dtd">
<html>
  <head>
    <title>TypeError: 'NoneType' object is not subscriptable // Werkzeug Debugger</title>
    <link rel="stylesheet" href="?__debugger__=yes&amp;cmd=resource&amp;f=style.css"
        type="text/css">
    <!-- We need to make sure this has a favicon so that the debugger does
         not by accident trigger a request to /favicon.ico which might
         change the application state. -->
    <link rel="shortcut icon"
        href="?__debugger__=yes&amp;cmd=resource&amp;f=console.png">
    <script src="?__debugger__=yes&amp;cmd=resource&amp;f=jquery.js"></script>
    <script src="?__debugger__=yes&amp;cmd=resource&amp;f=debugger.js"></script>
    <script type="text/javascript">
      var TRACEBACK = 140544604078432,
          CONSOLE_MODE = false,
          EVALEX = true,
          EVALEX_TRUSTED = false,
          SECRET = "FksjeIbgLYhHZWGEQSbl";
    </script>
  </head>
  <body style="background-color: #fff">
    <div class="debugger">
<h1>builtins.TypeError</h1>
<div class="detail">
  <p class="errormsg">TypeError: 'NoneType' object is not subscriptable</p>
</div>
<h2 class="traceback">Traceback <em>(most recent call last)</em></h2>
<div class="traceback">
  
  <ul><li><div class="frame" id="frame-140544604078264">
  <h4>File <cite class="filename">"/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py"</cite>,
      line <em class="line">2309</em>,
      in <code class="function">__call__</code></h4>
  <div class="source"><pre class="line before"><span class="ws"></span> </pre>
<pre class="line before"><span class="ws">    </span>def __call__(self, environ, start_response):</pre>
<pre class="line before"><span class="ws">        </span>&quot;&quot;&quot;The WSGI server calls the Flask application object as the</pre>
<pre class="line before"><span class="ws">        </span>WSGI application. This calls :meth:`wsgi_app` which can be</pre>
<pre class="line before"><span class="ws">        </span>wrapped to applying middleware.&quot;&quot;&quot;</pre>
<pre class="line current"><span class="ws">        </span>return self.wsgi_app(environ, start_response)</pre>
<pre class="line after"><span class="ws"></span> </pre>
<pre class="line after"><span class="ws">    </span>def __repr__(self):</pre>
<pre class="line after"><span class="ws">        </span>return '&lt;%s %r&gt;' % (</pre>
<pre class="line after"><span class="ws">            </span>self.__class__.__name__,</pre>
<pre class="line after"><span class="ws">            </span>self.name,</pre></div>
</div>

<li><div class="frame" id="frame-140544604079216">
  <h4>File <cite class="filename">"/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py"</cite>,
      line <em class="line">2295</em>,
      in <code class="function">wsgi_app</code></h4>
  <div class="source"><pre class="line before"><span class="ws">            </span>try:</pre>
<pre class="line before"><span class="ws">                </span>ctx.push()</pre>
<pre class="line before"><span class="ws">                </span>response = self.full_dispatch_request()</pre>
<pre class="line before"><span class="ws">            </span>except Exception as e:</pre>
<pre class="line before"><span class="ws">                </span>error = e</pre>
<pre class="line current"><span class="ws">                </span>response = self.handle_exception(e)</pre>
<pre class="line after"><span class="ws">            </span>except:</pre>
<pre class="line after"><span class="ws">                </span>error = sys.exc_info()[1]</pre>
<pre class="line after"><span class="ws">                </span>raise</pre>
<pre class="line after"><span class="ws">            </span>return response(environ, start_response)</pre>
<pre class="line after"><span class="ws">        </span>finally:</pre></div>
</div>

<li><div class="frame" id="frame-140544604079272">
  <h4>File <cite class="filename">"/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py"</cite>,
      line <em class="line">1741</em>,
      in <code class="function">handle_exception</code></h4>
  <div class="source"><pre class="line before"><span class="ws">            </span># if we want to repropagate the exception, we can attempt to</pre>
<pre class="line before"><span class="ws">            </span># raise it with the whole traceback in case we can do that</pre>
<pre class="line before"><span class="ws">            </span># (the function was actually called from the except part)</pre>
<pre class="line before"><span class="ws">            </span># otherwise, we just raise the error again</pre>
<pre class="line before"><span class="ws">            </span>if exc_value is e:</pre>
<pre class="line current"><span class="ws">                </span>reraise(exc_type, exc_value, tb)</pre>
<pre class="line after"><span class="ws">            </span>else:</pre>
<pre class="line after"><span class="ws">                </span>raise e</pre>
<pre class="line after"><span class="ws"></span> </pre>
<pre class="line after"><span class="ws">        </span>self.log_exception((exc_type, exc_value, tb))</pre>
<pre class="line after"><span class="ws">        </span>if handler is None:</pre></div>
</div>

<li><div class="frame" id="frame-140544604079328">
  <h4>File <cite class="filename">"/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/_compat.py"</cite>,
      line <em class="line">35</em>,
      in <code class="function">reraise</code></h4>
  <div class="source"><pre class="line before"><span class="ws">    </span>from io import StringIO</pre>
<pre class="line before"><span class="ws"></span> </pre>
<pre class="line before"><span class="ws">    </span>def reraise(tp, value, tb=None):</pre>
<pre class="line before"><span class="ws">        </span>if value.__traceback__ is not tb:</pre>
<pre class="line before"><span class="ws">            </span>raise value.with_traceback(tb)</pre>
<pre class="line current"><span class="ws">        </span>raise value</pre>
<pre class="line after"><span class="ws"></span> </pre>
<pre class="line after"><span class="ws">    </span>implements_to_string = _identity</pre>
<pre class="line after"><span class="ws"></span> </pre>
<pre class="line after"><span class="ws"></span>else:</pre>
<pre class="line after"><span class="ws">    </span>text_type = unicode</pre></div>
</div>

<li><div class="frame" id="frame-140544604078712">
  <h4>File <cite class="filename">"/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py"</cite>,
      line <em class="line">2292</em>,
      in <code class="function">wsgi_app</code></h4>
  <div class="source"><pre class="line before"><span class="ws">        </span>ctx = self.request_context(environ)</pre>
<pre class="line before"><span class="ws">        </span>error = None</pre>
<pre class="line before"><span class="ws">        </span>try:</pre>
<pre class="line before"><span class="ws">            </span>try:</pre>
<pre class="line before"><span class="ws">                </span>ctx.push()</pre>
<pre class="line current"><span class="ws">                </span>response = self.full_dispatch_request()</pre>
<pre class="line after"><span class="ws">            </span>except Exception as e:</pre>
<pre class="line after"><span class="ws">                </span>error = e</pre>
<pre class="line after"><span class="ws">                </span>response = self.handle_exception(e)</pre>
<pre class="line after"><span class="ws">            </span>except:</pre>
<pre class="line after"><span class="ws">                </span>error = sys.exc_info()[1]</pre></div>
</div>

<li><div class="frame" id="frame-140544604079440">
  <h4>File <cite class="filename">"/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py"</cite>,
      line <em class="line">1815</em>,
      in <code class="function">full_dispatch_request</code></h4>
  <div class="source"><pre class="line before"><span class="ws">            </span>request_started.send(self)</pre>
<pre class="line before"><span class="ws">            </span>rv = self.preprocess_request()</pre>
<pre class="line before"><span class="ws">            </span>if rv is None:</pre>
<pre class="line before"><span class="ws">                </span>rv = self.dispatch_request()</pre>
<pre class="line before"><span class="ws">        </span>except Exception as e:</pre>
<pre class="line current"><span class="ws">            </span>rv = self.handle_user_exception(e)</pre>
<pre class="line after"><span class="ws">        </span>return self.finalize_request(rv)</pre>
<pre class="line after"><span class="ws"></span> </pre>
<pre class="line after"><span class="ws">    </span>def finalize_request(self, rv, from_error_handler=False):</pre>
<pre class="line after"><span class="ws">        </span>&quot;&quot;&quot;Given the return value from a view function this finalizes</pre>
<pre class="line after"><span class="ws">        </span>the request by converting it into a response and invoking the</pre></div>
</div>

<li><div class="frame" id="frame-140544604079496">
  <h4>File <cite class="filename">"/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py"</cite>,
      line <em class="line">1718</em>,
      in <code class="function">handle_user_exception</code></h4>
  <div class="source"><pre class="line before"><span class="ws">            </span>return self.handle_http_exception(e)</pre>
<pre class="line before"><span class="ws"></span> </pre>
<pre class="line before"><span class="ws">        </span>handler = self._find_error_handler(e)</pre>
<pre class="line before"><span class="ws"></span> </pre>
<pre class="line before"><span class="ws">        </span>if handler is None:</pre>
<pre class="line current"><span class="ws">            </span>reraise(exc_type, exc_value, tb)</pre>
<pre class="line after"><span class="ws">        </span>return handler(e)</pre>
<pre class="line after"><span class="ws"></span> </pre>
<pre class="line after"><span class="ws">    </span>def handle_exception(self, e):</pre>
<pre class="line after"><span class="ws">        </span>&quot;&quot;&quot;Default exception handling that kicks in when an exception</pre>
<pre class="line after"><span class="ws">        </span>occurs that is not caught.  In debug mode the exception will</pre></div>
</div>

<li><div class="frame" id="frame-140544604079552">
  <h4>File <cite class="filename">"/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/_compat.py"</cite>,
      line <em class="line">35</em>,
      in <code class="function">reraise</code></h4>
  <div class="source"><pre class="line before"><span class="ws">    </span>from io import StringIO</pre>
<pre class="line before"><span class="ws"></span> </pre>
<pre class="line before"><span class="ws">    </span>def reraise(tp, value, tb=None):</pre>
<pre class="line before"><span class="ws">        </span>if value.__traceback__ is not tb:</pre>
<pre class="line before"><span class="ws">            </span>raise value.with_traceback(tb)</pre>
<pre class="line current"><span class="ws">        </span>raise value</pre>
<pre class="line after"><span class="ws"></span> </pre>
<pre class="line after"><span class="ws">    </span>implements_to_string = _identity</pre>
<pre class="line after"><span class="ws"></span> </pre>
<pre class="line after"><span class="ws"></span>else:</pre>
<pre class="line after"><span class="ws">    </span>text_type = unicode</pre></div>
</div>

<li><div class="frame" id="frame-140544604079104">
  <h4>File <cite class="filename">"/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py"</cite>,
      line <em class="line">1813</em>,
      in <code class="function">full_dispatch_request</code></h4>
  <div class="source"><pre class="line before"><span class="ws">        </span>self.try_trigger_before_first_request_functions()</pre>
<pre class="line before"><span class="ws">        </span>try:</pre>
<pre class="line before"><span class="ws">            </span>request_started.send(self)</pre>
<pre class="line before"><span class="ws">            </span>rv = self.preprocess_request()</pre>
<pre class="line before"><span class="ws">            </span>if rv is None:</pre>
<pre class="line current"><span class="ws">                </span>rv = self.dispatch_request()</pre>
<pre class="line after"><span class="ws">        </span>except Exception as e:</pre>
<pre class="line after"><span class="ws">            </span>rv = self.handle_user_exception(e)</pre>
<pre class="line after"><span class="ws">        </span>return self.finalize_request(rv)</pre>
<pre class="line after"><span class="ws"></span> </pre>
<pre class="line after"><span class="ws">    </span>def finalize_request(self, rv, from_error_handler=False):</pre></div>
</div>

<li><div class="frame" id="frame-140544604079664">
  <h4>File <cite class="filename">"/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py"</cite>,
      line <em class="line">1799</em>,
      in <code class="function">dispatch_request</code></h4>
  <div class="source"><pre class="line before"><span class="ws">        </span># request came with the OPTIONS method, reply automatically</pre>
<pre class="line before"><span class="ws">        </span>if getattr(rule, 'provide_automatic_options', False) \</pre>
<pre class="line before"><span class="ws">           </span>and req.method == 'OPTIONS':</pre>
<pre class="line before"><span class="ws">            </span>return self.make_default_options_response()</pre>
<pre class="line before"><span class="ws">        </span># otherwise dispatch to the handler for that endpoint</pre>
<pre class="line current"><span class="ws">        </span>return self.view_functions[rule.endpoint](**req.view_args)</pre>
<pre class="line after"><span class="ws"></span> </pre>
<pre class="line after"><span class="ws">    </span>def full_dispatch_request(self):</pre>
<pre class="line after"><span class="ws">        </span>&quot;&quot;&quot;Dispatches the request and on top of that performs request</pre>
<pre class="line after"><span class="ws">        </span>pre and postprocessing as well as HTTP exception catching and</pre>
<pre class="line after"><span class="ws">        </span>error handling.</pre></div>
</div>

<li><div class="frame" id="frame-140544604079720">
  <h4>File <cite class="filename">"/home/youngpark/tmp/flask_curl/server.py"</cite>,
      line <em class="line">7</em>,
      in <code class="function">add_message</code></h4>
  <div class="source"><pre class="line before"><span class="ws"></span>app = Flask(__name__)</pre>
<pre class="line before"><span class="ws"></span> </pre>
<pre class="line before"><span class="ws"></span>@app.route('/api/add_message/&lt;uuid&gt;', methods=['GET', 'POST'])</pre>
<pre class="line before"><span class="ws"></span>def add_message(uuid):</pre>
<pre class="line before"><span class="ws">    </span>content = request.json</pre>
<pre class="line current"><span class="ws">    </span>print (content['mytext'])</pre>
<pre class="line after"><span class="ws">    </span>return jsonify({&quot;uuid&quot;:uuid})</pre>
<pre class="line after"><span class="ws"></span> </pre>
<pre class="line after"><span class="ws"></span>if __name__ == '__main__':</pre>
<pre class="line after"><span class="ws">    </span>app.run(host= '0.0.0.0',port=5000, debug=True)</pre></div>
</div>
</ul>
  <blockquote>TypeError: 'NoneType' object is not subscriptable</blockquote>
</div>

<div class="plain">
  <form action="/?__debugger__=yes&amp;cmd=paste" method="post">
    <p>
      <input type="hidden" name="language" value="pytb">
      This is the Copy/Paste friendly version of the traceback.  <span
      class="pastemessage">You can also paste this traceback into
      a <a href="https://gist.github.com/">gist</a>:
      <input type="submit" value="create paste"></span>
    </p>
    <textarea cols="50" rows="10" name="code" readonly>Traceback (most recent call last):
  File &quot;/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py&quot;, line 2309, in __call__
    return self.wsgi_app(environ, start_response)
  File &quot;/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py&quot;, line 2295, in wsgi_app
    response = self.handle_exception(e)
  File &quot;/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py&quot;, line 1741, in handle_exception
    reraise(exc_type, exc_value, tb)
  File &quot;/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/_compat.py&quot;, line 35, in reraise
    raise value
  File &quot;/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py&quot;, line 2292, in wsgi_app
    response = self.full_dispatch_request()
  File &quot;/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py&quot;, line 1815, in full_dispatch_request
    rv = self.handle_user_exception(e)
  File &quot;/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py&quot;, line 1718, in handle_user_exception
    reraise(exc_type, exc_value, tb)
  File &quot;/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/_compat.py&quot;, line 35, in reraise
    raise value
  File &quot;/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py&quot;, line 1813, in full_dispatch_request
    rv = self.dispatch_request()
  File &quot;/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py&quot;, line 1799, in dispatch_request
    return self.view_functions[rule.endpoint](**req.view_args)
  File &quot;/home/youngpark/tmp/flask_curl/server.py&quot;, line 7, in add_message
    print (content['mytext'])
TypeError: 'NoneType' object is not subscriptable</textarea>
  </form>
</div>
<div class="explanation">
  The debugger caught an exception in your WSGI application.  You can now
  look at the traceback which led to the error.  <span class="nojavascript">
  If you enable JavaScript you can also use additional features such as code
  execution (if the evalex feature is enabled), automatic pasting of the
  exceptions and much more.</span>
</div>
      <div class="footer">
        Brought to you by <strong class="arthur">DON'T PANIC</strong>, your
        friendly Werkzeug powered traceback interpreter.
      </div>
    </div>

    <div class="pin-prompt">
      <div class="inner">
        <h3>Console Locked</h3>
        <p>
          The console is locked and needs to be unlocked by entering the PIN.
          You can find the PIN printed out on the standard output of your
          shell that runs the server.
        <form>
          <p>PIN:
            <input type=text name=pin size=14>
            <input type=submit name=btn value="Confirm Pin">
        </form>
      </div>
    </div>
  </body>
</html>

<!--

Traceback (most recent call last):
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 2309, in __call__
    return self.wsgi_app(environ, start_response)
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 2295, in wsgi_app
    response = self.handle_exception(e)
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 1741, in handle_exception
    reraise(exc_type, exc_value, tb)
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/_compat.py", line 35, in reraise
    raise value
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 2292, in wsgi_app
    response = self.full_dispatch_request()
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 1815, in full_dispatch_request
    rv = self.handle_user_exception(e)
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 1718, in handle_user_exception
    reraise(exc_type, exc_value, tb)
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/_compat.py", line 35, in reraise
    raise value
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 1813, in full_dispatch_request
    rv = self.dispatch_request()
  File "/home/youngpark/miniconda3/envs/tf4/lib/python3.6/site-packages/flask/app.py", line 1799, in dispatch_request
    return self.view_functions[rule.endpoint](**req.view_args)
  File "/home/youngpark/tmp/flask_curl/server.py", line 7, in add_message
    print (content['mytext'])
TypeError: 'NoneType' object is not subscriptable

-->
