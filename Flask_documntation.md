# What is Flask?
<p>Flask is a web application framework written in Python. It is developed by Armin Ronacher, who leads an international group 
of Python enthusiasts named Pocco.
Flask is based on the Werkzeug WSGI toolkit and Jinja2 template engine.</p>
 
Jinja2
Jinja2 is a popular templating engine for Python. A web templating system combines a template with a certain data source to render dynamic web pages.

Flask is often referred to as a micro framework. It aims to keep the core of an application simple yet extensible. 
Flask does not have built-in abstraction layer for database handling, nor does it have form a validation support. 
Instead, Flask supports the extensions to add such functionality to the application.

How to install flask
pip install Flask

In this example, ‘/’ URL is bound with hello_world() function. Hence, when the home page of web server 
is opened in browser, the output of this function will be rendered.

from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
   return 'Hello World’

if __name__ == '__main__':
   app.run()

The route() function of the Flask class is a decorator, which tells the application which URL should call the associated function.

Finally the run() method of Flask class runs the application on the local development server.

The above given Python script is executed from Python shell.
Python Hello.py

A message in Python shell informs you that
* Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)

Open the above URL (localhost:5000) in the browser. ‘Hello World’ message will be displayed on it.

However, while the application is under development, it should be restarted manually for each change in the code. 
To avoid this inconvenience, enable debug support. The server will then reload itself if the code changes. 
It will also provide a useful debugger to track the errors if any, in the application.

app.run(debug = True)

Simple way to render different pages Uisng Flask can be done

from flask import Flask,render_template, Response

app=Flask(__name__)

@app.route('/')
def index():
    return render_template('index.html')


@app.route('/about')
def about():
    return render_template('about.html')


@app.route('/contact')
def contact():
    return render_template('contact.html')


@app.route('/login')
def login():
    return render_template('login.html')

if __name__ == '__main__':
   app.run(debug = True)

All the html files can be stored in folder called templates and all pictures and 
css files used in the project can be stored in static files followed by css,images file name.

In order to demonstrate the use of POST method in URL routing, first let us create an HTML form and use the POST method to send form data to a URL.

<html>
   <body>
      <form action = "http://localhost:5000/login" method = "post">
         <p>Enter Name:</p>
         <p><input type = "text" name = "nm" /></p>
         <p><input type = "submit" value = "submit" /></p>
      </form>
   </body>
</html>

Usage for jinja tag in the code

Flask uses jinja2 template engine. A web template contains HTML syntax interspersed placeholders for variables and expressions 
(in these case Python expressions) which are replaced values when the template is rendered.

from flask import Flask, render_template
app = Flask(__name__)

@app.route('/result')
def result():
   dict = {'phy':50,'che':60,'maths':70}
   return render_template('result.html', result = dict)

if __name__ == '__main__':
   app.run(debug = True)

HTML script as result.html in the templates folder.

<!doctype html>
<html>
   <body>
      <table border = 1>
         {% for key, value in result.items() %}
            <tr>
               <th> {{ key }} </th>
               <td> {{ value }} </td>
            </tr>
         {% endfor %}
      </table>
   </body>
</html>







