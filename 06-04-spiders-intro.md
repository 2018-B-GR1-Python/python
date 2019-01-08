# Spiders

`Python Class` -> what and how to crawl and extract data

`Items and processors` extract subset of logical information

`Item pipelines` modify and change data

## Implementing spiders

1. What to crawl
2. How to crawl
3. How to parse

`http://books.toscrape.com/`

## Start a project

```
$ scrapy startproject python_01
$ cd python_01
$ cd python_01
$ ls
$ cd spiders
```
### intro_spider_01.py

```python
import scrapy

nombre_archivo = 'book_titles.txt'

class IntroSpider(scrapy.Spider):  ## Hereda
  nombre = 'introduccion_spider'
  
  def start_requests(self): ## self = this en java
    urls = [
      'http://books.toscrape.com/catalogue/page-1.html',
      'http://books.toscrape.com/catalogue/page-2.html',
      'http://books.toscrape.com/catalogue/page-3.html',
      'http://books.toscrape.com/catalogue/page-4.html',
      'http://books.toscrape.com/catalogue/page-5.html',
    ]
    
    for url in urls:
      yield scrapy.Request(url=url, callback=self.parse)
    
  def parse(self,response):
    lista_libros = response.css('article.product_pod > h3 > a::attr(title)').extract()
    
    with open(nombre_archivo, 'a+') as f:
      for titulo_libro in lista_libros:
        f.write(titulo_libro + "\n")
  
```

Subir 2 directorios y correr el spider

```
$ cd ../..
$ scrapy crawl intro_spider_01
```



