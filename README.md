README


## Data Ingestion

The ingest.py function is included in this repo as a functional example of how to ingest data. If you want to maintain and update this data source over and extended period, it is recommended that you handle ingestion through a seperate out of band process, but, following the steps provided here will allow you to ingest the data needed to create a functional bot that will be able to answer natural language questions from the context provided by your document(s).

To ingest the data you would like to use for your chatbot, execute the following steps:

1. Create a folder within the same directory as this document named "ingest"
2. Save any files you want to ingest in the "ingest" directory. 
3. Update the ingest.py file with your openai api key where specified
4. (Recommended) Create a python virutal environment to execute the remaining steps
5. Do a pip install for openai, llamaindex and any other required python libraries. In some cases depending on the types of documents you are ingesting, if you try to execute ingest.py, it may fail and provide an error message indicating you need to install an additional library with pip. If this happens just pip install the specified library and re-execute ingest.py.
6. Execute the ingest.py file with python which, depending on your system should be the command `python3 ingest.py` or `python ingest.py`. This step will create a subdirectory named "storage" which will be loaded with a chunked and vectorized index of your document(s).
7. Tar and zip the storage directory, you can name the archive anything you want: `tar -czvf archive.tar.gz ./storage`
8. Upload you saved archive.tar.gz file to some unauthenticated file or blob store. Make sure the file can be downloaded using curl or wget without requiring authentication. 
9. The data ingestion step is now complete. To include this data in your chatbot build, make sure the URL to your archive.tar.gz file is specified as the file_url value in the init.py file. 