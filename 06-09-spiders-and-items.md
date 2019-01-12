# Spiders and Items

```python
$ scrapy startproject python_03
$ cd python_03/python_03/spiders
```
## items.py

```python
class ItemProducto(scrapy.Item):
  titulo = scrapy.Field()
  precio = scrapy.Field()
  link = scrapy.Field()
```
## spider_items.py

```python
import scrapy
from python_03.items import ItemProducto

class SpiderItems(scrapy.Spider):
  name = 'spider_items'
  
  urls = ['https://www.amazon.com/s/ref=nb_sb_noss_2?url=search-alias%3Daps&field-keywords=macbook']
  
  def parse_page(self, response):
    resultados_busqueda = response.css('ul.s-result-list > li')
    
    for producto in resultados_busqueda:
    
      titulo = producto.css('.s-access-title::text').extract_first()
      precio = resultados_busqueda.css('.s-price::text').extract_first()
      link = resultados_busqueda.css('a.s-access-detail-page::attr(href)').extract_first()
      
      titulo_truncado = titulo[:50]
      id_producto = link.split('/')[-1]  # ultimo elemento
      short_link = 'https://www.amazon.com/dp/' + id_producto
      
      item_producto = ItemProducto()
      
      item_producto['titulo'] = titulo_truncado
      item_producto['precio'] = precio
      item_producto['link'] = short_link
      
      yield item_producto  # Es un return q no para el loop
      
        

```


