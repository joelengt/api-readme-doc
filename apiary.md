FORMAT: 1A
HOST: http://polls.apiblueprint.org/

# cromlu

Polls is a simple API allowing consumers to view polls and vote in them.
101 -> https://help.apiary.io/api_101/api_blueprint_tutorial/
repo examples -> https://github.com/apiaryio/api-blueprint.git
doc sample -> https://pandurangpatil.docs.apiary.io/#reference/user/user-collection

## Questions Collection [/questions]

### List All Questions [GET]

+ Response 200 (application/json)

        [
            {
                "question": "Favourite programming language?",
                "published_at": "2015-08-05T08:40:51.620Z",
                "choices": [
                    {
                        "choice": "Swift",
                        "votes": 2048
                    }, {
                        "choice": "Python",
                        "votes": 1024
                    }, {
                        "choice": "Objective-C",
                        "votes": 512
                    }, {
                        "choice": "Ruby",
                        "votes": 256
                    }
                ]
            }
        ]

### Create a New Question [POST]

You may create your own question using this action. It takes a JSON
object containing a question and a collection of answers in the
form of choices.

+ Attributes (object)
    + id: 250FF (string, required)
    + created: 1415203908 (number)
    + percent_off: 25 (number)

+ Request (application/json)

    + Body

        {
            "id": "250FF",
            "created": 1415203908,
            "percent_off": 25,
            "redeem_by": null
        }

+ Response 201 (application/json)

    + Headers

            Location: /questions/2

    + Body

            {
                "question": "Favourite programming language?",
                "published_at": "2015-08-05T08:40:51.620Z",
                "choices": [
                    {
                        "choice": "Swift",
                        "votes": 0
                    }, {
                        "choice": "Python",
                        "votes": 0
                    }, {
                        "choice": "Objective-C",
                        "votes": 0
                    }, {
                        "choice": "Ruby",
                        "votes": 0
                    }
                ]
            }


## Message [/messages/{id}]
This resource represents one particular message identified by its *id*.

### Retrieve Message [GET]
Retrieve a message by its *id*.

+ Response 200 (text/plain)

        Hello World!

### Delete Message [DELETE]
Delete a message.
**Warning:** This action **permanently** removes the message from the database.

+ Response 204


## User [/user/{appId}/{userId}{?force}]
Handle user objects

+ Parameters
    + appId (required, number, `1`) ... Application ID (`appId`)
    + userId (required, number, `1`) ... Numeric `userId` of the User object to manage

### Remove an User [DELETE]
+ Parameters
    + force (optional, boolean, `false`) ... Set to `true` to remove instead of deactivate

+ Response 204


## Bits Collection [/bits{?bit_type}]

### List Latest bits [GET]
List all bits recently inserted into database.

+ Parameters
    + bit_type (number, optional, `1`) ... Type of bit to retrieve: 1: Bits, 2: Newsletter

+ Response 200
    + Attributes
        - places (Place)

    + Body

            {
                "question": "Favourite programming language?",
                "published_at": "2015-08-05T08:40:51.620Z",
                "choices": [
                    {
                        "choice": "Swift",
                        "votes": 0
                    }, {
                        "choice": "Python",
                        "votes": 0
                    }, {
                        "choice": "Objective-C",
                        "votes": 0
                    }, {
                        "choice": "Ruby",
                        "votes": 0
                    }
                ]
            }




## Products [/products{?page}{?items}]
Products API CRUD 

### List all the products [GET]
list all the products with a paginator

+ Parameters
    + page (optional, number, `5`) ... page (`page`)
    + items (optional, number, `10`) ... Numeric `items` per page
        
+ Request
    + Headers
        Content-Type: application/json
  
+ Response 200 (application/json)

    + Body

        {
            "question": "Favourite programming language?",
            "published_at": "2015-08-05T08:40:51.620Z",
            "choices": [
                {
                    "choice": "Swift",
                    "votes": 0
                }, {
                    "choice": "Python",
                    "votes": 0
                }, {
                    "choice": "Objective-C",
                    "votes": 0
                }, {
                    "choice": "Ruby",
                    "votes": 0
                }
            ]
        }


### Create a new product [POST]
create a new product

+ Request

    + Headers
        Content-Type: application/json
        
    + Attributes (object)
        + value_option: 250FF (string, required)
        + age: 19 (number)
        + percent_off: "simple way" (string)

    + Body

        {
            "value_option": "250FF",
            "age": 20,
            "percent_off": "a simple way to overtake",
        }
    

+ Response 201
    + Headers
        Content-Type: application/json
    
    + Attributes (object)
        + value_option: 250FF (string, required)
        + age: 19 (number)
        + percent_off: "simple way" (string)

    + Body

        {
            "value_option": "250FF",
            "age": 20,
            "percent_off": "a simple way to overtake",
        }


## Products [/products/{id}]
Products by id

+ Parameters
    + id (required, number, `12`) ... product (`id`) number

### Get product by id [GET]
get product by id

+ Response 200 (application/json)

    + Body

        {
            "question": "Favourite programming language?",
            "choices": [
                "Swift",
                "Python",
                "Objective-C",
                "Ruby"
            ]
        }

### Update product by id [PUT]
update product by id

+ Request (application/json)
    + Headers
        Content-Type: application/json
        
    + Attributes (object)
        + question: 250FF (string, required)
        + choices: 19 (string)

    + Body

        {
            "question": "Favourite programming language?",
            "choices": [
                "Swift",
                "Python",
                "Objective-C",
                "Ruby"
            ]
        }


+ Response 200 (application/json)

    + Body

        {
            "question": "Favourite programming language?",
            "published_at": "2015-08-05T08:40:51.620Z",
        }
        
+ Response 404 (application/json)

    + Body

        {
            "question": "Favourite programming language?",
            "published_at": "2015-08-05T08:40:51.620Z",
        }


### Delete product by id [DELETE]
delete product by id

+ Response 200 (application/json)

    + Body

        {
            "question": "Favourite programming language?",
            "published_at": "2015-08-05T08:40:51.620Z",
        }



# Data Structures

## Place (object)

- id: `fRge5` (string, required) - The unique ID of the place.
- name: `Battery Harris` (string, required) - Name of the place.
- lat: `40.712017` (number, required) - Latitude as a decimal.
- lon: `-73.950995` (number, required) - Longitude as a decimal.
- status (enum[string])
  - pending - They haven't finished their public profile or whatever.
  - active - Good as gold.
  - closed - This place doesn't exist.
- created_at: `2015-01-07T14:03:43Z` (string, required) - ISO8601 date and time of when the rider was created.

## Place Create (object)

- name: `Battery Harris` (string, required) - Name of the place.
- lat: `40.712017` (number, required) - Latitude as a decimal.
- lon: `-73.950995` (number, required) - Longitude as a decimal.
- status (enum[string])
  - pending - They haven't finished their public profile or whatever.
  - active - Good as gold.
  - closed - This place doesn't exist.
  
## Place Full (object)

- id: `fRge5` (string, required) - The unique ID of the place.
- Include Place Create
- created_at: `2015-01-07T14:03:43Z` (string, required) - ISO8601 date and time of when the rider was created.

