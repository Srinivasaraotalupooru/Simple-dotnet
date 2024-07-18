# Introduction to HTTP

> HTTP is an application-protocol that defines a set of rules to send requests from the browser to the server and send responses from the server to the browser.

Initially developed by Tim Berners-Lee, later standardized by IETF (Internet Engineering Task Force) and W3C (World Wide Web Consortium).

![image](https://github.com/user-attachments/assets/ab35ea7d-8011-457c-ba56-563e78fe7e0c)


## HTTP Response

![image](https://github.com/user-attachments/assets/92f324bf-5f97-4694-877f-1bea72ffc6e2)

![image](https://github.com/user-attachments/assets/b9ca3277-bb41-41a5-961c-467cf769fe94)

### Response Start Line
Includes HTTP version, status code, and status description.

- **HTTP Version:** 1/1 | 2 | 3
- **Status Code:** 101 | 200 | 302 | 400 | 401 | 404 | 500
- **Status Description:** Switching Protocols | OK | Found | Bad Request | Unauthorized | Not Found | Internal Server Error

### HTTP Response Status Codes

- **1xx | Informational**
  - **101**: Switching Protocols
- **2xx | Success**
  - **200**: OK
- **3xx | Redirection**
  - **302**: Found
  - **304**: Not Modified
- **4xx | Client error**
  - **400**: Bad Request
  - **401**: Unauthorized
  - **404**: Not Found
- **5xx | Server error**
  - **500**: Internal Server Error

### HTTP Response Headers

- **Date**: Date and time of the response. Ex: Tue, 15 Nov 1994 08:12:31 GMT
- **Server**: Name of the server. Ex: Server=Kestrel
- **Content-Type**: MIME type of response body. Ex: text/plain, text/html, application/json, application/xml, etc.
- **Content-Length**: Length (bytes) of response body. Ex: 100
- **Cache-Control**: Indicates the number of seconds that the response can be cached at the browser. Ex: max-age=60
- **Set-Cookie**: Contains cookies to send to the browser. Ex: x=10
- **Access-Control-Allow-Origin**: Used to enable CORS (Cross-Origin-Resource-Sharing). Ex: Access-Control-Allow-Origin: http://www.example.com
- **Location**: Contains URL to redirect. Ex: http://www.example-redirect.com

Further reading: [MDN HTTP Headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers)

## HTTP Request

![image](https://github.com/user-attachments/assets/84db9cca-38d7-4639-8bf8-a92b5f2db9e4)

![image](https://github.com/user-attachments/assets/4a00de2f-72df-4a18-a2e7-9b1db78ace28)

### **HTTP Request - with Query String**

![image](https://github.com/user-attachments/assets/e856f60f-6709-4b16-9794-ad7ca0032efc)


### HTTP Request Headers

- **Accept**: Represents MIME type of response content to be accepted by the client. Ex: text/html
- **Accept-Language**: Represents the natural language of response content to be accepted by the client. Ex: en-US
- **Content-Type**: MIME type of request body. Ex: text/x-www-form-urlencoded, application/json, application/xml, multipart/form-data
- **Content-Length**: Length (bytes) of request body. Ex: 100
- **Date**: Date and time of request. Ex: Tue, 15 Nov 1994 08:12:31 GMT
- **Host**: Server domain name. Ex: www.example.com
- **User-Agent**: Browser (client) details. Ex: Mozilla/5.0 Firefox/12.0
- **Cookie**: Contains cookies to send to the server. Ex: x=100

Further reading: [MDN HTTP Headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers)

## HTTP Request Methods

- **GET**: Requests to retrieve information (page, entity object, or a static file).
- **POST**: Sends an entity object to the server; generally, it will be inserted into the database.
- **PUT**: Sends an entity object to the server; generally updates all properties (full-update) in the database.
- **PATCH**: Sends an entity object to the server; generally updates few properties (partial-update) in the database.
- **DELETE**: Requests to delete an entity in the database.

## HTTP GET vs POST

### GET

- Used to retrieve data from the server.
- Parameters will be in the request URL (as query string only).
- Can send a limited number of characters only to the server. Max: 2048 characters.
- Used mostly as a default method of request for retrieving pages, static files, etc.
- Can be cached by browsers/search engines.

### POST

- Used to insert data into the server.
- Parameters will be in the request body (as query string, JSON, XML, or form-data).
- Can send unlimited data to the server.
- Mostly used for form submission/XHR calls.
- Can't be cached by browsers/search engines.
