# Web Scraping with Python

## Tools you can use for web scraping

Requests library

Beautiful Soup

Scrapy - used for web crawling websites

Selenium - Automated bot&#x20;



## Why Scrap the web?

The web is filled with profitable data

For data trapped in web pages, scraping is the only option.



## Human vs Web Scrapers

<table><thead><tr><th>Human</th><th>Web Scraper</th><th data-hidden></th></tr></thead><tbody><tr><td>Enters a url or clicks a bookmark</td><td>Set a start_url</td><td></td></tr><tr><td>Download HTML</td><td>Download HTML</td><td></td></tr><tr><td>Parse HTML &#x26; render</td><td>Parse HTML</td><td></td></tr><tr><td>Review for useful information</td><td>Extract useful information</td><td></td></tr><tr><td>Interpret</td><td>Transform or Aggregate</td><td></td></tr><tr><td>Remember the information</td><td>Save the data</td><td></td></tr><tr><td>Click a link-Enter another URL</td><td>Go to the next URL</td><td></td></tr></tbody></table>

## URL Hacking

```
https://
www.website.com:443
/path
query_string
```

URL Fragments

```
# Location
```

```
& query strings
```

The '#' is the main filter set

The '&' is the searched query string



```
start_url = f'http://{host}{path}{query_string}'
```
