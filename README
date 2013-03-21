

    ==================================
    |LIFE SCIENCES LINKED DATA (LSLD)|
    ==================================

  
............
INTRODUCTION
^^^^^^^^^^^^

This is a standalone, light-weight, configuration-free bundle to publish Linked
Data. It is meant as an educational tool that students can use to become
familiar with Linked Data, by publishing their own dataset at localhost with
only the necessary hassle, but still being aware of the overal technical
setting. It can also be used for rapid prototyping and deployment of a Linked
Data system. 

The bundle is comprised of:

- Jena-Fuseki as a triple store.
- Jetty as a web server.
- Pubby for the actual Linked Data magic. 

Pubby is already configured to work with one of the example datasets included in
Jena-Fuseki. Jetty includes Pubby as a web application and it is configured
accordingly.

The pack is meant to work in a GNU/Linux system and it needs Java and Ruby
installed. No security nor performance requirements have been taken into account
when building it. The user should have basic knowledge on Unix, HTTP, RDF, OWL,
Linked Data and SPARQL. 

................
STANDARD RUNNING
^^^^^^^^^^^^^^^^

This section shows how to run the pack out of the box, with the example dataset
included in Jena-Fuseki, and the configuration for it (web.xml and
books-config-file.ttl). See bellow to use a different dataset and configuration.

Move to /jena-fuseki-0.2.6-SNAPSHOT and make Jena-Fuseki executable:

chmod +x fuseki-server s-*

Run Jena-Fuseki:

./fuseki-server --update --mem /ds

In another terminal, load data:

./s-put http://localhost:3030/ds/data default Data/books.ttl

Test that data has been loaded:

./s-query --service http://localhost:3030/ds/query 'SELECT * {?s ?p ?o}'

To test on the web, go to http://localhost:3030/sparql.html and execute 'SELECT
* {?s ?p ?o}'
(target graph http://localhost:3030/books.ttl)

Move to /jetty-distribution-9.0.0.M3 and run jetty:

java -jar start.jar jetty.port=8080

Test the whole setup by opening http://localhost:8080/book1 in a browser: there
should be a webpage with clickable links.

.........................
USING A DIFFERENT DATASET
^^^^^^^^^^^^^^^^^^^^^^^^^

A Life Sciences toy dataset, including links to other datasets of the Linked
Open Data cloud, is available at
jena-fuseki-0.2.6-SNAPSHOT/Data/LSLD_example.owl.

This time we will run fuseki differently (inspired by [1]): 

mkdir lslddb

./fuseki-server --update --loc=./lslddb /dataset

In another terminal, upload the dataset:

./s-put http://localhost:3030/dataset/data lsld Data/LSLD_example.owl

A pubby configuration file is already set at
jetty-distribution-9.0.0.M3/webapps/ROOT/WEB-INF/lsld-toy-config-file.ttl, edit
web.xml in the same directory to load the pubby configuration file by commenting
out the prior configuration files:

  <context-param>
    <param-name>config-file</param-name>
    <param-value>lsld-toy-config-file.ttl</param-value>
<!--<param-value>books-config-file.ttl</param-value> -->
<!--<param-value>config.ttl</param-value> -->
  </context-param>
  
In another terminal, run jetty:

java -jar start.jar jetty.port=8080

Test the whole setup by opening http://localhost:8080/Protein_A in a browser:
there should be a webpage with clickable links.

.....
ABOUT
^^^^^

This work is funded the Marie Curie program of the EU and is a project of the
Biological Informatics Group of the Centre for Biotechnology and Plant Genomics
of the UPM, Spain (http://wilkinsonlab.info). Any questions should be directed
to mikel.egana.aranguren@gmail.com. 

................
MORE INFORMATION
^^^^^^^^^^^^^^^^

Linked Data: http://www.w3.org/standards/semanticweb/data
Linked Open Data cloud: http://lod-cloud.net/
RDF: http://www.w3.org/standards/techs/rdf
OWL: http://www.w3.org/standards/techs/owl
SPARQL: http://www.w3.org/standards/techs/sparql
Jena-Fuseki: http://jena.apache.org/documentation/serving_data/index.html
Jetty: http://jetty.codehaus.org/jetty/
Pubby: http://wifo5-03.informatik.uni-mannheim.de/pubby/

.........
FOOTNOTES
^^^^^^^^^

[1]
http://answers.semanticweb.com/questions/9660/fuseki-gives-405-error-during-s-
put