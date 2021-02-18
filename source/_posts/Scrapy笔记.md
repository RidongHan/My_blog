---
title: Scrapy使用笔记
tags:
  - 爬虫框架
  - python
categories: python爬虫
abbrlink: '20200827a'
date: 2020-08-27 14:13:55
---
# 1.创建项目
 
> scrapy startproject tutorial 创建名为tutorial的项目

# 2.定义Item
> Items.py:

	import scrapy
    
    class DmozItem(scrapy.Item):
	    title = scrapy.Field()
	    link = scrapy.Field()
	    desc = scrapy.Field()


# 3.编写爬虫Spider
 
> tutorial/spiders/下创建 dmoz_spider.py:
> 
> 必须继承scrapy.Spider类；定义 name、start_urls、parse()

	import scrapy
	
	class DmozSpider(scrapy.spiders.Spider):
	    name = "dmoz"
	    allowed_domains = ["dmoz.org"]
	    start_urls = [
	        "http://www.dmoz.org/Computers/Programming/Languages/Python/Books/",
	        "http://www.dmoz.org/Computers/Programming/Languages/Python/Resources/"
	    ]
	
	    def parse(self, response):
	        filename = response.url.split("/")[-2]
	        with open(filename, 'wb') as f:
	            f.write(response.body)

# 4.爬取数据
> 首先，进入项目根目录
>  
> scrapy crawl dmoz

# 5.提取Item: Xpath 和 css 选择器selector
	for sel in response.xpath('//ul/li'):
	    title = sel.xpath('a/text()').extract()
	    link = sel.xpath('a/@href').extract()
	    desc = sel.xpath('text()').extract()
	    print title, link, desc

# 6.使用Item
	from tutorial.items import DmozItem
	def parse(self, response):
	        for sel in response.xpath('//ul/li'):
	            item = TutorialItem()
	            item['title'] = sel.xpath('a/text()').extract()
	            item['link'] = sel.xpath('a/@href').extract()
	            item['desc'] = sel.xpath('text()').extract()
	            yield item

# 7.保存爬取的数据

> scrapy crawl dmoz -o items.json














