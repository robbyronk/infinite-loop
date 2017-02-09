# HTTP Methods

A HTTP Request includes a method (sometimes called a verb) that roughly describes what the request
is intended to do. On the server side, the HTTP method and the URL are often the primary way to 
route requests to different controllers/handlers.

A little glossary in this context:
- safe - the request does not modify data on the server
- idempotent - the request can be made more than once with the same effect as just once
- CRUD - Create, Read, Update, Delete. The four most common actions in applications.

## GET
The GET method is what your browser used to request this webpage. When designing an API, the GET
method is used for retrieving information and objects. GET requests can't have a request body, which
means that request parameters will have to be included in the URL as query parameters or as
request headers. Some examples of parameters are filtering a list of items (i.e. `?color=red`) or
loading page 4 of a forum thread (`?page=4`). Requests made with the GET request should almost never
modify data on the server or cause actions, such as sending an email, to happen.

The GET method is the "Read" in CRUD.

GET requests are safe and idempotent.

## POST
        Second most common method
        Browers will alert the user if they try to refresh a POST request
            So probably don't use for showing a filtered list of things
        Used for initiating actions
        Parameters are often put into the body of the request
        
The POST method is the "Create" in CRUD.

POST requests are not safe or idempotent.

## PUT
        Idempotent, meaning no matter how many times the user issues a PUT request on a resource, the change/action should only happen once
        PUT should include the whole resource, use PATCH to update part of the resource
        
The PUT method is the "Update" in CRUD.

PUT requests are not safe and are idempotent.

## DELETE
        Also Idempotent
        Can return 204 on successful deletion

The DELETE method is the "Delete" in CRUD.

DELETE requests are not safe and are idempotent.

## PATCH
        Idempotent
        Used for updating a resource with only part of the data

The PATCH method is another "Update" in CRUD.

PATCH requests are not safe and are idempotent.

## HEAD
HEAD requests will return only response headers. This request type is like a GET request without
wanting the response body. One use for HEAD requests is to check if a webpage (or script or image)
exists without having the server send the HTML, JS, etc.
  
HEAD requests are safe and idempotent.

## OPTIONS
Most often used for CORS.
        
###### Additional Reading
- https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods
- http://www.restapitutorial.com/lessons/httpmethods.html
- http://www.restapitutorial.com/lessons/idempotency.html
