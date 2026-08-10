# Introducing Splunk

Splunk is a SIEM - Security Information and Event Management. Data Analytics, Ingestion, Visual Display and shows the data.

SPL - Search Practice Language

Forwarder - can be universal, heavy or intermediate. Forwards data to an indexer
Indexer - takes raw data, processes it, and stores it. Think of it like a page. A bucket lives in the indexer.
Search Head - main interface; executes search requests. sends a data request to the index.

- Standalone: single instance, our Splunk download, no forwarders. Input resides within the server's configurations.
- Basic: forwarders, basic Splunk deployment.
- Multi-Instance: function separation, multiple indexers.
- Clustering: can increase search capacity, a minimum of 3 search heads. Clustering indexers can also increase availability. needs to be managed through a deployment service

Practice:
1. Run Splunk on a Docker container
2. Ingest tutorial data
3. Apps -> Search & Reporting -> 
