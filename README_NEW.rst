Getting Started
---------------
This is a modified version of original https://github.com/mongodb-labs/solr-doc-manager

I have edded: 
1) filter by field value 
2) remapping of solr fields name

If you want to update solr only with a document with a particular field value you can add in the config.py
inside the args the query keyword

example of config.json file ::
	
	{
	        "mainAddress": "localhost:27017",
	        "verbosity":3,
	        "namespaces": {
	                "recipes.scraped": true
	        },
	        "docManagers": [
	                    {
	                        "docManager": "solr_doc_manager_new",
	                        "targetURL": "http://localhost:8983/solr/mycollection1",
	                        "uniqueKey": "uid",
	                        "autoCommitInterval": 0,
	                        "args":{
	                                "query":{"status":"I"},
	                                "fields_rename":{
	                                        "final_extracted_info.text":"body",
	                                        "final_extracted_info.name":"title"
	                                        }
	                                }
	                    }
	        ]
	}


Usage
~~~~~~~~~~~~
You need to go in to the dir where you have gitted this project and you need to
make export PYTHONPATH=.
then you can start mongo-connector with ``mongo-connector -c /home/roberto/config.json``

Above you can see the config.json file content where there is ::
 	"docManager": "solr_doc_manager_new"

