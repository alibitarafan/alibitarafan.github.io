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

Now BeautifulSoup comes into play. What response_page stores is a tree structure of the website's elements. Arguments given to the BeautifulSoup constructor are contents which function get received and one optional formatting keyword which in here is 'lxml'.
{% highlight python %}
response_page = BeautifulSoup(response.content, 'lxml')
{% endhighlight %}

BeautifulSoup offers many functionalities, searching and navigating can be done using provided functions which can be viewed in [here][navigating-tree], however I will use the [find][find-method] method for this project.
the right side of this assignment operation will search for a css class called "id-secperf sfe-section-major" in a html element tagged div from the BeautifulSoup tree in response_page.
{% highlight python %}
sectors_table = response_page.find("div", class_ = "id-secperf sfe-section-major")
{% endhighlight %}


[requests-docs]: https://pypi.python.org/pypi/requests
[BeautifulSoup-docs]: https://www.crummy.com/software/BeautifulSoup/bs4/doc/
[navigating-tree]: https://www.crummy.com/software/BeautifulSoup/bs4/doc/#navigating-the-tree
[find-method]: https://www.crummy.com/software/BeautifulSoup/bs4/doc/#find
