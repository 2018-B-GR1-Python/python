
# Reg Exp

Extraer texto que contenga la palabra `friend` xpath

```
$ response.xpath("//*[contains(text(), 'friend')]/text()").extract()
```


Extraer texto que contenga la palabra `friend` css

```
$ response.css(".text:contains('friend'::text)").extract()
```



Extraer informacion del `author` con letra `A` css

```
$ response.css(".author::text").re("A[a-z]*\s\w+")
```

Extraer informacion del `author` con letra `A` xpath

```
$ response.xpath("//*[@class='author'][starts-with(text(), 'A')]/text()").extract()
```
