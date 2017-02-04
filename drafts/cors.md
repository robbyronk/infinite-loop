# Cross Origin Resource Sharing

You'll run into this if your webapp tries to use an API on another *origin*. An origin is the 
scheme, host and port of where your JavaScript came from. For example, if your JS is served from
`https://app.example.com` and your API is at `https://api.example.com`, you're gonna need CORS.

## A crash course in CORS

To implement CORS in your application, you first need to handle *pre-flight* requests. Pre-flight
requests are sent automatically by the user's browser. They have a HTTP method of `OPTIONS` and 
include a few headers. 

The first pre-flight request header is `Origin` and it will have a value like `https://app.example.com`.
Your server will want to check that the Origin header has a valid value. If the Origin is not what
you expect, your users may be under attack!

The second header to have a look at is `Access-Control-Request-Method` and it will have a HTTP method
as a value. If it's a method your server isn't expecting, reject the pre-flight request, like we'll
see below.

The third header to inspect is `Access-Control-Request-Headers`. It will contain the headers that
the original request will contain. The most common header included here is `Content-Type` since
your API likely speaks JSON and `Content-Type: application/json` will be in all of your API requests.

To accept the pre-flight request, have your server respond with an empty `200 OK` with some extra
headers.

The first response header is `Access-Control-Allow-Origin`. The value of this **has** to match the 
`Origin` header of the pre-flight request. The value can also be `*` (asterisk) which means, *I don't
care about security.* The value can't be a comma separated list of allowed origins, only one. If the 
value doesn't match, the pre-flight request is rejected.
 
The second response header is `Access-Control-Allow-Methods`. This is a comma separated list of
HTTP methods that are allowed. If the value of the `Access-Control-Request-Method` header is not included
the pre-flight request is rejected.

`Access-Control-Allow-Headers` is a comma separated list of request headers that are allowed.
All of the `Access-Control-Request-Headers` must be included to not reject the pre-flight request.

If `Access-Control-Allow-Origin`, `Access-Control-Request-Method` and `Access-Control-Request-Headers`
all pass then the pre-flight request is ready for takeoff and is allowed. 

One more header is recommended, though optional. `Access-Control-Max-Age` sets the length of time
the browser will cache the pre-flight response. Without caching the pre-flight response, your client
will need to issue (and wait for) the pre-flight request before issuing the original request.
 
With the pre-flight request handled, all that's left to do check the `Origin` header on normal
requests and add `Access-Control-Allow-Origin` to normal responses.

## Troubleshooting

When CORS fails, your browser won't help at all. What you'll need to do is use `curl`.

Open your network tab (under Inspect Element) and right click on the failed request, click
"copy as curl". Now paste this into your terminal. Add `-v -s -o /dev/null` on the end.

`-s` tells curl to not output the progress meter.

`-v` will output the headers of the request and the response.

`-o /dev/null` puts the response into a black hole instead of all over your screen.

Make sure your server is adding the right response headers.

For pre-flight (`OPTIONS` method):
- `Access-Control-Allow-Origin`
- `Access-Control-Request-Method`
- `Access-Control-Request-Headers`

For other requests:
- `Access-Control-Allow-Origin`

If the headers are there, make sure that the values are correct.

`Access-Control-Allow-Origin` **must** match character for character with the `Origin` header.

`Access-Control-Request-Method` **must** have the original request method in it. `GET`, `POST`, `PUT`,
`DELETE`, `HEAD`, etc.

## Further Reading

https://developer.mozilla.org/en-US/docs/Web/HTTP/Access_control_CORS

https://en.wikipedia.org/wiki/Cross-origin_resource_sharing


