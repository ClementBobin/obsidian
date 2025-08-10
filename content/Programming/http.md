# HTTP Status Codes

## Categories

- **1XX** status codes: Informational Requests
-   **2XX** status codes: Successful Requests
-   **3XX** status codes: Redirects
-   **4XX** status codes: Client Errors
-   **5XX** status codes: Server Errors

## Complete List

| Code | Name                               | Description                                                                                                                                                                                                                                  |
| ---- | ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 100  | Continue                           | Everything so far is OK and that the client should continue with the request or ignore it if it is already finished.                                                                                                                         |
| 101  | Switching Protocols                | The client has asked the server to change protocols and the server has agreed to do so.                                                                                                                                                      |
| 102  | Processing                         | The server has received and is processing the request, but that it does not have a final response yet.                                                                                                                                       |
| 103  | Early Hints                        | Used to return some response headers before final HTTP message.                                                                                                                                                                              |
| 200  | OK                                 | Successful request.                                                                                                                                                                                                                          |
| 201  | Created                            | The server acknowledged the created resource.                                                                                                                                                                                                |
| 202  | Accepted                           | The client's request has been received but the server is still processing it.                                                                                                                                                                |
| 203  | Non-Authoritative Information      | The response that the server sent to the client is not the same as it was when the server sent it.                                                                                                                                           |
| 204  | No Content                         | There is no content to send for this request                                                                                                                                                                                                 |
| 205  | Reset Content                      | Tells the user agent to reset the document which sent this request.                                                                                                                                                                          |
| 206  | Partial Content                    | This response code is used when the range-header is sent from the client to request only part of a resource.                                                                                                                                 |
| 207  | Multi-Status                       | Conveys information about multiple resources, for situations where multiple status codes might be appropriate.                                                                                                                               |
| 208  | Already Reported                   | The members of a DAV binding have already been enumerated in a preceding part of the multi-status response.                                                                                                                                  |
| 226  | IM Used                            | IM is a specific extension of the HTTP protocol. The extension allows a HTTP server to send diffs (changes) of resources to clients.                                                                                                         |
| 300  | Multiple Choices                   | The request has more than one possible response. The user agent should choose one.                                                                                                                                                           |
| 301  | Moved Permanently                  | The URL of the requested resource has been changed permanently. The new URL is given in the response.                                                                                                                                        |
| 302  | Found                              | This response code means that the URI of requested resource has been changed temporarily                                                                                                                                                     |
| 303  | See Other                          | The server sent this response to direct the client to get the requested resource at another URI with a GET request.                                                                                                                          |
| 304  | Not Modified                       | It tells the client that the response has not been modified, so the client can continue to use the same cached version of the response.                                                                                                      |
| 305  | Use Proxy                          | Defined in a previous version of the HTTP specification to indicate that a requested response must be accessed by a proxy. (discontinued)                                                                                                    |
| 307  | Temporary Redirect                 | The server sends this response to direct the client to get the requested resource at another URI with same method that was used in the prior request.                                                                                        |
| 308  | Permanent Redirect                 | This means that the resource is now permanently located at another URI, specified by the Location: HTTP Response header.                                                                                                                     |
| 400  | Bad Request                        | The server could not understand the request                                                                                                                                                                                                  |
| 401  | Unauthorized                       | The client didn't authenticate himself.                                                                                                                                                                                                      |
| 402  | Payment Required                   | This response code is reserved for future use. The initial aim for creating this code was using it for digital payment systems, however this status code is used very rarely and no standard convention exists.                              |
| 403  | Forbidden                          | The client does not have access rights to the content                                                                                                                                                                                        |
| 404  | Not Found                          | The server can not find the requested resource                                                                                                                                                                                               |
| 405  | Method Not Allowed                 | The request method is known by the server but is not supported by the target resource                                                                                                                                                        |
| 406  | Not Acceptable                     | The reponse doens't conforms to the creteria given by the client                                                                                                                                                                             |
| 407  | Proxy Authentication Required      | This is similar to 401 Unauthorized but authentication is needed to be done by a proxy.                                                                                                                                                      |
| 408  | Request Timeout                    | This response is sent on an idle connection by some servers, even without any previous request by the client.                                                                                                                                |
| 409  | Conflict                           | This response is sent when a request conflicts with the current state of the server.                                                                                                                                                         |
| 410  | Gone                               | This response is sent when the requested content has been permanently deleted from server, with no forwarding address.                                                                                                                       |
| 411  | Length Required                    | Server rejected the request because the Content-Length header field is not defined and the server requires it.                                                                                                                               |
| 412  | Precondition Failed                | Access to the target resource has been denied.                                                                                                                                                                                               |
| 413  | Payload Too Large                  | Request entity is larger than limits defined by server.                                                                                                                                                                                      |
| 414  | Request-URI Too Long               | The URI requested by the client is longer than the server is willing to interpret.                                                                                                                                                           |
| 415  | Unsupported Media Type             | The media format is not supported by the server.                                                                                                                                                                                             |
| 416  | Requested Range Not Satisfiable    | The range specified by the Range header field in the request cannot be fulfilled.                                                                                                                                                            |
| 417  | Expectation Failed                 | the expectation indicated by the Expect request header field cannot be met by the server.                                                                                                                                                    |
| 418  | I'm a teapot                       | The server refuses the attempt to brew coffee with a teapot.                                                                                                                                                                                 |
| 421  | Misdirected Request                | The request was directed at a server that is not able to produce a response.                                                                                                                                                                 |
| 422  | Unprocessable Entity               | The request was well-formed but was unable to be followed due to semantic errors.                                                                                                                                                            |
| 423  | Locked                             | The resource that is being accessed is locked.                                                                                                                                                                                               |
| 424  | Failed Dependency                  | The request failed due to failure of a previous request.                                                                                                                                                                                     |
| 426  | Upgrade Required                   | The server refuses to perform the request using the current protocol but might be willing to do so after the client upgrades to a different protocol.                                                                                        |
| 428  | Precondition Required              | his response is intended to prevent the 'lost update' problem, where a client GETs a resource's state, modifies it and PUTs it back to the server, when meanwhile a third party has modified the state on the server, leading to a conflict. |
| 429  | Too Many Requests                  | The user has sent too many requests in a given amount of time                                                                                                                                                                                |
| 431  | Request Header Fields Too Large    | The server is can't process the request because its header fields are too large.                                                                                                                                                             |
| 444  | Connection Closed Without Response | The connection opened, but no data was written.                                                                                                                                                                                              |
| 451  | Unavailable For Legal Reasons      | The user agent requested a resource that cannot legally be provided (such as a web page censored by a government)                                                                                                                            |
| 499  | Client Closed Request              | The client closed the connection, despite the server was processing the request already.                                                                                                                                                     |
| 500  | Internal Server Error              | The server has encountered a situation it does not know how to handle.                                                                                                                                                                       |
| 501  | Not Implemented                    | The request method is not supported by the server and cannot be handled.                                                                                                                                                                     |
| 502  | Bad Gateway                        | This error response means that the server, while working as a gateway to get a response needed to handle the request, got an invalid response.                                                                                               |
| 503  | Service Unavailable                | The server is not ready to handle the request.                                                                                                                                                                                               |
| 504  | Gateway Timeout                    | This error response is given when the server is acting as a gateway and cannot get a response in time.                                                                                                                                       |
| 505  | HTTP Version Not Supported         | The HTTP version used in the request is not supported by the server.                                                                                                                                                                         |
| 506  | Variant Also Negotiates            | the chosen variant resource is configured to engage in transparent content negotiation itself, and is therefore not a proper end point in the negotiation process.                                                                           |
| 507  | Insufficient Storage               | The method could not be performed on the resource because the server is unable to store the representation needed to successfully complete the request.                                                                                      |
| 508  | Loop Detected                      | The server detected an infinite loop while processing the request.                                                                                                                                                                           |
| 510  | Not Extended                       | Further extensions to the request are required for the server to fulfill it.                                                                                                                                                                 |
| 511  | Network Authentication Required    | Indicates that the client needs to authenticate to gain network access.                                                                                                                                                                      |
| 599  | Network Connect Timeout Error      | The connection timed out due to a overloaded server, a hardware error or a infrastructure error.                                                                                                                                             |
HTTP status codes are used to indicate the outcome of a client's request to a server. They provide information about the result of the request and the current state of the server-client interaction. Here is a list of common HTTP status codes along with their descriptions: 
## Informational (1xx) 
- **100 Continue:** The server has received the request headers and the client should proceed to send the request body.
- **101 Switching Protocols:** The server acknowledges that the client is switching to a different protocol. 
- **102 Processing:** The server has received and is processing the request, but no response is available yet. 
- **103 Early Hints:** Indicates that the server is sending hints to the client even before the final response is available.
## Successful (2xx) 
- **200 OK:** The request was successful, and the server has returned the requested data. 
- **201 Created:** The request has been fulfilled, resulting in the creation of a new resource. 
- **202 Accepted:** The request has been accepted for processing, but the processing has not been completed. 
- **203 Non-Authoritative Information:** The server successfully processed the request, but the response might be from a third-party source.
- **204 No Content:** The server successfully processed the request but has no content to send back. 
- **205 Reset Content:** The server instructs the client to reset the document view, clearing the form's input fields.
- **206 Partial Content:** The server is delivering only part of the resource due to a range header sent by the client. 
- **207 Multi-Status:** The response conveys information about multiple resources' status. 
- **208 Already Reported:** The members of a DAV binding have been enumerated already. 
- **226 IM Used:** The server has fulfilled the request for the resource, and the response is a representation of the result of one or more instance-manipulations applied to the current instance.
## Redirection (3xx) 
- **300 Multiple Choices:** Indicates multiple options for the resource, from which the client can choose. 
- **301 Moved Permanently:** The requested resource has been permanently moved to a new location. 
- **302 Found:** The requested resource is temporarily moved to a different location. 
- **303 See Other:** The response to the request can be found under a different URI.
- **304 Not Modified:** The client's cached copy is still valid, and there is no need to send a new request. 
- **305 Use Proxy:** The requested resource must be accessed through the proxy specified in the Location header. 
- **306 Switch Proxy:** No longer used. Originally meant "Subsequent requests should use the specified proxy."
- **307 Temporary Redirect:** The requested resource is temporarily moved to a different location, and the client should use the original request method to retrieve it. 
- **308 Permanent Redirect:** The requested resource is permanently moved to a different location, and the client should use the original request method to retrieve it.
## Client Error (4xx) 
- **400 Bad Request:** The server could not understand the request due to malformed syntax or invalid parameters. 
- **401 Unauthorized:** The client must authenticate itself to get the requested response. 
- **403 Forbidden:** The client does not have permission to access the requested resource. 
- **404 Not Found:** The server could not find the requested resource. 
- **405 Method Not Allowed:** The method specified in the request is not allowed for the resource. 
- **406 Not Acceptable:** The requested resource is only capable of generating content not acceptable according to the client's accept headers. 
- **407 Proxy Authentication Required:** The client must first authenticate itself with the proxy. 
- **408 Request Timeout:** The client did not produce a request within the time the server was prepared to wait. 
- **409 Conflict:** The request could not be completed due to a conflict with the current state of the target resource. 
- **410 Gone:** The target resource is no longer available at the server and no forwarding address is known. 
- **411 Length Required:** The server refuses to accept the request without a defined Content-Length. 
- **412 Precondition Failed:** One or more conditions specified in the request header fields evaluated to false. 
- **413 Payload Too Large:** The server refuses to process the request because the request payload is larger than the server is willing or able to process. 
- **414 URI Too Long:** The server is refusing to service the request because the request-target is longer than the server is willing to interpret. 
- **415 Unsupported Media Type:** The origin server is refusing to service the request because the payload is in a format not supported by this method on the target resource. 
- **416 Range Not Satisfiable:** None of the ranges in the request's Range header field overlap the current extent of the selected resource or that the set of ranges requested has been rejected due to invalid ranges or an excessive request of small or overlapping ranges. 
- **417 Expectation Failed:** The expectation given in the request's Expect header field could not be met by at least one of the inbound servers. 
- **418 I'm a teapot:** Any attempt to brew coffee with a teapot should result in the error code "418 I'm a teapot". The resulting entity body MAY be short and stout. 
- **421 Misdirected Request:** The request was directed at a server that is not able to produce a response. This can be sent by a server that is not configured to produce responses for the combination of scheme and authority that are included in the request URI. 
- **422 Unprocessable Entity:** The server understands the content type of the request entity, and the syntax of the request entity is correct, but it was unable to process the contained instructions. 
- **423 Locked:** The source or destination resource of a method is locked. 
- **424 Failed Dependency:** The method could not be performed on the resource because the requested action depended on another action and that other action failed. 
- **425 Too Early:** The server is unwilling to risk processing a request that might be replayed. 
- **426 Upgrade Required:** The server refuses to perform the request using the current protocol but might be willing to do so after the client upgrades to a different protocol. 
- **428 Precondition Required:** The origin server requires the request to be conditional. 
- **429 Too Many Requests:** The user has sent too many requests in a given amount of time ("rate limiting"). 
- **431 Request Header Fields Too Large:** The server is unwilling to process the request because its header fields are too large. 
- **451 Unavailable For Legal Reasons:** The server is denying access to the resource as a consequence of a legal demand.
## Server Error (5xx) 
- **500 Internal Server Error:** A generic error message indicating that the server has encountered an unexpected condition. 
- **501 Not Implemented:** The server does not have the functionality required to fulfill the request. 
- **502 Bad Gateway:** The server, acting as a gateway, received an invalid response from the upstream server. 
- **503 Service Unavailable:** The server is currently unable to handle the request due to temporary overloading or maintenance. 
- **504 Gateway Timeout:** The server, while acting as a gateway or proxy, did not receive a timely response from the upstream server or some other auxiliary server it needed to access in order to complete the request. 
- **505 HTTP Version Not Supported:** The server does not support, or refuses to support, the major version of HTTP that was used in the request message. 
- **506 Variant Also Negotiates:** Transparent content negotiation for the request results in a circular reference. 
- **507 Insufficient Storage:** The method could not be performed on the resource because the server is unable to store the representation needed to successfully complete the request. 
- **508 Loop Detected:** The server detected an infinite loop while processing the request. 
- **510 Not Extended:** Further extensions to the request are required for the server to fulfill it. 
- **511 Network Authentication Required:** The client needs to authenticate to gain network access. 
- **599 Network Connect Timeout Error:** This status code is not specified in any RFCs, but is used by some HTTP proxies to signal a network connect timeout error.

[And many more... ](https://umbraco.com/knowledge-base/http-status-codes/)

Please note that this is not an exhaustive list, but it covers many of the commonly encountered status codes in web development. Understanding these codes can help you diagnose and troubleshoot issues during server-client communication.
# Introduction to HTTPS

HTTPS (Hypertext Transfer Protocol Secure) is a secure version of the HTTP protocol, which is used for transmitting data between a user's web browser and a website. HTTPS is designed to provide a secure and encrypted connection to protect the confidentiality and integrity of the data exchanged over the internet. It's widely used for online banking, e-commerce, email, and any other sensitive data transmission on the web.

## How HTTPS Works

HTTPS employs a combination of encryption and authentication mechanisms to ensure secure data transfer:

1. **Encryption**: HTTPS uses cryptographic algorithms to encrypt the data transmitted between the user's browser and the web server. This encryption converts the data into a scrambled format, making it unreadable to anyone intercepting the traffic without the proper decryption key.
    
2. **Authentication**: Websites using HTTPS obtain an SSL/TLS (Secure Sockets Layer/Transport Layer Security) certificate from a trusted Certificate Authority (CA). This certificate serves as a digital identity for the website and ensures that the user's browser is connecting to the legitimate site and not a malicious imposter.
    
3. **Data Integrity**: HTTPS also includes mechanisms to verify the integrity of the data during transmission. Any tampering or modification of data while in transit will be detected.
    

## Key Components of HTTPS

- **SSL/TLS Certificate**: Websites that use HTTPS have an SSL/TLS certificate issued by a trusted CA. This certificate contains the website's public key and other information and is used to initiate the secure connection.
    
- **Encryption Protocols**: HTTPS relies on encryption protocols such as TLS (Transport Layer Security) to secure the data. TLS ensures that the data exchanged between the user and the website remains confidential.
    
- **HTTPS Port**: HTTPS typically uses port 443 for communication, while standard HTTP uses port 80. This helps browsers and servers distinguish between secure and non-secure connections.
    

## Advantages of HTTPS

1. **Data Security**: HTTPS ensures that data transmitted between the user and the website is encrypted, making it extremely difficult for unauthorized parties to intercept and decipher the information.
    
2. **Authentication**: Users can trust that they are connecting to the legitimate website and not a fraudulent one, thanks to the SSL/TLS certificate.
    
3. **Search Engine Ranking**: Search engines, such as Google, prioritize websites using HTTPS in their search results, improving their visibility.
    
4. **Compliance**: Many data protection regulations and standards, like GDPR, require the use of HTTPS to protect user data.
    

## How to Recognize HTTPS

Users can identify HTTPS by looking at the address bar of their web browser. A website using HTTPS will display a padlock icon, and the URL will begin with "https://" instead of "http://". Additionally, modern browsers may indicate "Secure" or display the website's name in green.

## Conclusion

HTTPS is a fundamental technology that ensures the secure and encrypted transmission of data over the internet. It provides data security, authentication, and data integrity, making it essential for protecting sensitive information in online transactions, communication, and interactions with websites.