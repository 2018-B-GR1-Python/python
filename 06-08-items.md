# Items

Python scrapy shell

```
$ scrapy shell https://www.amazon.com/s/ref=nb_sb_noss_2?url=search-alias%3Daps&field-keywords=macbook
$ class ItemProducto(scrapy.Item):
    title = scrapy.Field()
    price = scrapy.Field()
    link = scrapy.Field()
$ producto_uno = ItemProducto()
$ from pprint import pprint
$ resultados_busqueda = response.css('ul.s-result-list')
$ pprint(resultados_busqueda.css('.s-access-title::text').extract()) 
$ pprint(resultados_busqueda.css('.s-access-title::text').extract_first()) 
$ producto_uno['title'] = resultados_busqueda.css('.s-access-title::text').extract_first()
$ producto_uno['link'] = resultados_busqueda.css('a.s-access-detail-page::attr(href)').extract_first()
$ producto_uno['price'] = resultados_busqueda.css('.s-price::text').extract_first()

```
