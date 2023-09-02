# REST

REST stands for "Representational State Transfer." It is an architectural style and set of constraints for designing networked applications, particularly web services and APIs. RESTful systems are characterized by their statelessness, use of standard HTTP methods (GET, POST, PUT, DELETE), and emphasis on resources and representations.

**Statelessness:** Each request from a client to a server must contain all the information needed to understand and process the request. The server should not store any client state between requests. This allows for scalability and simplicity.

**Client-Server Architecture:** The client and server should be separate from each other and communicate through a well-defined interface. This separation allows for independent development and scalability of both client and server components.

**Resources:** Resources are the key abstractions in REST. They are identified by URLs and can represent real-world entities (e.g., users, products) or virtual concepts (e.g., authentication tokens). Resources can have multiple representations, such as JSON or XML, and different representations can include varying fields.

**HTTP Methods:** RESTful APIs make use of standard HTTP methods to perform actions on resources. The most common methods are GET (retrieve), POST (create), PUT (update), and DELETE (remove). These methods are used to indicate the desired action on a resource.

**Representation:** Resources can have different representations, such as JSON, XML, or HTML. Clients can specify their preferred representation format using the "Accept" header in their requests.

**Stateless Communication:** Communication between client and server should be stateless, meaning that each request from the client to the server should contain all the necessary information. The server does not store any information about the client's state between requests.

**Uniform Interface:** A uniform and consistent interface should be defined for interacting with resources. This simplifies the client's understanding of the API and promotes scalability. The uniform interface is typically provided by standard HTTP methods and resource URLs.

## Endpoints

HTTP Methods

Versioning

## HATEOAS
HATEOAS (Hypermedia as the Engine of Application State) is a fundamental constraint in the REST architectural style. It helps make RESTful APIs more self-descriptive and enables clients to interact with the API in a more discoverable and flexible way by encouraging the inclusion of hypermedia links in the responses of a web service or API. These links provide information about available actions or resources related to the current state of the application. Essentially, HATEOAS allows a client to navigate the application's capabilities dynamically by following links provided in responses, rather than relying on out-of-band information or documentation.

### Standards

While there is no single way to format a HATEOAS response, one common approach is to include a "links" item within the object, which provides structured information about links and their associated actions or resources.
 
#### Example
```
{
  "book": {
    "title": "The Great Gatsby",
    "author": "F. Scott Fitzgerald",
    "genre": "Classic",
    "price": 12.99,
    "links": [
      {
        "rel": "self",
        "href": "/books/12345"
      },
      {
        "rel": "author",
        "href": "/authors/6789"
      },
      {
        "rel": "similar-books",
        "href": "/books/similar?genre=Classic"
      }
    ]
  }
}
```

### HAL+JSON (Hypertext Application Language) 

HAL+JSON is a widely-adopted specification for implementing HATEOAS. It defines a set of conventions for structuring JSON data and is used by frameworks like Spring HATEOAS.

Here are some key characteristics and concepts associated with HAL JSON:

1. **Resource Representation**: In HAL JSON, each resource is represented as a JSON object with key-value pairs.

2. **Hypermedia Links**: HAL JSON includes a "links" object that contains hypermedia links associated with the resource. These links guide clients to related resources or actions. Links are represented as key-value pairs, where the key is a link relation and the value is a URL.

3. **Embedded Resources**: Resources can contain embedded resources within them. Embedded resources are references to other resources and are often used to reduce the number of HTTP requests required to retrieve related data. They are typically placed under the "_embedded" key.

#### Response Media Type (Content-Type Header)
The `application/hal+json` content-type header is sometimes used to indicate that the response follows the HAL JSON format.

Clients can send a request with an "Accept" header specifying "application/hal+json" to indicate their preference for HAL+JSON responses. The server can then respond with data formatted according to the HAL specification.

#### Request Example

```
GET /api/resource HTTP/1.1
Host: example.com
Accept: application/hal+json
```

#### HAL+JSON Response Example

```
HTTP/1.1 200 OK
Content-Type: application/hal+json

{
  "_links": {
    "self": { "href": "/products/123" },
    "author": { "href": "/authors/456" },
    "comments": { "href": "/products/123/comments" }
  },
  "id": 123,
  "name": "Sample Product",
  "_embedded": {
    "category": {
      "_links": {
        "self": { "href": "/categories/789" }
      },
      "name": "Sample Category"
    }
  }
}
```

#### Specification


[JSON Hypertext Application Language](https://tools.ietf.org/html/draft-kelly-json-hal-08)