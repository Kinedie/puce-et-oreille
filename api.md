# API
## What does API stands for ?
## What is SOAP and why is its reputation so bad ?
SOAP stands for **Simple Object Access Protocol**.
## What has REST brought ?
REST or REpresentational State Transfer, is an architectural style. Roy Fielding conceptualized it and presented it in 2020.
A RESTful API is a service-oriented architecture. It follows the following constraints :
1. **responsibility segregation** (client / server)
2. **a stateless API**. The request must return the exact same response everytime it is thrown.
3. **a cacheable API**. Using HTTP cache to reduce at best the generation time of the response.
4. **a layered system**. The client is not aware of the process behind the generation of the response.
5. **an uniformed interface for resources**. Each resource :
- must be distinguished by its own unique identifier, such as an ID in the URI.
- must have a representation (be formatted).
- must be self-written ("Content-Type" must be defined).
6. The sixth rule isn't mandatory. **The code may be on demand**, meaning anytime a request is done to the server, the related piece of code may be executed on the client side.
## What about Graphql ?
