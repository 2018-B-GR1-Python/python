# Nested Selectors

```
$ scrapy shell https://www.amazon.com/s/ref=nb_sb_noss_2?url=search-alias%3Daps&field-keywords=macbook
$ from pprint import pprint
$ search_results = response.css('ul.s-result-list > li').extract()
$ type(search_results)
$ pprint(response.css('.s-access-title::text').extract())
$ pprint(search_results.css('.s-access-title::text').extract())
```

