> **Note**, this content was originally posted on the [Repl Talk Forum](https://repl.it/talk/learn/Make-Your-Own-Rest-API-With-Flask/116910). Certain concepts that are mentioned are specific for Replit, like cycles and `pyproject.toml`.

---

Hello! I know I've been pretty inactive in Repl Talk (I've been doing [Github](https://github.com/BD103) and PyPI Packages), but I decided to make this tutorial.

# Making a Flask Rest API 🙃
Yes! I'm willing to bet most of the people viewing this has a Flask website, or at least knows Python. (_Woo, Python Gang Unite!_) Anyway...

This tutorial is mainly Python. I will split it up into many different parts and sections to increase effectiveness. Let's get started.

## 💾 Setup a Basic Flask Site 💽
First, we need to make a simple Flask site. Create a new Python repl and make the following file setup:

```
main.py
templates/
|- index.html
static/
|- style.css
```

Also insert the following into their respective files.

- `main.py`

```python
from flask import Flask, render_template

app = Flask("app")

@app.route("/")
def index():
	return render_template("index.html")

if __name__ == "__main__":
	app.run(host="0.0.0.0", port=8000)
```

- `templates/index.html`

```html
<!DOCTYPE html>

<html>
<head>
	<title>Rest API Server</title>
	<link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
</head>
	
<body>
	<div  class="center">
		<p>Welcome to this website's Rest API! Please access it at the <code>/api</code> endpoint. You can find the docs <a  href="/docs">here</a>.</p>
	</div>
</body>
</html>
```

- `style.css`

```css
body {
	/* You can replace the colors with your own :) */
	background: linear-gradient(to top left, darkblue, darkcyan);
	background-repeat: no-repeat;
	background-size: cover;
	background-attachment: fixed;
	color: white;
	font-family: "Segoe UI", Tohama, Geneva, Verdana, sans-serif;
	font-size: 20px;
}

.center {
	position: fixed;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
}
```

If you're lazy, you can also fork the repl linked below. :D

Now that we have some sample files, let's try running the repo!

![Success Image](https://user-images.githubusercontent.com/59022059/105514472-83767280-5ca1-11eb-8d4e-bde7229bf6b3.png)

Yay! We did it! Well, at least we created the first stepping stones to a great backend.

## 🔻 Error Handling 🔺 (E.g. 404, [418](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/418), 500...)

You'll notice that if you click the _docs_ button it will give you a 404 error. Let's fix that by first making an error handling system.

```python
from flask import ...
from werkzeug.exceptions import HTTPException

...

# Insert the following after the def index(): function
@app.errorhandler(Exception)
def error(e):
	# Set default error code in case something goes wrong
	code = 500
	if isinstance(e, HTTPException):
		code = e.code
	return render_template("error.html", e=str(e)), code
```

Also make a `error.html` page under templates and insert the following:

```html
<!DOCTYPE html>
<html>
<head>
	<title>Rest API Server - Error</title>
	<link rel="stylesheet" href="{{ url_for('static', filename='style.css' }}">
</head>

<body>
	<div class="center">
		<h3>AAAA! Something went (Horribly) Wrong!</h3>
		<code>{{ e }}</code>
	</div>
</body>
</html>
```

Quick (not really) thing on all those `{{ ... }}`. Basically, Flask uses Jinja2, a website formatter. It allows you to specify variables, and serve them specifically to the client. That's what the `render_template()` function does. A Flask specific example is `{{ url_for('static', filename='style.css') }}`. Flask has a function `url_for()`, so when it tries to get the variable, it runs the function. `url_for()` has two main parameters, folder and filename. The folder is the first specified variable, static. Remember that we created the static folder and it has `style.css` inside. The filename obviously specifies the file name. If you go to the actual website and view the `<link ...>` tag, you will see that is has `href="/static/style.css"`. Of course, this isn't necessary, you don't have to use `url_for()`, but Flask highly encourages it. So do it anyways.

This is all a bit different for the `<code>{{ e }}</code>`. `e` is a variable that we pass in the `render_template()` function. `e` is the content of the error that happened, so an example is _404 Not Found: The requested URL was not found on the server. If you entered the URL manually please check your spelling and try again._ That is what `e` gets set to when you go to a non-existant section of the site. (_Side Note: Watch out for all those pesky ~~birds~~ 500 errors. That means something is wrong with your code._)

Of course, after reading back this entire section, I never did explain how to create the actual docs for the API. That's probably because we haven't created the API yet, so we are going to put that on hold...

## 🔌 The Actual API (Woo Celebrate and Other Fun Words 🥳)

Ok. The API is going to be based after the `/api` endpoint, so an example is [rest-api-template.bd103.repl.co/api](https://rest-api-template.bd103.repl.co/api). Let's start writing the function.

```python
from flask import Flask, render_template, request

...

# Insert after def error(): function
@app.route("/api", methods=["GET", "POST"])
def api():
```

Ok. Let's stop for a second. In `@app.route(...)` I wrote the keyword argument `methods=["GET", "POST"]`. This is abolutely necessary, as it tell Flask to accept requests so using `curl ...`, `requests.get(...)`, and other methods will all works. Also make sure to update the `import` statement. Let's continue:

```python
...

@app.route("/api", methods=["GET", "POST"])
def api():
	data = request.args.get("data")

	if data is None:
		return {"type": "Error", "content": "No data requested"}
	elif data == "1":
		return {"type": "Data", "content": "Yay! Request successful!"}
	else:
		return {"type": "Error", "content": "Data specified does not exist"}
```

A few things:

1. `request.args.get("data")` gets the data from the requested url. For instance, if someone tried to go to `/api?data=0`, they would get the object saying _"Data specified does not exist"_. Instead, if they went to `/api?data=1` then they would get a successful request.
2. You always want to have an `if data is None`, for if the person accessing the url doesn't specify an argument. An example is if someone goes to `/api?name=something`. `data` would be equal to `None` because it doesn't exist and wasn't specified. 
3. I like to return all my data in an object (or JSON) based format. So I give a type, and I give content. I do this usually when I write an API that can return different types of data so that the requester knows what they are getting. You do not need to return data in this kind of format, but many other APIs work the same exact way.

There you go, you can get multiple arguments and return different items dependent.

### Sub-Subject: 🔗 URL Variables 🔗

Quick subject change in case you want to be more specific, you can create variable urls. For instance if you want to specify a specific type of data, e.g. Pizzas or People, you can do something like this:

```python
@app.route("/api/<type>")
def api(type):
	if type == "pizza":
		return "There are 10 pizzas being made in the pizzaria"
	elif type == "people":
		return "There are 3 people making the pizzas in the pizzaria"
	else:
		return "Type not available"
```

The variable name is specified with `<varname>`, and you have to make a parameter in the function. You can string multiple together, but it doesn't look as good if you make you API just that. Join URL variables and POST arguments to get an amazing website.

## 💻 Actual Applications 💻

In the replit, we are going to be saving and returning hit counts. For instance, how many times the website gets connected to a user. We are going to do this with simple variables, but they will get reset once the program stops. This is intentional, and you should probably change this.

> Challenge: Make an API where it saves the hit count as a JSON file, then accesses it so that your data gets saved!

```python
from flask import Flask, request, render_template
from werkzeug.exceptions import HTTPException

app = Flask("app")
hits = 0
errors = 0

@app.route("/")
def index():
	global hits
	hits += 1
	return render_template("index.html")

@app.errorhandler(Exception)
def error(e):
	global errors
	errors += 1
	code = 500
	if isinstance(e, HTTPException):
		code = e.code
	return render_template("errors.html", e=str(e)), code

@app.route("/api")
def api():
	global hits, errors
	hits += 1

	data = request.arg.get("data")
	
	if data is None:
		return {"type": "Error", "content": "No data requested"}
	elif data == "hits":
		return {"type": "HitCount", "content": hits}
	elif data == "errors":
		return {"type": "ErrorCount", "content": errors}
	else:
		return {"type": "Error", "content": "Data specified does not exist"}

if __name__ == "__main__":
	app.run(host="0.0.0.0", port=8000)
```

There we go. We have an application that counts how many times the site has been accessed, and also how many times an error has occurred, and returns that data. Congratulations! I give you guys a working Rest API! Feel free to fork this repl and edit it to your will. Share what you've done in the comments, too. I would like to see it!

## 📚 Making a Documentation 📚

By now, you guys are pros at this. Insert the following into `main.py`:

```python
...
# Maybe somewhere below index(): ?
@app.route("/docs")
def docs():
	global hits
	hits += 1
	return render_template("docs.html")

...
```

Create `docs.html` under the templates folder:

```html
<!DOCTYPE html>

<html>
<head>
	<title>Rest API Server - Docs</title>
	<link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
</head>
	
<body>
	<h1>Rest API Docs</h1>
	<p>Hi! This is a template, so you are going to have to fill this out yourself. Sorry :D</p>
</body>
</html>
```

Like it said, you're going to have to fill out the docs yourself. Sorry, but it is now your API. You know what it does, I probably don't. Also, do everyone a favor, and make the documentation **actually readable**. As much as I like Github, their docs are an absolutely confusing mess of programming jargon.

## Bonus Topic: ✨ Tokens ✨

Many APIs require authentication. Maybe there is data that we want to keep private, but still want to include in the API. An example is Github's API accessing personal information. You have to create a Personal Access Token, as send it in the header as part of the request. We are going to add a way to do this as well, though there are some drawbacks to this solution.

First, add `import pickle` at the top of the script.

```python
from flask import Flask, request, render_template
from werkzeug.exceptions import HTTPException
import pickle

...
```

Pickle is a binary handling system make specifically for Python. Common uses are saving variables and classes and objects. It can also save as readable(~~ish~~) text. Next let's create a pickle file. (I'll be using the console, I won't be writing this into any `.py` file. I recommend you do this too, though you can also make your own function.

```console
$ python
Python 3.8.7 (default, ...)
RaNdOm TeXt HeRe Ok FuN
>>> import pickle
>>> token = ["123456", "abcdef", "BD103WuzHere"]
>>> with open("tokens.pkl", "wb") as p:
... 	pickle.dump(token, p, -1)
...
>>> exit()
$ clear
```

Make sure to use correct indentation for the `pickle.dump(...)` line. The `$` represents a bash command, so something that you run in the command line. The `>>> ` represents a command that you run in the Python REPL. `... ` represents indented script, so the contents of a loop, function, etc. Also, running `clear` at the end isn't necessary, but I like cleaning up after myself. To make sure that this script worked, check to see if `tokens.pkl` is in your program files. You can also replace the values inside `token` to any password you want. I must say, though, **`.pkl` files are binary. Any normal computer will have trouble reading it, but Replit is weird and will render all the text in the file when viewed. This means that your passwords can be seen by anyone with the repl link. I recommend setting up an external server, like MongoDB, to store actual passwords if you want to do this professionally.**

Wow. With that out of the way, let's edit our main script:

```python
...

@app.route("/api", methods=["GET", "POST"])
def api():
	global hits, errors
	hits += 1
	
	data = request.args.get("data")
	token = request.args.get("token")

	with open("tokens.pkl", "rb") as t:
		if token is not None:
			if token in pickle.loads(t.read()):
				auth = True
			else:
				auth = False
		else:
			auth = False
	
	if data is None:
		return {"type": "Error", "content": "No data requested"}
	elif data == "hits":
		return {"type": "HitCount", "content": hits}
	elif data == "errors" and not auth:
		return {"type": "Error", "content": "Not authenticated"}, 401
	elif data == "errors" and auth:
		return {"type": "ErrorCount", "content": errors}
	else:
		return {"type": "Error", "content": "Data specified does not exist"}

if __name__ == "__main__":
	app.run(host="0.0.0.0", port=8000)
```

There you go. Now the program will read `tokens.pkl`, see if the specified token in the request (E.g. `/api?data=errors&token=BD103WuzHere`) is in the file. If so, it sets the variable `auth` to True. Then it detects if the request is authorized, and returns different data dependent.

## Final File Setup

Just in to confirm, this is the final directory setup you should have. (_You can also peek at the repl to see it too!_)

```
main.py
static/
|- style.css
templates/
|- index.html
|- error.html
|- docs.html
tokens.pkl

Some optional files:
README.md
pyproject.toml
poetry.lock
```

---

So, just like that it's over. I really hope you guys find this useful. Now, I try not to ask this a lot, but honestly. I poured my heart and soul and mind into this tutorial. Could you please upvote this? I don't want all this knowledge to go to waste, and I really appreciate it. Thank you, again, and I will see you around.

@BD103, Python Developer and Overall Great Guy (If I do say so myself 😁)