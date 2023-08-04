Caching is an important concept to understand for every Python programmer and data scientist. The concept of caching revolves around improving the performance of the application by holding the data in memory to avoid the slow retrieval of data from its source. It gives our applications a performance boost
In a nutshell, the concept of caching revolves around utilising programming techniques to store data in a temporary location instead of retrieving it from the source each time.

Subsequently, caching can provide an application performance boost as it is faster to access data from the temporary location than it is to fetch the data from the source each time, such as from database, web service, etc.

There are many ways to achieve fast and responsive applications. Caching is one approach that, when used correctly, makes things much faster while decreasing the load on computing resources. Python’s functools module comes with the @lru_cache decorator, which gives you the ability to cache the result of your functions using the Least Recently Used (LRU) strategy. This is a simple yet powerful technique that you can use to leverage the power of caching in your code.

Caching and Its Uses
Caching is an optimization technique that you can use in your applications to keep recent or often-used data in memory locations that are faster or computationally cheaper to access than their source.

Imagine you’re building a newsreader application that fetches the latest news from different sources. As the user navigates through the list, your application downloads the articles and displays them on the screen.

What would happen if the user decided to move repeatedly back and forth between a couple of news articles? Unless you were caching the data, your application would have to fetch the same content every time! That would make your user’s system sluggish and put extra pressure on the server hosting the articles.

A better approach would be to store the content locally after fetching each article. Then, the next time the user decided to open an article, your application could open the content from a locally stored copy instead of going back to the source. In computer science, this technique is called caching.

Implementing a Cache Using a Python Dictionary
You can implement a caching solution in Python using a dictionary.

Staying with the newsreader example, instead of going directly to the server every time you need to download an article, you can check whether you have the content in your cache and go back to the server only if you don’t. You can use the article’s URL as the key and its content as the value.


import requests

cache = dict()

def get_article_from_server(url):
    print("Fetching article from server...")
    response = requests.get(url)
    return response.text

def get_article(url):
    print("Getting article...")
    if url not in cache:
        cache[url] = get_article_from_server(url)

    return cache[url]

get_article("https://realpython.com/sorting-algorithms-python/")
get_article("https://realpython.com/sorting-algorithms-python/")
