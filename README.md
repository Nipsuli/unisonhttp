# unisonhttp

WIP Http related stuff.

Uses `utils` from [Nipsuli/unison-utils](https://github.com/Nipsuli/unison-utils)

Status:
* HttpResponse -DONE
* HttpRequest -DONE
* HttpServer -WIP
* HttpClient -TODO

Types:
``` Idris
type HttpResponse = {
  statusCode: Nat,
  headers: Map Text Text,
  body: Optional Text
}

type HttpRequest = {
  method : HttpMethod,
  path : Text,
  query : Map Text Text,
  headers : Map Text Text,
  body : Optional Text
}
```

Main functions:
``` Idris
HttpResponse.toText : HttpResponse -> Text
HttpResponse.fromText : Text -> Optional HttpResponse
HttpResponse.fromBytes : Bytes -> Optional HttpResponse
HttpResponse.toBytes   : HttpResponse -> Bytes

HttpRequest.toText : HttpRequest -> Text
HttpRequest.fromText : Text -> Optional HttpRequest
HttpRequest.fromBytes  : Bytes -> Optional HttpRequest
HttpRequest.toBytes    : HttpRequest -> Bytes
```

Utility functions:
``` Idris
HttpResponse.statusCodeToReason : Nat -> Text
headersToText : Map Text Text -> Text
parseHttpMethod : Text -> Optional HttpMethod
parseMessageHeaders : Text -> Map Text Text
parsePath : Text -> Optional Text
parseQuery : Text -> Map Text Text
parseStatusCode : Text -> Optional Nat
queryToText : Map Text Text -> Text
```

Mapped status codes:
``` Idris
HttpResponse.statusCodeReason = Map.fromList ([
  (100, "Continue"),
  (101, "Switching Protocols"),
  (102, "Processing"),
  (200, "OK"),
  (201, "Created"),
  (202, "Accepted"),
  (203, "Non-Authoritative Information"),
  (204, "No Content"),
  (205, "Reset Content"),
  (206, "Partial Content"),
  (207, "Multi-Status"),
  (208, "Already Reported"),
  (226, "IM Used"),
  (300, "Multiple Choices"),
  (301, "Moved Permanently"),
  (302, "Found"),
  (303, "See Other"),
  (304, "Not Modified"),
  (305, "Use Proxy"),
  (307, "Temporary Redirect"),
  (308, "Permanent Redirect"),
  (400, "Bad Request"),
  (401, "Unauthorized"),
  (402, "Payment Required"),
  (403, "Forbidden"),
  (404, "Not Found"),
  (405, "Method Not Allowed"),
  (406, "Not Acceptable"),
  (407, "Proxy Authentication Required"),
  (408, "Request Timeout"),
  (409, "Conflict"),
  (410, "Gone"),
  (411, "Length Required"),
  (412, "Precondition Failed"),
  (413, "Request Entity Too Large"),
  (414, "Request-URI Too Long"),
  (415, "Unsupported Media Type"),
  (416, "Requested Range Not Satisfiable"),
  (417, "Expectation Failed"),
  (418, "I'm a teapot"),
  (420, "Enhance Your Calm"),
  (422, "Unprocessable Entity"),
  (423, "Locked"),
  (424, "Failed Dependency"),
  (426, "Upgrade Required"),
  (428, "Precondition Required"),
  (429, "Too Many Requests"),
  (431, "Request Header Fields Too Large"),
  (444, "No Response"),
  (449, "Retry With"),
  (450, "Blocked by Windows Parental Controls"),
  (451, "Unavailable For Legal Reasons"),
  (499, "Client Closed Request"),
  (500, "Internal Server Error"),
  (501, "Not Implemented"),
  (502, "Bad Gateway"),
  (503, "Service Unavailable"),
  (504, "Gateway Timeout"),
  (505, "HTTP Version Not Supported"),
  (506, "Variant Also Negotiates"),
  (507, "Insufficient Storage"),
  (508, "Loop Detected"),
  (509, "Bandwidth Limit Exceeded"),
  (510, "Not Extended"),
  (511, "Network Authentication Required")
])
```
