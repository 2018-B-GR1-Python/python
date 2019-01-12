# Input Processors

`scrapy shell`

```
$ scrapy startproject python_04
$ cd python_04/python_04/spiders
```

## items.py

```python
import scrapy
from scrapy.loader.processors import MapCompose
# Apply a sequence of functions to any list

def shorten_amazon_link(link):
  id_producto = link.split('/')[-1]  # ultimo elemento
  short_link = 'https://www.amazon.com/dp/' + id_producto
  return short_link

class ItemProducto(scrapy.Item):
  titulo = scrapy.Field()
  precio = scrapy.Field()
  link = scrapy.Field(
     input_processor = MapCompose(shorten_amazon_link)
  )
  
```

## input_processor.py

```
import scrapy
from scrapy.loader import ItemLoader
from scrapy.loader.processors import MapCompose
from scrapy.loader.processors import TakeFirst
from python_04.items import ItemProducto


def truncar_texto(texto):
  return texto[:50]

class DetallesProducto(scrapy.Spider):
  name = 'input_processor'
  
  urls = ['https://www.amazon.com/s/ref=nb_sb_noss_2?url=search-alias%3Daps&field-keywords=macbook']
  
  def parse_page(self, response):
    resultados_busqueda = response.css('ul.s-result-list > li')
    
    for producto in resultados_busqueda:
    
      producto_loader = ItemLoader(item=ProductItem(), selector=producto)
      
      # producto_loader.default_input_processor = MapCompose(truncar_texto)
      # producto_loader.default_output_processor = TakeFirst()
      
      producto_loader.add_css('titulo','.s-access-title::text').extract_first()
      producto_loader.add_css('precio','.s-price::text').extract_first()
      producto_loader.add_css('link','a.s-access-detail-page::attr(href)').extract_first()
      
      yield producto_loader.load_item()  # Es un return q no para el loop
```

Cada producto extraido con esta funcion en titulo, precio y link trae una lista
