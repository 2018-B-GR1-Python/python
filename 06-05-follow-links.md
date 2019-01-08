# Follow links

```
$ scrapy startproject python_02
$ cd python_02/python_02/spiders
```

## follow_links_02.py

```
import scrapy
from scrapy.spiders import CrawlSpider, Rule
from scrapy.linkextractors import LinkExtractor

class GenSpiderCrawl(CrawlSpider):
  name = 'crawl_onu'
  
  allowed_domains = ['un.org']
  
  start_urls = ['http://www.un.org/en/sections/about-un/funds-programmes-specialized-agencies-and-others/index.html']
  
  

```
