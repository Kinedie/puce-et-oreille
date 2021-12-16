# HTTP
## What is HTTP ?
## About HTTP headers
- the version of the HTTP protocol used
- a HTTP response code
- the response URI
- the HTTP method
## About HTTP bodies
- the host
- the content-type
- the content-length
## About HTTP response status codes
HTTP codes indicate the response state. They own three digits.
- 1XX http codes are used for informative responses.
- 2XX http codes are indicate the request succeded.
- 3XX http codes mean the resource has permanently moved.
- 4XX http codes indicate a client-side error. Either the data are badly structured or incomplete (`400 BAD REQUEST`), or the request in forbidden (`401 UNAUTHORIZED`), or the resource doesn't exist (`404 NOT FOUND`).
- 5XX http codes indicate server-side errors (`500 INTERNAL SERVER ERROR`).
## What's in a HTTP request ?
## What's in a HTTP response ?
## All available HTTP methods
### GET
Displaying the representation of a resource (retrieving data)
### HEAD
It's a bit like the GET method. Nothing but the headers are are sent as a response.
### POST
Creating a new resource (creating and sending data to server).
### PUT
Replacing part of a resource with new content enclosed in the request. (Resource is squashed then replaced with a new object) PUT method is said to be nor safe, not indempotent.
### PATCH
Modifying a resource with changes written in the request content.
### DELETE
Deleting the resource.
### CONNECT
Given a URI, connecting the server to that URI.
### OPTIONS
Given a resource, listing all available actions for that resource.
### TRACE
Controlling the path of the request through several servers. As a response, a VIA header lists all the servers in question.
