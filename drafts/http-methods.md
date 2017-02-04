    GET
        Most common method
        Browsers will want to cache these requests
        Used for showing data to users
        Do not initiate actions (such as sending emails, submitting orders, deleting things) with GET unless you are really, really sure
        Can't attach a body to a GET request
        R (read) in CRUD
    POST
        Second most common method
        Browers will alert the user if they try to refresh a POST request
            So probably don't use for showing a filtered list of things
        Used for initiating actions
        Parameters are usually put into the body of the request
        C (create) in CRUD
    PUT
        Idempotent, meaning no matter how many times the user issues a PUT request on a resource, the change/action should only happen once
        PUT should include the whole resource, use PATCH to update part of the resource
        U (update) in CRUD
    DELETE
        Also Idempotent
        Can return 204 on successful deletion
        D in CRUD
    HEAD
        Returns the headers for the resource
        Like doing a GET without wanting the response body
    PATCH
        Idempotent
        Used for updating a resource with only part of the data
    OPTIONS
        See CORS