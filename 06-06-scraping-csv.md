# Scraping csv

```
$ scrapy startproject python_03
$ cd python_03/python_03/spiders
```


## csv_spider_03.py

```python
import scrapy
from scrapy.spiders import CSVFeedSpider

class CsvDataset(CSVFeedSpider):

  name = 'csv_spider'
  
  start_urls = ['https://archive.ics.uci.edu/ml/machine-learning-databases/wine-quality/winequality-white.csv']
  
  delimiter = ';'
  
  quotechar = '"'
  
  headers = ['fixed acidity','volatile acidity','citric acid','residual sugar','chlorides',
  'free sulfur dioxide','total sulfur dioxide','density','pH','sulphates','alcohol','quality']
  
  def parse_row(self, response, row):
    print('ph = ',row['pH'])
  
  
```


## Start

```
$ cd ../..
$ scrapy startproject python_03
```
