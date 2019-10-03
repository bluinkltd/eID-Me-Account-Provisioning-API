Accounts 
==========

Create Account
--------------

This request is used to register a new account for an online identity. Includes an identifier (or username) and email along with claims, which are verified pieces of information about the user's identity. Responds with the information that was stored along with the state (Active/Suspended) of the account.

    POST /api/enterprise/admin/accounts/create
    
### Requests ###

Headers: <br>
* Content-Type: application/json <br>
* Authorization: <i>API Key</i>

Body

    {
      "identifier": "jsmith",
      "email": "jsmith@bluink.ca",
      "claims": {
      	"given_name": "Joe",
      	"family_name": "Smith",
      	"brithdate": "1980-01-01",
      	"street_address":"10 Louisa St",
      	"locality":"Ottawa",
      	"region":"ON",
      	"country":"CA",
      	"directory_username":"jsmith@bluink.ca",
      	"directory_unique_identifier":"72e7bc60-619c-56e5-0c71-fd56dc2ba0a6"
      }
    }
    
    
### Responses ###

Headers: <br>
* Content-Type: application/json <br>
* Code: 201

Body

    {
      "success": true,
      "account": {
      	"uuid":"1c858982-6dae-11e9-b1ff-02420ac8000d",
        "identifier": "jsmith",
      	"email": "jsmith@bluink.ca",
      	"claims": {
      		"name": "Joe Smith",
    	  	"brithdate": "1980-01-01",
    	  	"street_address":"10 Louisa St",
    	  	"locality":"Ottawa",
    	  	"region":"ON",
    	  	"country":"CA",
    	  	"postal_code":"K1R 6Y6"
      	},	
      	"protectedClaims":{
      		"directory_username":"C4xLjUwNzE1LjYuMSI6InVzZXJuYW1lMTIzIn0.8e9U59g9gZZehmFgjlnnDPLheXIriRws-rXiQtjV",
      		"directory_unique_identifier":"LjEuNC4xLjUwNzE1LjYuMiI6ImlkZW50aWZpZXIxMjMifQ.dqFKuakfmDugpEJrEX4gDCIjgF7K4NbR_"
      	},
      	"active": 1,
        "created_at": 1467832851,
        "updated_at": 1467832851
      }
    }
    
Headers: <br>
* Content-Type: application/json <br>
* Code: 401

Body

    {
      "success": false,
      "error": "Account already exists."
    }

    
Update Account
--------------

This request is used to update an existing online identity account. Request must include a unique id (uuid) as well as the identity claims that are to be changed.
Responds with the updated account information and state.

    POST /api/enterprise/admin/accounts/update
    
### Requests ###

Headers: <br>
* Content-Type: application/json <br>
* Authorization: <i>API Key</i>

Body

    {
      "uuid":"1c858982-6dae-11e9-b1ff-02420ac8000d",
      "claims": {
      	"street_address":"16 Chamberlain Ave",
      	"locality":"Ottawa",
      	"region":"ON",
      	"country":"CA",
      	"postal_code":"K1S 3T3"
      }
    }

### Responses ###

Headers: <br>
* Content-Type: application/json <br>
* Code: 201

Body

    {
      "success": true,
      "account": {
        "uuid":"1c858982-6dae-11e9-b1ff-02420ac8000d", 
        "identifier": "jsmith",
      	"email": "jsmith@bluink.ca",
      	"claims":{
      		"name": "Joe Smith",
    	  	"brithdate": "1980-01-01",
    	  	"street_address":"14 Chamberlain Ave",
    	  	"locality":"Ottawa",
    	  	"region":"ON",
    	  	"country":"CA",
    	  	"postal_code":"K1S 3T3"
      	},	
      	"protectedClaims":{
      		"directory_username":"C4xLjUwNzE1LjYuMSI6InVzZXJuYW1lMTIzIn0.8e9U59g9gZZehmFgjlnnDPLheXIriRws-rXiQtjV",
      		"directory_unique_identifier":"LjEuNC4xLjUwNzE1LjYuMiI6ImlkZW50aWZpZXIxMjMifQ.dqFKuakfmDugpEJrEX4gDCIjgF7K4NbR_"
      	},
      	"active": 1,
      	"created_at": 1467832851,
      	"updated_at": 1467835962
      }
    }
    
Headers: <br>
* Content-Type: application/json <br>
* Code: 400

Body

    {
      "success": false,
      "error": "Validation error on input."
    }
    
Headers: <br>
* Content-Type: application/json <br>
* Code: 404

Body

    {
      "success": false,
      "error": "Account does not exist."
    }
    
    
    
View Account
--------------

View an existing online identity account. Request must include the unique id (uuid) as a parameter.
Responds with the existing account information and state.

    GET /api/enterprise/admin/accounts/view/{uuid}
    
### Request ###

Headers: <br>
* Content-Type: application/json <br>
* Authorization: <i>API Key</i>


### Responses ###

Headers: <br>
* Content-Type: application/json <br>
* Code: 200

Body

    {
      "success": true,
      "account": {
        "uuid":"1c858982-6dae-11e9-b1ff-02420ac8000d", 
        "identifier": "jsmith",
      	"email": "jsmith@bluink.ca",
      	"claims": {
      		"name": "Joe Smith",
    	  	"brithdate": "1980-01-01",
    	  	"street_address":"14 Chamberlain Ave",
    	  	"locality":"Ottawa",
    	  	"region":"ON",
    	  	"country":"CA",
    	  	"postal_code":"K1S 3T3"
      	},	
      	"protectedClaims":{
      		"directory_username":"C4xLjUwNzE1LjYuMSI6InVzZXJuYW1lMTIzIn0.8e9U59g9gZZehmFgjlnnDPLheXIriRws-rXiQtjV",
      		"directory_unique_identifier":"LjEuNC4xLjUwNzE1LjYuMiI6ImlkZW50aWZpZXIxMjMifQ.dqFKuakfmDugpEJrEX4gDCIjgF7K4NbR_"
      	},
      	"active": 1,
        "created_at": 1467832851,
        "updated_at": 1467835962
      }
    }
    
Headers: <br>
* Content-Type: application/json <br>
* Code: 404

Body

    {
      "success": false,
      "error": "Account does not exist."
    }
    
    
Activate/Suspend Account
-------------------------

Activates or suspends an existing online identity account. Request must include the unique id (uuid) of the account as well as the 
boolean value (0 or 1) of the state. Responds with the account identifier, email and state.

    POST /api/enterprise/admin/accounts/activate
    
### Request ###

Headers: <br>
* Content-Type: application/json <br>
* Authorization: <i>API Key</i>

Body

    {
      "uuid":"1c858982-6dae-11e9-b1ff-02420ac8000d",
      "active":0
    }

### Responses ###

Headers: <br>
* Content-Type: application/json <br>
* Code: 201

Body

    {
      "success": true,
      "account": {
        "uuid":"1c858982-6dae-11e9-b1ff-02420ac8000d", 
        "identifier": "jsmith",
      	"email": "jsmith@bluink.ca",
      	"deleted":1467846149
      }
    }
    
Headers: <br>
* Content-Type: application/json <br>
* Code: 404

Body

    {
      "success": false,
      "error": "Account does not exist."
    }

Delete Account
---------------
Permanently removes the online identity account. Request must include the unique id (uuid) of the account to be deleted. 
The response returns the identifier and email account details as they were known before the user was deleted, as well as a 
timestamp of deletion.


    POST /api/enterprise/admin/delete
    

### Request ###

Headers: <br>
* Content-Type: application/json <br>
* Authorization: <i>API Key</i>

Body

    {
      "uuid":"1c858982-6dae-11e9-b1ff-02420ac8000d"
    }
    

### Responses ###

Headers: <br>
* Content-Type: application/json <br>
* Code: 201

Body

    {
      "success": true,
      "account": {
        "uuid":"1c858982-6dae-11e9-b1ff-02420ac8000d", 
        "identifier": "jsmith",
        "email": "jsmith@bluink.ca",
        "deleted":1467846149
      }
    }
    
    
Headers: <br>
* Content-Type: application/json <br>
* Code: 404

Body

    {
      "success": false,
      "error": "Account does not exist."
    }


    

















