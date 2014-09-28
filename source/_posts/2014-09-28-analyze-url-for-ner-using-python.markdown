---
layout: post
title: "Analyze URL for NER Using Python"
date: 2014-09-28 23:41
comments: true
categories: 
---

The amount of natural language text that is available is increasing day by day.The Complexity of Natural Language makes it difficult to access information in text. So, guys dive in to Text Processing. 

Named Entity Recognition is one of the important sub-task of Text Processing to classify elements in text into pre-defined categories such as the names of persons, organizations, locations etc. Here I will share a code snippet for Entity Extraction using TextRazor API in Python.

Pre-requisities:

	a. Python 2.7
        b. Get a free API key from https://www.textrazor.com 
	c. Install Python SDK for TextRazor. Download zip and run setup.py from https: //github.com/TextRazor/textrazor-python
	
{% codeblock Named Entity Recognition -ner.py %}

from textrazor import TextRazor
#Text Razor API Details

client = TextRazor("<Text Razor API KEY>", extractors=["entities"],do_encryption=True)
client.set_do_cleanup_HTML(True)

#Resolving Entities via two dictionaries

client.set_entity_dbpedia_type_filters(['Person','Company','Place','Organisation'])
client.set_entity_freebase_type_filters(['/people/person','/location/location','/government/politician','/book/periodical','/business/job_title'])

#Sort Entities
response = client.analyze_url(<Type-in URL here to be analyzed>)
entities = list(response.entities())
sorted_entities = sorted(response.entities(), key=lambda entity: entity.starting_position)
seen = set()

for entity in entities:
    if entity.id not in seen:
        print entity.id,entity.freebase_types,entity.dbpedia_types,entity.relevance_score,entity.confidence_score
        seen.add(entity.id)
{% endcodeblock %}

For any queries Contact - tanu<dot>mittal<at>iic<dot>ac<dot>in
