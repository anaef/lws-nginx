# LWS Library

The LWS library provides functions and other values for implementing web services with LWS. The
library is loaded automatically.


## log([level,] message)

Logs a message in the error log of the web server. The argument *message* must be a string value,
and the optional argument *level* can take the values `emerg`, `alert`, `crit`, `err`, `warn`,
`notice`, `info`, and `debug`; it defaults to `err`.


## redirect(location [, args])

Schedules an internal redirect to *location*. If *location* starts with `@`, it refers to
a named location. Otherwise, *location* refers to a path, and *args* are optional query arguments.
The request becomes internal and can use locations marked with the `internal` directive. A Lua
chunk should return after scheduling an internal redirect.


## parseargs(args)

Parses the URL query parameters in *args* and returns them as a table. For repeated keys, only the
final value is provided. The function also parses response bodies with a content type of
`application/x-www-form-urlencoded`.


## status

Represents a table of common HTTP status codes with strings as keys and integers as values.
Indexing this table is strict and generates a Lua error if a key is not found.

| Key | Value |
| --- | --- |
| `CONTINUE` | 100 |
| `SWITCHING_PROTOCOLS` | 101 |
| `PROCESSING` | 102 |
| `OK` | 200 |
| `CREATED` | 201 |
| `ACCEPTED` | 202 |
| `NON_AUTHORITATIVE_INFORMATION` | 203 |
| `NO_CONTENT` | 204 |
| `RESET_CONTENT` | 205 |
| `PARTIAL_CONTENT` | 206 |
| `MULTIPLE_CHOICES` | 300 |
| `MOVED_PERMANENTLY` | 301 |
| `FOUND` | 302 |
| `SEE_OTHER` | 303 |
| `NOT_MODIFIED` | 304 |
| `USE_PROXY` | 305 |
| `TEMPORARY_REDIRECT` | 307 |
| `PERMANENT_REDIRECT` | 308 |
| `BAD_REQUEST` | 400 |
| `UNAUTHORIZED` | 401 |
| `PAYMENT_REQUIRED` | 402 |
| `FORBIDDEN` | 403 |
| `NOT_FOUND` | 404 |
| `METHOD_NOT_ALLOWED` | 405 |
| `NOT_ACCEPTABLE` | 406 |
| `PROXY_AUTHENTICATION_REQUIRED` | 407 |
| `REQUEST_TIMEOUT` | 408 |
| `CONFLICT` | 409 |
| `GONE` | 410 |
| `LENGTH_REQUIRED` | 411 |
| `PRECONDITION_FAILED` | 412 |
| `REQUEST_ENTITY_TOO_LARGE` | 413 |
| `REQUEST_URI_TOO_LARGE` | 414 |
| `UNSUPPORTED_MEDIA_TYPE` | 415 |
| `REQUEST_RANGE_NOT_SATISFIABLE` | 416 |
| `EXPECTATION_FAILED` | 417 |
| `MISDIRECTED_REQUEST` | 421 |
| `TOO_MANY_REQUESTS` | 429 |
| `INTERNAL_SERVER_ERROR` | 500 |
| `NOT_IMPLEMENTED` | 501 |
| `BAD_GATEWAY` | 502 |
| `SERVICE_UNAVAILABLE` | 503 |
| `GATEWAY_TIMEOUT` | 504 |
| `HTTP_VERSION_NOT_SUPPORTED` | 505 |
| `INSUFFICIENT_STORAGE` | 507 |