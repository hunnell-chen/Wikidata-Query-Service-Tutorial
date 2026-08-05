# Intro to SPARQL for Cultural Heritage Data in Wikidata[^1]
This tutorial introduces the basics of querying Wikidata using SPARQL, the query language for RDF data. We will start with simple queries and work our way up to more complex ones, including visualizations like maps, charts, and graphs. The Wikidata Query Service at https://query.wikidata.org/ will be our main tool throughout this tutorial.

# Learning Objectives
1. Introduce query languages in general, and SPARQL specifically 
2. Build baseline skills for structuring queries to interact with knowledge graph data and generate data vizualizations
3. Introduce the purpose and usefulness of queries for identifying missing information

# "Quick and dirty" Keyword Searching
There are different ways to query information in Wikidata. The simplest way is to use the search bar at the top of a Wikidata page to for search for a keyword, e.g. search for the Synagogue at Dura-Europos. The search bar at the top of a Wikidata page is set to look by default to search only in the Q-pages (that is, Wikidata items). 
However, the drop down menu at the left of the search box can also be toggled to search for a property (looking in the P-pages). On a separate tab, take a moment to familiarize yourself with this feature. Paying attention to the drop down menu at the left of the search bar, search first for the item (Q-number) for the Synagogue at Dura-Europos. Next, toggle your dropdown to search in the properties (P-numbers) for the "significant person" property page.

The "quick and dirty" method is not much different from other keyword searches you're probably already familiar with. SPARQL queries, in contrast, are much more powerful, as they allow you to search in much more nuanced and granular ways, essentially allowing a user to crawl through a web of relationships among datapoints.

Before we jump into SPARQL, a few useful tips to be aware of as you start exploring the Wikidata ecosystem:
1. For any given entry, there is always the possibility to see other pages that link to the page of interest , e.g. all pages linking to the item for the Synagogue at Dura: [https://www.wikidata.org/wiki/Special:WhatLinksHere/Q39246](https://www.wikidata.org/wiki/Special:WhatLinksHere/Q1577089). Each WD item/property page should have a "What Links Here" link in the righthand menu (sometimes hidden under three vertical dots).

2. To discover Wikidata objects nearby your physical location, you might explore the "nearby search": https://www.wikidata.org/wiki/Special:Nearby

3. WikiProject IDEA items are indexed in Wikidata with the property **on focus list of wikimedia project (P5008)** pointing to **Wikiproject IDEA (Q114241199)**.

---

### Exercise 1: Basic Item Retrieval
Write a SPARQL query to retrieve all items on the WikiProject IDEA focus list.

<details>
<summary>Show me the solution</summary>

```sparql
SELECT ?item ?itemLabel WHERE {
  ?item wdt:P5008 wd:Q114241199 .
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en" . }
}
LIMIT 50
[^1]: This tutorial adapts and builds upon the Library Carpentry Wikidata tutorial available at https://librarycarpentry.github.io/lc-wikidata/05-intro_to_querying.html 
