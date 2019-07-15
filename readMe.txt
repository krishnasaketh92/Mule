Assumptions:
1.the Three different tables are created according to json key's in the input json and the respective data is inserted accordingly 
2.for each record a serial number(sequence called contact_seq) is generated and returned to user on successful insertion of data((identification_id) 
3.The sequence number is made as primary(identification_id) and foreign key in the tables.
4.the above sequence number is used for CRUD operations .
5.for parrallel execution of queries scatter-gatherer is used and flows and flow-refs are used for modularity of the code.
6.exception is handled using catch exception handling 
7.choice router is used to route message to flows based on user operation.
8.the Mule flows are invoked by http listner which listen for requests at http://localhost:8081/ms3/cmapi

sample Inputs:

insert:

URL :http://localhost:8081/ms3/cmapi/read
http method:http://localhost:8081/ms3/cmapi/read
message body:

	"Identification": {
		"FirstName": "Bob",
		"LastName": "Frederick",
		"DOB": "06/21/1980",
		"Gender": "M",
		"Title": "Manager"
	},
	"Address": [{
		"type ": "home",
		"number": 1234,
		"street": "blah blah St",
		"Unit": "1 a",
		"City": "Somewhere",
		"State": "WV",
		"zipcode": "12345"
	}],
	"Communication": [{
			"type": "email",
			"value": "bfe@sample.com",
	  		"preferred" : "true"
		},
		{
			"type": "cell",
			"value": "304-555-8282"
		}
	]
}

Delete :
url :http://localhost:8081/ms3/cmapi/delete
http method:Post
sample body:
{
 "contactId":"45"

}

select :
url :url :http://localhost:8081/ms3/cmapi/select
http method :POST
sample body :

{
 "contactId":"45"

}



