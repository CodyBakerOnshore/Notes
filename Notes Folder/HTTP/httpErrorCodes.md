# HTTP Error Codes

<!-- TOC -->

- [HTTP Error Codes](#http-error-codes)
- [1XX Informational](#1xx-informational)
        - [100: Continue](#100-continue)

<!-- /TOC -->

# 1XX Informational

 This class of status code indicates a provisional response, consisting of the *Status Line* and *Optional Headers*, it is ***Terminated*** by an empty line. There are *NO* required headers for this class of status code.
 * Since HTTP/1.0 ***DID NOT** define any 1xx status codes, **Servers MUST NOT** send a 1xx response to a client **except** under experimental conditions.*
 * a client ***must*** be prepared to accept *one or more* 1xx status codes prior to a regular response, *even if the client does not **expect** a 100(*continue*) status msg*.

### 100: Continue
- The client should *continue* the request.
    + response is used to inform *client* that the initial part of the request has been received and has not yet been rejected by the server.

### 101: Switching Protocols
- The *server* understands *and is willing to comply* with the *client's* request, via the *Upgrade message header field*, for a change in the application protocol being used on ***This** Connection*. The server will switch protocols to those defined by the *response's **Upgrade Header Field** immediately after* the empty line which terminates the 101 response.
    - Protocol should only be switched when it is *advantageous* to do so! 
        + for Ex: switching to a newer version of HTTP is advantageous over older versions, and switching to a real-time, synchronous protocol *might* be advantageous when delivering resources that *deliver* such features.

#2xx Successful

### 200: OK

Request Succeeded
* The request succeeded, The information returned with the response is dependent on the method used in the *request*.
    - For Example(s):
        + GET: an entity corresponding to the requested resource is sent in the response.
        + HEAD: the entity-header fields corresponding to the requested resource are sent in the response *without* and message-body.
        + POST: an entity *describing or containing* the result of the action.
        + TRACE: an entity containing the request message as received by the *end server*.

### 201: Created

### 202: Accepted

### 203: Non-Authoritative Information

### 204: No Content

### 205: 
