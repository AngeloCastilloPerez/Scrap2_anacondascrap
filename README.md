# Extract Data Scrap
Descarga de datos: Países del mundo por población (2022)
import scrapy


    class WorldometersSpider(scrapy.Spider):
         name = 'worldometers'
         allowed_domains = ['www.worldometers.info'] #Solo se hara scraptin a los vinculos en esta raíz
         start_urls = ['https://www.worldometers.info/world-population/population-by-country/']

     def parse(self, response):
            rows = response.xpath('//tr')

             for row in rows:
                 #title = response.xpath('//h1/text()').get()
                countries = row.xpath('./td/a/text()').get()
                 population = row.xpath('./td[3]/text()').get()

             yield{
                #'titles':title,
                'countries': countries,
                'population': population,
                   }
            
# Curso de Web Scraping en Python | Web Scraping Avanzado con Scrapy [Nivel Avanzado]:

https://www.youtube.com/watch?v=S_znhijDygM&ab_channel=FrankAndrade

Página : 

https://www.worldometers.info/world-population/population-by-country/
