---
layout: post
title: "Downloading PDF Files Using Python"
date: 2013-06-14 11:35
comments: true
categories: 
---
Python Script to Download PDF files Using gspread library retrieving  data from spreadsheet and requests for downloading it as a zip file.
First you need to install python packages "gspread" and "requests".

{% codeblock %}
import requests
import gspread
gc = gspread.login('Username@gmail.com','Password')
spreadsheet = gc.open_by_url("URL of Spreadsheet")	
worksheet = spreadsheet.sheet1
cell = worksheet.cell(2, 2)
value = cell.values
print(value)
print "downloading with requests"
r = requests.get(value)
with open("code.zip", "wb") as code:
   code.write(r.content)
{% endcodeblock %}
