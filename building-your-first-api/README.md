<h1>
  <span class="headline">Intro to FastAPI</span>
  <span class="subhead">Building Your First API</span>
</h1>

**Learning objective**: By the end of this lesson, you will be able to **implement** a basic FastAPI application with a 'hello world' route.

## Create an entry-point module

First let's create a `main.py` file in the root directory:

```bash
touch main.py
```

## Import the FastAPI dependency

First import the FastAPI class from the `fastapi` module:

```py
# main.py

from fastapi import FastAPI
```

## Initialize the API application

Next we create an instance of the FastAPI class:

```py
# main.py

app = FastAPI()
```

## Defining the 'hello world' Route

Next we will define a root endpoint that responds to `GET` requests:

```py
# main.py

@app.get('/')
def home():
    return 'Hello World!!!!'
```

## The complete `hello world` app

Your final code will look like this:

```py
# main.py

from fastapi import FastAPI

app = FastAPI()


@app.get('/')
def home():
    return 'Hello World!!!!'
```

## Starting the API Server

Launch the server with the following command in your terminal:

```sh
pipenv run uvicorn main:app
```

<img src="./assets/uvicorn-logo.png" alt="uvicorn-logo" style="width:250px;"/>

[Uvicorn](https://www.uvicorn.org/) is a web server that sits between your FastAPI application and the client that's using the API. You can think of it as a translator between FastAPI and the outside world.

You should see something similar to the following terminal output:

```txt
INFO:     Started server process [5503]
INFO:     Waiting for application startup.
INFO:     Application startup complete.
INFO:     Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
```

Open a web browser and navigate to [http://127.0.0.1:8000](http://127.0.0.1:8000). You should see your `Hello World!` message.

## Development Mode

When you open your browser, you should see the `"Hello World!"` message. But what happens if you go back to `main.py`, change the response message, and refresh the browser? You’ll still see the original `"Hello World!"` message.

Why? The server doesn’t automatically update to reflect changes in your code. To see updates, you have to stop the server and restart it, which can get tiring when you're making lots of changes.

Luckily, FastAPI can handle this for you. The tool we’re using to run FastAPI, called `uvicorn`, has a feature to automatically restart the server whenever you change your code.

To use this feature:

1. Stop the server by pressing **Ctrl+C**.
2. Restart it with this command, adding the `--reload` flag:

```sh
pipenv run uvicorn main:app --reload
```

Change the text in the `return` function of the `main.py` file to look like this:

```py
return 'Welcome to my API'
```

Save the file and refresh your browser. You should see the updates dynamically reflected.

Once you're done, type `CTRL+C` to shut down the webserver.
