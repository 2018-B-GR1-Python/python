# Follow links

```
$ scrapy startproject python_02
$ cd python_02/python_02/spiders
```

## follow_links_onu_02.py

```python
import scrapy
from scrapy.spiders import CrawlSpider, Rule
from scrapy.linkextractors import LinkExtractor

class GenSpiderCrawl(CrawlSpider):
  name = 'crawl_onu'
  
  allowed_domains = ['un.org']
  
  start_urls = ['http://www.un.org/en/sections/about-un/funds-programmes-specialized-agencies-and-others/index.html']
  
  rules = (Rule(LinkExtractor(), callback='parse_page')
  
  def parse_page(self, response):
    lista_de_agencias = response.css('div.field-item.even > h4::text').extract()
    for agencia in lista_de_agencias:
      with open('onu_agencias.txt', 'a+') as f:
        f.write(agencia + '\n')
  
```

start

```
$ scrapy startproject python_02
```
