To install and run the jmeter test:

1. Download JMeter from here http://tweedo.com/mirror/apache//jmeter/binaries/apache-jmeter-2.11.zip
2. Unzip it to a directory of your choice (will be called ${jmeter-home} in this guide
3. Make binaries executable ( chmod +x ${jmeter-home}/bin/jmeter )
4. Run JMeter ( cd ${jmeter-home} => ./bin/jmeter )
5. Open SemaGrow Stack JMeter Workspace ( semagrow-stack-jmeter.jmx )
 
Situation until now :

1. You have a JMeter workspace that's running two SPARQL queries agains dbpedia ( SELECT * WHERE { ?s ?p ?o } LIMIT 1 (and 2) )
2. You have a JMeter workspace that's simulating one ( = 1) user running two queries once ( = 1 time ) => results in two ( = 2 ) requests to dbpedia.
3. Run this test : ctrl+R 

Checkout output of Listeners : 

1. In JMeter open "Thread Group" => "HTTP Request"
2. Click on the nodes with the "meter"-icon (all these listeners will have different output)
3. note documentation of listeners: http://jmeter.apache.org/usermanual/listeners.html


Adapting settings :

1. Thread Group
	1.1. Number of Threads (users) : simulates the number of users
	1.2. Loop Count (should correspond to the number of queries (lines) in SparqlQueries.csv
2. HTTP Request Defaults (these settings will be taken for all HTTP Requests)
	1.1. Server Name or IP : the endpoint's domain
	1.2. Path : the path to the endpoint
3. HTTP Request
	1.1. Parameters : key=query, value=${query} [ = query from SparqlQueries.csv ]
	
4. SPARQL Queries from CSV
	1.1. Definition on the source file for the SPARQL Queries (one query per line)


