

Solr Starts

```bash
solr-integration-strategies/carrot2-3.8.0/solr-4.6.0/example$ 
java -Dsolr.solr.home=../../solr-home -Dsolr.clustering.enabled=true -jar start.jar
```

Solr changed files
```bash
$ git status
#	modified:   ../../solr-home/example/conf/schema.xml
#	modified:   ../../solr-home/example/conf/solrconfig.xml
#	modified:   ../../solr-home/solr.xml
```

Solr facets

http://localhost:8983/solr/select/?q=*:*&facet=true&facet.field=title&facet.prefix=i&rows=0

Solr with Carrot2

Solr TermVectorComponent

http://wiki.apache.org/solr/TermVectorComponent


### Otros Frameworks

https://github.com/zelandiya/maui

Maui se basa en wikipedia para inferir

http://www.quora.com/What-are-good-tools-to-extract-key-words-and-or-topics-tags-from-a-random-paragraph-of-text



Lucene

http://www.lucenetutorial.com/lucene-in-5-minutes.html

http://lucenetuts.blogspot.com.ar/2013/09/tutorial-working-with-lucene-and-eclipse.html


https://lucene.apache.org/core/4_0_0/misc/org/apache/lucene/misc/HighFreqTerms.html

http://stackoverflow.com/questions/12098083/term-vector-frequency-in-lucene-4-0
