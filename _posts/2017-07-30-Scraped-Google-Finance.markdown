---
layout: post
title:  "Scraping with python"
date:   2017-07-30 18:30:00 +0300
categories: web scraping, python
---
In this post I want show how to load a website using ["requests"][requests-docs] library and parse the loaded page through ["BeautifulSoup"][BeautifulSoup-docs] then I will find an element from the webpage in order to extract some specific information.

these are the libraries I imported in my project file.
{% highlight python %}
import requests
from bs4 import BeautifulSoup
{% endhighlight %}

url is a string variable which holds the address of the webpage. response, stores what the server sends back after we use the function get from requests library. With looking at the status_code associated my query I can find out whether or not my query has been successful.
{% highlight python %}
url = "https://www.google.com/finance"
response = requests.get(url)
if not response.status_code == 200:
 print("Website is unreachable")
{% endhighlight %}

Now BeautifulSoup comes into play; what response_page stores is a treeview of the website. Arguments given to the BeautifulSoup constructor are content of the webpage and an optional formatting keyword which in here is 'lxml'.
{% highlight python %}
response_page = BeautifulSoup(response.content, 'lxml')
{% endhighlight %}


[requests-docs]: https://pypi.python.org/pypi/requests
[BeautifulSoup-docs]: https://www.crummy.com/software/BeautifulSoup/bs4/doc/
