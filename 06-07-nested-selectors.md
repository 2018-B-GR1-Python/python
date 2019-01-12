# Nested Selectors

```
$ scrapy shell https://www.amazon.com/s/ref=sr_ex_n_1?rh=n%3A172282%2Ck%3Amacbook&bbn=172282&keywords=macbook&ie=UTF8&qid=1547305537
$ from pprint import pprint
$ search_results = response.css('ul.s-result-list > li').extract()
$ type(search_results)
$ pprint(response.css('.s-access-title::text').extract())
$ pprint(search_results.css('.s-access-title::text').extract())
```

