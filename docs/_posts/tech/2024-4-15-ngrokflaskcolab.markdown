---
layout: post
title:  "Exposing Your Flask App to the World with Ngrok and Pyngrok in Google Colab"
date:   2024-4-15 06:25:17 -0800
categories: jekyll update technology
---

****
### Introduction
Google Colab provides an excellent environment for running Python code, including web applications built with Flask. However, sharing these applications with others or integrating them with external services can be challenging due to the limitations of Colab's runtime environment. In this blog post, we'll explore how to overcome this limitation by using Ngrok and Pyngrok to expose your local Flask app running in Google Colab to the internet.

### Prerequisites
Before we begin, ensure you have the following:

1. A Google Colab notebook.
2. Basic knowledge of Python and Flask.
3. An Ngrok account (sign up for free at [Ngrok](https://dashboard.ngrok.com/signup)).
4. Pyngrok library installed (install via `!pip install pyngrok`).

### Setting Up Ngrok in Google Colab
First, let's install Pyngrok in our Google Colab notebook. Run the following command:

```python
!pip install pyngrok > /dev/null
```

This command installs Pyngrok, a Python wrapper for Ngrok, which allows us to manage Ngrok directly from our Python code.

### Exposing Your Flask App
Next, let's write the Python code to start our Flask application and create a secure tunnel using Ngrok:

```python
import getpass
import threading
from flask import Flask
from pyngrok import ngrok, conf

# Prompt the user to enter their Ngrok authentication token
print("Use your authtoken, which can be copied from https://dashboard.ngrok.com/get-started/your-authtoken")
conf.get_default().auth_token = getpass.getpass()

# Create a Flask application
app = Flask(__name__)

# Define a simple route for our Flask app
@app.route("/")
def index():
    return "Hello World from Google Colab!"

# Start Ngrok tunnel and get the public URL
public_url = ngrok.connect(5000).public_url
print("Ngrok tunnel \"{}\"".format(public_url))

# Set the BASE_URL configuration for the Flask app
app.config["BASE_URL"] = public_url

# Start the Flask app in a separate thread
threading.Thread(target=app.run, kwargs={"use_reloader": False}).start()
```

Let's go through the code:

- We import necessary libraries: `getpass` for securely inputting the Ngrok authentication token, `threading` for running Flask in a separate thread, `Flask` for creating our web application, and `pyngrok` for managing Ngrok from Python.
- We prompt the user to input their Ngrok authentication token, which is required to create the tunnel.
- We create a Flask application and define a simple route that returns "Hello World".
- We connect to Ngrok, specifying the port on which our Flask app is running (in this case, port 5000). Ngrok then assigns a public URL to our local server.
- We set the `BASE_URL` configuration variable for our Flask app to the public URL provided by Ngrok.
- Finally, we start the Flask app in a separate thread to avoid blocking the notebook execution.

### Conclusion
In conclusion, by utilizing Ngrok and Pyngrok within Google Colab, you can effortlessly expose your local Flask application to the internet. This enables easy sharing of your work with others or integration with external services without the need for complex deployment setups. 