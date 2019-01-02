---
layout: post
title:  "Node.js explained for mannequins"
date:   2018-01-02 20:38:20
---

![](https://static.webpunks.co/uploads/2016/08/nodejs-modules-webentwicklung-webdevelopment-webpunks.jpg)
## Introduction


Node.js or node is an open source and cross-platform runtime environment for executing javascript code outside of a browser. 

Quite often, we use node to build back-end services also called API (Application Programming Interface), these are the services that power client applications like the web app running inside of a web browser, or a mobile app running on a mobile device, these client apps are simply what the user sees and interacts with.
The apps themselves are  just the surface, they need to talk to some sort of service sitting on a server or in the cloud to store data, send emails or push notifications, and much more

> Node.JS is ideal for building Highly scalable, data-intensive and real-time back-end services that power client applications.
 
 Well you might be thinking, but there are other back-end services or frameworks such as ASP.NET, Rails, etc, so what's so special abouT node?
- Great for prototyping and agile development
- Superfast and highly scalable
 - Javascript Everywhere (Cleaner and more consistent codebase)
- The Largest ecosystem of open-source libraries.

##  Node Architecture
Before node.js we used javascript to build applications that ran only inside a browser, every browser has a javascript engine that takes our javascript code and converts it to machine code (code computer can understand ).
Microsoft uses chakra, firefox uses spider monkey and chrome uses V8, because of this variety of engines js can behave differently in different browsers.
> A browser provides a runtime environment for javascript code, up to 2009 the only way to execute js was in a browser in 2009 Ryan dahl the creator of Node.js came up with a brilliant idea he thought it would be great to execute js out of a browser so he took chrome’s v8 engine and embedded it inside a c++ program and  called that program Node.exe so similar to a browser node is a runtime environment for js code …. 

I know what you're thinking why did Ryan create a runtime environment out of the browser, couldn't he use the browser offline? … 
why must this be complicated ?
Now, we will look a bit more into that.

Node has certain objects that provide an environment for our js code, these objects are different from the environmental objects we have in browsers, for example in browsers we have the window or the document object `document.getElementById('')` which allows us to work with the environment which our code is running (the browser). 
but with Node js, we don't have the document or window object. one very important thing to note was that initially when js was created it was created to run in browsers so it had no access to things like the file system ( for security purposes ) so now with node it gives us more interesting capabilities we can work with the file system `fs.readFile()` listen for requests `http.createServer()` and so much more which we can't do inside of a browser
so we can see that both chrome and node use the V8 engine but they provide different runtime environments for Javascript. 

#####   Node is not a programming language!
#####    Node is not a framework!

##  How does    Node work
I had mentioned earlier that Node applications are highly scalable, well that is because of the non-blocking/Asynchronous nature of node 

####   What is Asynchronous/ non-blocking? 
Let me try to explain with a metaphor, imagine you go to a restaurant and, the waiter comes to customer A’s table takes the order for customer A and goes to the kitchen, drops the order for the chef to prepare the meal so while the chef is preparing the meal he comes back to take customer B’s order drops the order in the kitchen and that way the same waiter can be used to serve many different tables so they don't have to wait for the chef to finish Customer A’s food before they are served … This is what we call Asynchronous or non-blocking architecture.

####   Synchronous / Blocking Architecture 
Back to our restaurant example, imagine you go to a restaurant and in this restaurant the waiter takes your order goes to the kitchen and waits there for the chef to prepare your meal and while the chef is preparing your meal, the waiter is not doing anything then when the meal is ready the waiter serves you and proceed to the next table. 
This is what we call blocking or Synchronous architecture and that is how applications like ASP.net or Rails work out of the box.

So when we receive a request a thread is assigned to handle that request, it is likely we will query a database and sometimes it might take a little while until the result is ready, so while the result is processing that thread is sitting idle doing nothing so we need a new thread to process requests for another client, so what would happen if we had a large number of concurrent clients, at some point we will run out of threads to serve the clients, so new clients have to wait and if we don't want them to wait we need to add more hardware. With this kind of architecture we are not utilizing resources efficiently and that is the problem with synchronous architecture and that's how back-end frameworks like rails or asp.net work by default. off-course its possible to make asp.net asynchronous but that would require extra work node.js comes asynchronous out of the box. 

So in Node we have a single thread handling multiple requests, if it is querying a DB it doesn't have to wait for the DB to return results. when the DB returns the results it puts it in something called an event queue, node is continuously monitoring this queue in the background, when there's an event it will take it out and process it, this makes node ideal for I/O-intensive apps, Node should not be used for CPU intensive apps like video encoding or image manipulation in these apps we have a lot of calculation to be done by the CPU and few that touch the file system. 


##  In conclusion 
> Javascript itself is a single-threaded, non-blocking, asynchronous, concurrent language, it has a callback, an event loop, a callback queue, and some other API's and stuff 

node is a runtime environment for js, javascript itself has some inbuilt functions for codes to be non-blocking (the definition for blocking is relative but we all agree that blocking is slow code ) and a common example is the set timeout. 

Also node.js also has some applications on the front-end if you're curious. 
You can let me know if you would like an advanced article expatiating more on node.js or applications of Node in the front-end, or writing a simple back-end node server, you can reach me [here](https://twitter.com/nottherealilest) …Remember this blog is for all things Javascript.  
