# HTTP

## How does HTTP work?
* HTTP is a request-response protocol
* The client sends a request to the server
* The server responds with the requested data
* Communication between client and server is through a series of messages
* Messages contain information about request or response
* HTTP messages consist of a start line, headers, and a message body.


## What is the HTTP request and response format?

### HTTP request format

* Start line includes:
	* Request method
	* URL
	* HTTP version
* Headers
* Optional message body

```
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/89.0.4389.82 Safari/537.36
Accept-Language: en-US,en;q=0.9
```

### HTTP response format

* Start line includes
	* HTTP version
	* Status code
	* Reason phrase
* Headers
* Optional message body

```
HTTP/1.1 200 OK
Date: Wed, 30 Mar 2023 10:00:00 GMT
Server: Apache/2.4.41 (Ubuntu)
Last-Modified: Mon, 28 Mar 2023 10:00:00 GMT
ETag: "123456789abcdef"
Content-Length: 1234
Content-Type: text/html; charset=UTF-8

<!DOCTYPE html>
<html>
<head>
  <title>Example Page</title>
</head>
<body>
  <h1>Hello, world!</h1>
</body>
</html>
```

* HTTP responses don’t always include a body, such as a 204.

```
HTTP/1.1 204 No Content
Content-Length: 0
Date: Fri, 09 Apr 2023 14:26:00 GMT
Server: Apache/2.4.6 (CentOS) OpenSSL/1.0.2k-fips mod_fcgid/2.3.9 PHP/5.4.16
```

## What is caching in HTTP and how does it work?

* storing a copy of a resource for future use.
* It allows clients to use the cached copy instead of requesting the resource from the server again.
* Caching can improve performance by reducing the amount of time and resources needed to fetch the resource.
* It can also reduce network traffic by minimizing the number of requests sent to the server.
* The cached copy can be stored on the client's device or on an intermediary server between the client and the original server.
* Caching is commonly used in web browsers to improve website loading times by caching static resources such as images and CSS files.

## Browswer caching

* To tell the browser to cache a resource, the server includes caching instructions in the HTTP response headers.
* These headers specify how long the resource should be cached and when the cached copy can be used.
* Headers used to control caching include Cache-Control, Expires, ETag, and Last-Modified.
* These headers allow the server to control how the browser caches resources and when it should request a new copy.
	* Cache-Control: This header specifies the caching directives that must be followed by any cache, including the browser cache. It can include instructions such as how long the resource should be cached, whether it can be cached by intermediate caches, and whether it can be cached at all.
	* Expires: This header specifies an expiration date and time for the cached resource. After this time, the cached copy should be considered stale and a new copy should be requested from the server.
	* ETag: This header provides a unique identifier for the resource that can be used to check if the cached copy is still valid. If the server determines that the resource has changed, it can send a new copy along with a new ETag value.
	* Last-Modified: This header provides the date and time that the resource was last modified. This information can be used to check if the cached copy is still valid. If the server determines that the resource has changed, it can send a new copy along with a new Last-Modified value.

## What is HTTP keep-alive, and how does it work?

* HTTP keep-alive is a mechanism for handling multiple HTTP requests and responses over a single TCP connection.
* It reduces the overhead of establishing and tearing down multiple TCP connections.
* By allowing a single connection to handle multiple requests, HTTP keep-alive can improve performance.
* HTTP keep-alive is supported by most modern web browsers and web servers.
* It is a default feature in HTTP/1.1, but not in earlier versions of the HTTP protocol.
* An example would be chat.

## How to determine HTTP supported version of server
* Look at header returned from web server. Could use Curl to do this. HTTP/1.0, HTTP/1.1, HTTP/2
* Send a head request with curl

```
$ curl -I https://example.com
```

Response

```
HTTP/1.1 200 OK
Date: Fri, 09 Apr 2023 16:35:51 GMT
Server: Apache/2.4.41 (Ubuntu)
```

## HTTP response codes

* 1xx - Informational
* 2xx - Success
* 3xx - Redirection
* 4xx - Client Error
* 5xx - Server Error


