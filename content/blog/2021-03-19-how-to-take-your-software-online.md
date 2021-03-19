---
title: How to take your software online?
date: 2021-03-19T06:03:58.647Z
image: /images/poster.png
tags:
  - Python
  - Azure
  - WebServices
  - AppService
  - FastAPI
draft: false
---


We as developers write code and want it to be readable by everyone and if possible it should be available for everyone to use it. But it happens many times that we don't know how to make it public and usable across our different apps. 

Suppose if you wrote a python code which converts a given string to a poetry, suppose you had a NodeJS program written which backs up your file to your favorite cloud, suppose you had an incredibly special and proprietary Random Number Generator code how would you put it on cloud? How would you use it across multiple apps? How would use the same code in different environment?

Well one solution to all of this is you create a Web API and enclose your software in it and make it run on any of your favorite cloud provider. Now the question arises what is a Web API?

Now Web API's can be complicated to a person who is beginning to learn about computers and distributed devices but the idea behind it is quite simple. You have some piece of code that you want to use it on multiple end applications \[namely mobile apps, web apps, admin panel's], and you don't want it to be directly embedded inside those end applications. You can do it with Web API's. These are nothing but some way through which computers can contact each other and ask each other to do various tasks when user at the client end wants to do something. These paths can also be called as endpoints.

Let's take an example, when you login to your Facebook, Instagram or Google Account what happens is your mobile app is contacting their servers and telling them **"Bro, there's this guy *Gat786* having a secret** ★★★★★ **and wants to use data which is related to him".** It typically happens over the internet and uses [HTTP request response protocol](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Technical_overview). You can read about it in detail to know more about it. 

While this is a huge and complicated example on how things are done. What you typically want to do is similar. You have some piece of code, let's say some function which accepts some input let's say i.e. a string and returns a result. Now you want to put make it available to everyone. The easiest way to do that is REST API's. 

REST stands for *REpresentational State Transfer.* Which says that it is used to transfer state data which you can represent in front of user. Now REST uses HTTP protocol underneath what it means for you is you request for something by providing a path and the provide data related to that request. Server accepts that request checks whether everything is all right and then replies with a response if it finds one. 

To understand about REST Services more in a detailed way you should watch this [video](https://www.youtube.com/watch?v=SLwpqD8n3d0&ab_channel=ProgrammingwithMosh).

Now for our blog let's take an example of a Python Function which accepts a request and returns a random quote every time. 

```python
import json
import random

def get_random_quote():
    with open("./quotes.json","r",encoding='utf-8') as quotes_file:
        quotes = json.loads("".join(quotes_file.readlines()))
        length_of_array = random.randint(0,len(quotes))
        return quotes[length_of_array]

```

This will read a file named `quotes.json` and return a random quote from the file when it finds one. I found that file on [kaggle](https://www.kaggle.com/akmittal/quotes-dataset?select=quotes.json). 

Now let's try to make an API around this function.

It would be better if you have watched the video which is suggested to get more idea about how it works but I will explain over here in a bit. 

How it works in REST is you send in distinct types of HTTP requests to do different tasks.

For E.g. 

If you want to fetch some data you will send a GET request, if you want to delete some data you will send a DELETE request. If you want to create some new resource, you will send in POST request and same goes for updating you will send in a UPDATE request. For more information on this go [here](https://www.w3schools.com/tags/ref_httpmethods.asp). 

For this scenario you get an idea where I am trying to get at. For this scenario we can use a GET request to make this function available as an endpoint.

Now for this we will use a python library called [FastAPI](https://fastapi.tiangolo.com/). For making stuff with FastAPI you will need uvicorn installed as well. You can install both like this - 

```shell
pip install fastapi uvicorn[standard]
```

With FastAPI creating a Rest Endpoint is as simple as creating a file `main.py` and writing the following code in it.

```
from typing import Optional

from fastapi import FastAPI

app = FastAPI()


@app.get("/")
def read_root():
    return {"Hello": "World"}
    
```

You can run this app with the command `uvicorn main:app --reload ` 

Once you have the app running hit the endpoint `localhost:8000 ` and you will get a message of `{"Hello": "World"} .`

We must create a new function with path quote which will return our random quote to make our first API. It can be done like this.

```python
from typing import Optional
import quotes_function
from fastapi import FastAPI

app = FastAPI()


@app.get("/")
def read_root():
    return {"Hello": "World"}
    
@app.get("/quotes"):
def get_quote():
    return quotes_function.get_random_quote()
```

 After adding this function now when you hit the endpoint `localhost:8000/quotes` you will see that it returns our random quotes. Now we can deploy it to some cloud provider, and we will be able to use it in our mobile apps, desktop apps or any other app we can imagine. 

Real world scenarios are much more complicated than this, but this is a beginning and all the REST Apis are built on these concepts. 

You can use Azure App Service for deploying this with ease, but every Cloud Provider has one or the other way with which you can deploy this and make it available across the globe.

I will in future write about how you can deploy this but for now this is it for this write-up. See you next time around. 

Follow me on various platforms to get connected. Bye 👋👋