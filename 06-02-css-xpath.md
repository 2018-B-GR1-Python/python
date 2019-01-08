

Inline-style: 
![Scrapy](https://raw.githubusercontent.com/2018-B-GR1-Python/python/master/Screen%20Shot%202019-01-05%20at%2008.08.11.png?raw=true "SCRAPY")


```
$ scrapy shell 'http://quotes.toscrape.com/'
$ response.css('title')
$ response.css('title').extract()
$ response.css('title::text').extract()
$ response.css('.author')
$ type(response.css('.autor'))
$ response.css('.author').extract()
$ type(response.css('.autor').extract())
$ response.css('.author').extract()[0]
$ response.css('.author').extract_first()
$ type(response.css('.autor').extract_first())
$ response.css('.author::text').extract()
$ response.css('.small.author::text').extract()
$ response.css('.quote > .text').extract()
$ response.css('.row > div > div:nth-child(2) > .text::text').extract()
$ response.css('.row > div > div:nth-child(5) > .text::text').extract()
$ response.css('a::attr(href)').extract()

$ response.xpath('/html/head/title').extract()
$ response.xpath('//title').extract()
$ response.xpath('/html/body/div/div[2]/div[1]/div[2]/span[1]').extract()
$ response.xpath('/html/body/div/div/div/div/span').extract()
$ response.xpath('/html/body/div/div/div/div/span/text()').extract()
$ response.xpath("//span[@class=''text]").extract()
$ response.xpath("//span[@class=''text]/text()").extract()

```
