Task 1. Questions:
A. What type of content did the server return?
JSON type


B. Where do you see the resource ID?
"id": 1

C. Can you see the HTTP status code?
No. Just the body

-------------------------------------------------------------------------

Task 2. Questions:
D. What does 200 mean?
It means that we have successfully reached the server.(OK)

E. What category of status code is it?
Success Category.

F. What other codes do you know?
404: Not found -> Client Error
201 : Created -> Success
500: Internal server error -> Server Error

-------------------------------------------------------------------------

Task 3. Questions:
G. What would happen if Content-Type were text/html instead?
The client would treat the response as a web page rather than structured data, making it difficult for applications to parse the JSON programmatically.

H. Does the content-length match the actual size of the body?
Yes, it represents the exact size of the message body in bytes (292 bytes in this case). It ensures the receiver knows when the data transfer is complete.

I. Why is Connection important in high-traffic systems?
Persistent connections (keep-alive) allow multiple requests/responses over a single TCP connection, reducing latency and saving server resources by avoiding repetitive handshakes.

-------------------------------------------------------------------------

Task 4. Questions
J. What status code did you receive?
The server returned an **HTTP 404 Not Found** status code.

K. Is there a response body?
Yes, there is a very minimal response body, as indicated by the `content-length: 2`. It likely contains an empty JSON object `{}`.

L. How does it differ from the successful case?
The main difference is the **Status Code** (404 vs 200). Additionally, the **Content-Length** is significantly smaller (2 bytes vs 292 bytes) because the server did not return the actual post data, only an error indicator.
-------------------------------------------------------------------------

Task 5. Questions
M. What status code did the server return?
The server returned **201 Created**.

N. What does it mean?
This status code indicates that the request has been fulfilled and has resulted in one or more new resources being created on the server.

O. What headers appear in this response?

- **x-powered-by:** Express (Indicates the backend framework).
- **x-ratelimit-remaining:** 999 (Shows how many more requests are allowed within the current time window).
- **cf-cache-status:** DYNAMIC (Indicates the response was generated in real-time and not served from a cache).
- **server:** cloudflare (The infrastructure provider handling the request).

-------------------------------------------------------------------------

Task 6. Questions
P. Does this API actually validate the token?
No, JSONPlaceholder is a mock API and ignores the Authorization header, returning the data regardless of the token's validity.

Q. What status code would a real secure API return if the token were invalid?
A secure production API would return an **HTTP 401 Unauthorized** status code.

R. What is the difference between 401 and 403?
- **401 Unauthorized:** The request lacks valid authentication credentials (the server doesn't know who you are).
- **403 Forbidden:** The server understands the request and the user is authenticated, but the user does not have permission to access the specific resource (the server knows who you are, but you aren't allowed here).

-------------------------------------------------------------------------

Task 7. Questions
S. When would this be useful?
It is useful when you need to retrieve metadata about a resource (like its size or type) without downloading the actual content. This saves time and bandwidth.

T. Why might monitoring systems use this approach?
Monitoring tools use HEAD requests to check if a server is online and responding (e.g., checking for a 200 OK status) with minimal overhead. It is faster and more cost-effective as it avoids transferring the entire response body.


200	Success	OK.         The action requested by the client was received, understood, and accepted.
201	Success	Created.    The request has been fulfilled and has resulted in one or more new resources being created.
400	Client Error	    Bad Request. The server could not understand the request due to invalid syntax (e.g., malformed JSON).
401	Client Error	    Unauthorized. The request requires user authentication (you are not logged in or the token is wrong).
403	Client Error	    Forbidden. The server understood the request, but refuses to authorize it (you don't have permission).
404	Client Error	    Not Found. The server can't find the requested resource (the URL is wrong or the ID doesn't exist).
500	Server Error	    Internal Server Error. The server encountered an unexpected condition that prevented it from fulfilling the request.

-------------------------------------------------------------------------
TASK 8. 
Returning 200 OK for errors is a "silent failure" that misleads the client into thinking a request succeeded when it actually failed. This breaks automated monitoring tools that track system health via status codes and disrupts client-side logic that expects valid data. Properly using 4xx or 5xx codes is essential for accurate debugging and professional API standards.














