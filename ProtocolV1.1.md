## ICBP Protocol Version 1, Variant 1

The ICBP Protocol is implemented via a series of endpoints.

### `/info`
This is the only fully set endpoint, all others are defined in the `endpoints` key in the info object.

Returns a JSON document similar to the following. Does not accept any data sent to it and the headers are irrelevant to ICBP.

The `versions` field should be an array of versions in the format `(version).(variant)`.

```json
{
  "versions": [ 1.1 ],
  "endpoints": {
    "websocket": "/ws"
  }
}
```

### `websocket`
Connects with a Websocket with a `Sec-WebSocket-Protocol` header set to `ICBP-V1` and every time a client wishes to recieve the data for a URL, it sends on the Websocket a json message in the format(then followed by a null byte):
```json
{
  "type": "request",
  "method": "(insert method here, i.e. GET or POST)",
  "headers": {
    "Header-Name": "header value"
  },
  "body": "(insert body here except for GET requests)"
}
```
There also should every 5000-7000ms be a heartbeat message sent by the client to the server in the following format(followed by a null byte):
```json
{
  "type": "heartbeat",
  "beatTime": "(insert the amount of time in ms since it last beat as a number)"
}
```
If it has been 10000ms since the last message of any kind on the server side, then it should close the connection.
