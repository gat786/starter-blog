---
title: How to take your software online?
date: 2021-03-19T06:03:58.647Z
image: /images/poster.png
draft: true
---
We as developers write code and want it to be readable by everyone and if possible it should be available for everyone to use it. But it happens many times that we don't know how to make it public and usable across our different apps. 

Suppose if you wrote a python code which converts a given string to a poetry, suppose you had a NodeJS program written which backs up your file to your favorite cloud, suppose you had an incredibly special and proprietary Random Number Generator code how would you put it on cloud? How would you use it across multiple apps? How would use the same code in different environment?

Well one solution to all of this is you create a Web API and enclose your software in it and make it run on any of your favorite cloud provider. Now the question arises what is a Web API?

Now Web API's can be complicated to a person who is beginning to learn about computers and distributed devices but the idea behind it is quite simple.  You have some piece of code that you want to use it on multiple end applications \[namely mobile apps, web apps, admin panel's], and you don't want it to be directly embedded inside those end applications. You can do it with Web API's. These are nothing but some way through which computers can contact each other and ask each other to do various tasks when user at the client end wants to do something.

Let's take an example, when you login to your Facebook, Instagram or Google Account what happens is your mobile app is contacting their servers and telling them **"Bro, there's this guy *Gat786* having a secret** ★★★★★ **and wants to use data which is related to him".** It typically happens over the internet and uses [HTTP request response protocol](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Technical_overview). You can read about it in detail to know more about it. 

While this is a huge and complicated example on how things are done. What you typically want to do is similar. You have some piece of code, let's say some function which accepts some input let's say i.e. a string and returns a result. Now you want to put make it available to everyone. The easiest way to do that is REST API's. 

REST stands for *REpresentational State Transfer.* Which says that it is used to transfer state data which you can represent in front of user.