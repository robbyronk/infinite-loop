    URL
        Scheme (HTTP/HTTPS)
        Hostname
        Port
        Path
        Query Parameters
        Fragment (not sent to server)
    Method
    Headers
        Accept: The mime type the client wants, such as `application/json`
        Authorization: Can contain the users credentials, such their JWT. Do not use HTTP Basic Auth.
        Cookie: Previously set cookie(s). They are sent with every request
        Content-Type: The mime type of the body. Used in Request and Response
        Host: The hostname the request is being made for. Your webserver might be interested in this to route requests based on what host is being requested
        Referer
        User Agent
        Location
        Set-Cookie
        Status
    Body
        Body of the request will contain data to store, request parameters, etc
        Body of the response is the data you are interested in, such as the created resource
        