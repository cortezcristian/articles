

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

https://lucene.apache.org/core/2_9_4/api/all/org/apache/lucene/search/Similarity.html


```java
import java.io.BufferedReader;
import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStreamReader;
import java.text.ParseException;

import org.apache.lucene.analysis.Analyzer;
import org.apache.lucene.analysis.core.WhitespaceAnalyzer;
import org.apache.lucene.document.Document;
import org.apache.lucene.document.Field;
import org.apache.lucene.document.FieldType;
import org.apache.lucene.document.StringField;
import org.apache.lucene.document.TextField;
import org.apache.lucene.index.DirectoryReader;
import org.apache.lucene.index.DocsEnum;
import org.apache.lucene.index.FieldInfo.IndexOptions;
import org.apache.lucene.index.Fields;
import org.apache.lucene.index.IndexWriter;
import org.apache.lucene.index.IndexWriterConfig;
import org.apache.lucene.index.MultiFields;
import org.apache.lucene.index.Terms;
import org.apache.lucene.index.TermsEnum;
import org.apache.lucene.search.similarities.DefaultSimilarity;
import org.apache.lucene.store.Directory;
import org.apache.lucene.store.RAMDirectory;
import org.apache.lucene.util.BytesRef;
import org.apache.lucene.util.Version;
import org.json.simple.JSONArray;
import org.json.simple.JSONObject;
import org.json.simple.parser.JSONParser;


public class Extractor {

	public static void main(String[] args) throws org.json.simple.parser.ParseException {
		// TODO Auto-generated method stub
		System.out.println("Extractor");
		try {
			// Lucene config artifacts
			Directory directory = new RAMDirectory();  
		    Analyzer analyzer = new WhitespaceAnalyzer(Version.LUCENE_40);
		    IndexWriterConfig config = new IndexWriterConfig(Version.LUCENE_40, analyzer);
		    IndexWriter writer = new IndexWriter(directory, config);
		    // Lucene config artifacts ends
			
			// Read File Starts
			String filePath = "/var/www/micheael-lai/usable-300/sites300nohtml.json";
	        BufferedReader br = new BufferedReader(new InputStreamReader(new FileInputStream(filePath), "Cp1252"));         

	        String line;
	        while ((line = br.readLine()) != null) {
	            // process the line.
	        	//System.out.println(line);
                JSONObject site = (JSONObject) new JSONParser().parse(line);
                System.out.println(site.get("text"));
                
                // Load Docs
                addDoc(writer, (String) site.get("text"), (String) site.get("url"));
	           
	        	
	        }
	        
	        // Read File Ends
	        
	        // Lucene Analyze
	        writer.close();
	        br.close();

	        System.out.println("-----------------");
	        DirectoryReader reader = DirectoryReader.open(directory);
	        DefaultSimilarity similarity = new DefaultSimilarity();
			int docnum = reader.numDocs();
			Fields fields = MultiFields.getFields(reader);
			for (String field : fields) {
			    Terms terms = fields.terms(field);
			    TermsEnum termsEnum = terms.iterator(null);
			    while (termsEnum.next() != null) {
			        double idf = similarity.idf(termsEnum.docFreq(), docnum);
			        System.out.println("" + field + ":" + termsEnum.term().utf8ToString() + " idf=" + idf);
			    }
			}
	        /*
	        DocsEnum de = MultiFields.getTermDocsEnum(reader, MultiFields.getLiveDocs(reader), "title", new BytesRef(""));
	        int doc;
	        while((doc = de.nextDoc()) != DocsEnum.NO_MORE_DOCS) {
	              System.out.println(de.freq());
	        }
	        */
	        reader.close();
	        // Lucene Analyze ends
	        
        } catch (IOException e) {
	        e.printStackTrace();
	    }
	}
	
	private static void addDoc(IndexWriter w, String title, String url) throws IOException {
		FieldType fieldType = new FieldType();
	    fieldType.setStoreTermVectors(true);
	    fieldType.setStoreTermVectorPositions(true);
	    fieldType.setIndexed(true);
	    fieldType.setIndexOptions(IndexOptions.DOCS_AND_FREQS);
	    fieldType.setStored(true);
		
		Document doc = new Document();
		doc.add(new Field("title", title, fieldType));
		//doc.add(new TextField("title", title, Field.Store.YES));

		// use a string field for isbn because we don't want it tokenized
		doc.add(new StringField("url", url, Field.Store.YES));
		w.addDocument(doc);
	}

}

```
