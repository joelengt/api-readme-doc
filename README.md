# api readme doc
a simple api documentation in a readme.md

# Format

## response ok
```json
{
	"status": 200,
	"data": {...}
}
```
	
// response error
{
	"status": 404,
	"error": "Not found"
}


// response list with pagination detail or endpoint detail
{
	"status": 200,
	"data": {...},
    "meta": {
      // pagination detail or extra detail
    }
}






// pagination 


// request

// URI: /products?page=5&page_size=20

// response list with pagination detail or endpoint detail
{
	"status": 200,
	"data": {
        "items": {
            [
                {
                    "id": 1,
                    "name": "Widget #1",
                    "color": "red"
                },
                {
                    "id": 2,
                    "name": "Widget #2",
                    "color": "blue"
                },
                {
                    "id": 3,
                    "name": "Widget #3",
                    "color": "green"
                }
            ]
        }
    },
    "meta": {
        "pagination": {
            "page": 5,
            "page_size": 10,
            "total_pages": 20,
            "total_items": 200,
        },
        "links": {
            "previous": "/products/4",
            "self": "/products/5",
            "next": "/products/6",
            "first": "/products/1",
            "last": "/products/33"
        }
    }
}


