# **Python Application Development Using Requests** #
 <!--images-->
![Getting Started](req1.png)

Requests is a popular apache2 licensed module in Python that can be used to interact with HTTP servers such as world wide web servers to download content that can be used for parsing websites or automatically posting to web forms. You can make a GET request, a POST request, passing parameters in URLs, get response content and addition of custom headers.

Requests will allow you to send HTTP/1.1 requests using Python. It is an easy-to-use library with a lot of features ranging from passing parameters in URLs to sending custom headers and SSL Verification. With it, you can add content like headers, form data, multipart files, and parameters via simple Python libraries. It also allows you to access the response data of Python in the same way.
You can use Requests with Python version 2.6–2.7 and 3.3–3.6, you should know that Requests is an external module, so you will have to install it. 

#### **To install requests using pip:** ####
```
pip install requests
```
## **Making a GET Request** ##
It is very easy to send an HTTP request using Requests. You begin by importing the module and then make the request. Here is an example:
```python
import requests
req = requests.get('https://google.com/')
```

All the information about our request is now stored in a Response object called req. For example, you can get the encoding of the webpage using the req.encoding property. You can also get the status code of the request using the req.status_code property.
```python
req.encoding     # returns ISO-8859-1
req.status_code  # returns 200
```
You can access the cookies that the server sent back using req.cookies. Similarly, you can get the response headers using req.headers. The req.headers property returns a case insensitive dictionary of response headers. This means that ```req.headers['Content-Length']```, ```req.headers['content-length']``` and ```req.headers['CONTENT-LENGTH']``` will all return the value of the 'Content-Length' response header.

The requests module can also be used in getting files from the internet. For example, the python script below will download the Google icon and save it to the same folder containing the script.
```python
import requests
url = 'http://google.com/favicon.ico'
r = requests.get(url, allow_redirects=True)
open('google.ico', 'wb').write(r.content)
```
## **Making a POST Request** ##
Making a POST request is just as easy as making GET requests. You just use the post() function instead of get(). This can be useful when you are automatically submitting forms. For example, the following code will download the whole Wikipedia page on Nanotechnology and save it on your PC.

```python
import requests
req = requests.post('https://en.wikipedia.org/w/index.php', data = {'search':'Nanotechnology'})
req.raise_for_status()
with open('Nanotechnology.html', 'wb') as fd:
    for chunk in req.iter_content(chunk_size=50000):
        fd.write(chunk)
```


## **Errors and Exceptions** ##
There are a number of exceptions and error codes you need to be familiar with when using the Requests library in Python.
- If there is a network problem like a DNS failure, or refused connection the Requests library will raise a ConnectionError exception.
- With invalid HTTP responses, Requests will also raise an HTTPError exception, but these are rare. 
- If a request times out, a Timeout exception will be raised.
- If and when a request exceeds the preconfigured number of maximum redirections, then a TooManyRedirects exception will be raised.
Any exceptions that Requests raises will be inherited from the requests.exceptions.RequestException object.
