    200 OK - Everything is all good
    201 Created - The request created something.
    202 Accepted - The request was received and is being processed. Check back soon
    204 No Content - The request was successful but there's nothing to return. Sometimes used when deleting resources.
    301 - Permanent Redirection. Rarely used
    302 - Temporary Redirection. Often used for going to HTTPS, sending the user to the login page, taking the user to the originally requested page after logging in, taking the user to the canonical URL, URL shorteners, etc
    304 Not Modifed - Used for caching. The client includes a datetime or hash of the previously received resource. The server returns a 304 if the cached resource can be used.
    400 - Bad request. The client sent a bad request
    401 - The user is not authenticated. The application should have them log in.
    403 - The user is not allowed to make this request. This should be a 404 if the user is not allowed to know if what's being requested exists.
    404 Not Found - The thing you are looking for could not be found. Also used when the user does not have the access to see what's being requested.
    405 Method Not Allowed - The application developer probably screwed up. Check your routes!
    406 Not Acceptable - The Accept headers in the request don't match what the server can produce. The application developer should have a look a the Accept header and make sure it looks correct, then check the server.
    500 Server Error - It could be anything. Anything.
    502 Bad Gateway - You might see this when your application server gives your web server bad data or hangs up on them. Make sure your application server is running and check it's logs.
    503 Service Unavailable - The server is really busy right now. Use an exponential random backoff timer to check if the server comes back.
        Include code on implementing a backoff algorithm