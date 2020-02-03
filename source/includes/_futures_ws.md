# WebSocket

## Guidelines

### General Message Request/Handling Logic from Client Side
 
* Client usually initiate request with `op` parameter (followed by other required parameters).
* Server usually reply message with `m` value to indicate message topic, e.g., `order`, `depth`, `auth`.
* Private data response usually has `accountId` field, such as `order`, `balance`; public data response usually contains `symbol` field.
* Uniquie `id` parameter is recommended for your request. We will echo it back for you to track the requests. (The only exception is `depth-snapshot`, we do not include `id`)

### WebSocket Request

`WSS <account-group>/api/pro/v1/stream`

In order to authorize the session you must include `<account-group>` in the URL. Without `<account-group>`, you can 
only subscribe to public data. 

