# Pipelines

```
$ scrapy startproject python_05
$ cd python_05/python_05/spiders
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

## pipelines.py

```python
import scrapy
from scrapy.loader import ItemLoader
from scrapy.loader.processors import MapCompose
from scrapy.loader.processors import TakeFirst
from python_05.items import ItemProducto

def pipelines(texto):
  return texto[:50]

class DetallesProducto(scrapy.Spider):
  name = 'input_processor'
  
  urls = ['https://www.amazon.com/s/ref=nb_sb_noss_2?url=search-alias%3Daps&field-keywords=macbook']
  
  def parse_page(self, response):
    resultados_busqueda = response.css('ul.s-result-list > li')
    
    for producto in resultados_busqueda:
    
      producto_loader = ItemLoader(item=ProductItem(), selector=producto)
      
      producto_loader.default_input_processor = MapCompose(truncar_texto)
      producto_loader.default_output_processor = TakeFirst()
      
      producto_loader.add_css('titulo','.s-access-title::text').extract_first()
      producto_loader.add_css('precio','.s-price::text').extract_first()
      producto_loader.add_css('link','a.s-access-detail-page::attr(href)').extract_first()
      
      yield producto_loader.load_item()  # Es un return q no para el loop

```


## pipelines.py

```python
class ValidarMacbook(objeto):
  def process_item(self, item, spider):
    
    if('macbook' not in item['titulo'].lower() or float(item['precio']) < 200.0):
      item['titulo'] = 'No-Macbook'
    
    return item
    
    
class ValidarPrecio(object):
  def process_item(self, item, spider):
    if(float(item['precio']) > 1200.0):
      item['precio'] = 'Inasequible'
    
    return item

class MarkarComoViable(object):
  def process_item(self, item, spider):
    if item['titulo'] != 'No-Macbook' and item['precio'] != 'Inasequible':
      print("\n \nItem encontrado")
      print("Titulo", item['titulo'])
      print("Precio", item['precio'])
      print("Link", item['link'])
      print("\n")
    return item 
```

## settings.py

```
# Configure item pipelines
# El numero es la prioridad
ITEM_PIPELINES = {
  'python_05.pipelines.ValidarMacbook': 100,
  'python_05.pipelines.ValidarPrecio': 200,
  'python_05.pipelines.MarkarComoViable': 300,
}

# Configurar feed exporters
# XML JSON CSV son aceptados
FEED_FORMAT = 'json'
FEED_URI = 'tmp/macbook.json'

```










