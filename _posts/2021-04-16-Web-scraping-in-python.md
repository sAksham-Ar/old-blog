---
layout: post
title:  "Web scraping in Python"
category: Python
---

Today we are going to learn how to scrape a website in python. We will be scraping google to find results and store them as JSON.

## Requirements

For web scraping we would require two libraries: 

1. requests
2. bs4

Just install them with pip as:

{% capture code %}
pip3 install requests bs4
{% endcapture %}
{% include code.html code=code lang="bash" %}

## Starting

first we would need to import the required libraries:

{% capture code %}
import requests
from bs4 import BeautifulSoup
import json
{% endcapture %}
{% include code.html code=code lang="python" %}

Suppose we search "foo bar" in google the URL looks like this:

https://www.google.com/search?q=foo+bar 

This means that if we want to search a custom search query we just replace all the spaces with + and add it to the end of https://www.google.com/search?q=.

In python this would look like:

{% capture code %}
BaseUrl="https://www.google.com/search?q="
SearchTerm="foo+bar"
Url=BaseUrl+SearchTerm
{% endcapture %}
{% include code.html code=code lang="python" %}

We will use requests to get HTML from this link which looks like:

{% capture code %}
r=requests.get(Url)
{% endcapture %}
{% include code.html code=code lang="python" %}

```r.content``` will contain the HTML code.

## Searching HTML through BeautifulSoup

We first need to find out which class a single search result belong to, which we can do by clicking inspect element on a result.

![output](/assets/web-scraping-in-python-1.png)

from this photo we can see that the title of the search is in a "h3".So we just need to find all the "h3"  elements. Using BeautifulSoup we can do that as:
{% capture code %}
soup=BeautifulSoup(r.content,"html.parser")
titles=soup.find_all("h3")
titles=titles[:-1]
{% endcapture %}
{% include code.html code=code lang="python" %}
The last element is related searches so i truncated it. As we can see from the screen shot the links are just the prvious a tag to h3 so ew can get the links by:
{% capture code %}
links=[]
for title in titles:
    links.append(title.find_previous("a"))
{% endcapture %}
{% include code.html code=code lang="python" %}

## Storing it as JSON
We can store the information in a python list of dictionaries and output it as JSON. We will get the text from "h3" and the "href" from "a" element.
{% capture code %}
ResultsList=[]
ResultDict={}
for title,link in zip(titles,links):
	ResultDict={}
	# skipping google search results
​	if link["href"][7:22]=="/www.google.com":
​		continue
​	ResultDict["title"]=title.text
	# getting the actual URL from "href"
​	ResultDict["link"]=link["href"][7:].split("&")[0]
​	ResultsList.append(ResultDict)
print(json.dumps(ResultsList,indent=4))
{% endcapture %}
{% include code.html code=code lang="python" %}
The output looks like:
![output](/assets/web-scraping-in-python-2.png)

## Entire Code
{% capture code %}
import requests
from bs4 import BeautifulSoup
import json

BaseUrl="https://www.google.com/search?q="
SearchTerm="foo+bar"
Url=BaseUrl+SearchTerm
r=requests.get(Url)

soup=BeautifulSoup(r.content,"html.parser")
titles=soup.find_all("h3")
titles=titles[:-1]

links=[]
for title in titles:
    links.append(title.find_previous("a"))

ResultsList=[]
ResultDict={}
for title,link in zip(titles,links):
	ResultDict={}
	# skipping google search results
​	if link["href"][7:22]=="/www.google.com":
​		continue
​	ResultDict["title"]=title.text
	# getting the actual URL from "href"
​	ResultDict["link"]=link["href"][7:].split("&")[0]
​	ResultsList.append(ResultDict)
print(json.dumps(ResultsList,indent=4))
{% endcapture %}
{% include code.html code=code lang="python" %}

## Conclusion
You can take this one step further by taking the search term as an input from the user. I have only show you a small part of what Beautiful Soup can do, for more information go [here](https://beautiful-soup-4.readthedocs.io/en/latest/). Have fun experimenting with this!
