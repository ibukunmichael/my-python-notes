# **Python Application Development Using Zappa** #
 <!--images-->
![Getting Started](zappa1.jpg)

**Zappa** makes it super easy to build and deploy server-less, event-driven Python applications (including, but not limited to, WSGI web apps) on AWS Lambda + API Gateway. Think of it as "serverless" web hosting for your Python apps. That means infinite scaling, zero downtime, zero maintenance - and at a fraction of the cost of your current deployments!

If you've got a Python web app (including Django and Flask apps), it's as easy as:
```
$ pip install zappa
$ zappa init
$ zappa deploy
```
and now you're server-less!

With a traditional HTTP server, the server is online 24/7, processing requests one by one as they come in. If the queue of incoming requests grows too large, some requests will time out. With Zappa, each request is given its own virtual HTTP "server" by Amazon API Gateway. AWS handles the horizontal scaling automatically, so no requests ever time out. Each request then calls your application from a memory cache in AWS Lambda and returns the response via Python's WSGI interface. After your app returns, the "server" dies.

It's great for deploying serverless microservices with frameworks like Flask and Bottle, and for hosting larger web apps and CMSes with Django. Or, you can use any WSGI-compatible app you like. 
Zappa also lets you build hybrid event-driven applications that can scale to trillions of events a year with no additional effort on your part! You also get free SSL certificates, global app deployment, API access management, automatic security policy generation, precompiled C-extensions, auto keep-warms, oversized Lambda packages, and many other exclusive features.

### **Installation and Configuration** ###
Zappa can easily be installed through pip, i.e.
```
$ pip install zappa
```
**Running the Initial Setup / Settings**
Zappa can automatically set up your deployment settings for you with the init command:
```
$ zappa init
```
This will automatically detect your application type (Flask/Django ) and help you define your deployment configuration settings. Once you finish initialization, you'll have a file named zappa_settings.json in your project directory defining your basic deployment settings. 
Now, you're ready to deploy!

**Initial Deployments**
Once your settings are configured, you can package and deploy your application to a stage called "production" with a single command:
```
$ zappa deploy production
```
And now your app is live.

To explain what's going on, when you call deploy, Zappa will automatically package up your application and local virtual environment into a Lambda-compatible archive, replace any dependencies with versions precompiled for Lambda, set up the function handler and necessary WSGI Middleware, upload the archive to S3, create and manage the necessary Amazon IAM policies and roles, register it as a new Lambda function, create a new API Gateway resource, create WSGI-compatible routes for it, link it to the new Lambda function, and finally delete the archive from your S3 bucket. 

Be aware that the default IAM role and policy created for executing Lambda applies a liberal set of permissions. These are most likely not appropriate for production deployment of important applications. 
 Zappa goes quite far beyond what Lambda and API Gateway were ever intended to handle. 



