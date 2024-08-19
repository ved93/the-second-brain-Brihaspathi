---
id: '202110081149'
tags: []
related: []
from:
---

# Understanding search queries/ What are you searching for?

Whenever I wanted to buy something, I used to scroll through many products and I always felt why its not giving me the products I want. I never thought shpwoing products based on the search query is difficult. Most of the time user doesnt know the proper name of teh products itself. 
When I joined paytm, this opportunity presented me a problem which I wanted to solve.

Search query Understanding is a process to show relevant products to the user searching for. i.e. I was searching for the syska trimmers ht200, I expect it to show that product. 
We identify , syska is the brand here, trimmer is catg of products and ht200 is a model name. 
To make it more challenging, what if I search for red nike shoes under 5000 and its misspelling versions redd shos under 5000 etc, to have a great search experience I expect to understand my query and return good set of results. 

Having good understanding of search queries determines our serahc experience.


vivo back cover

If we type red tape shoes(favorite example), then we should be able to tell that red is not color here. One aspect of query understanding is to identify if user has made a mistake while typing or he typed a synonyms. i.e. you can search for chappal, bloo tootg headphone, semsang phon , jhutte kam dam wale, jio ka mobile touch wala, best shirt, best smart watch, saste phones .
We aspire to provide best search experience for cases like these.   
second aspect is figureing out attributes(size , color, price) of a query. i.e. shoes size 8, red shoes under 2000 
If we can understand these attributes then we can show only relevant products to user. i.e. We see no point in showing a shoes when we dont have a given size. I have personally have been  disappointed to choose a shoe which doesnt have required size.


We are using deep learning and NLP embeddings to solve this problem. The biggest problem we have is we dont have labelled data for queries. We use click history and some euristics to figure out a label so that we can train models. 


The problem doesnt look challenging for simple queries but 


Whenever a query comes to us, we identify brand , catg of product and attributes like price, color and size then we fetch the relevant products based on these filters. 










