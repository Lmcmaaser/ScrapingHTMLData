#ScrapingHTMLData
#Python3

#import urllib, BeautifulSoup from file, and SSL
import urllib.request, urllib.parse, urllib.error
from urllib.request import urlopen
from bs4 import BeautifulSoup
import ssl
import re

#ignore SSL certificate errors
ctx = ssl.create_default_context()
ctx.check_hostname = False
ctx.verify_mode = ssl.CERT_NONE

url = input('Enter - ')
html = urllib.request.urlopen(url, context=ctx).read() #can treat webpage like a file
soup = BeautifulSoup(html, 'html.parser')

numb = []
tags = soup('span')  #retrieve desired tags
for tag in tags:
    numb.append(int(tag.string))
print(sum(numb))
