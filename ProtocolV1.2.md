## ICBP Protocol Version 1, Variant 2

The ICBP Protocol is implemented via a series of endpoints.

### `/info`
This is the only fully set endpoint, all others are defined in the `endpoints` key in the info object.

Returns a JSON document similar to the following. Does not accept any data sent to it and the headers are irrelevant to ICBP.

The `versions` field should be an array of versions in the format `(version).(variant)`.

```json
{
  "versions": [ 1.2 ],
  "endpoints": {
    "get": "/get",
    "post": "/post",
    "put": "/put",
    "patch": "/patch",
    "delete": "/delete"
  }
}
```

### `get`
The request should be in the JSON format:
```json
{
  "headers": {
    "Header-Name": "header value"
  }
}
```

### `post`
The request should be in the JSON format:
```json
{
  "headers": {
    "Header-Name": "header value"
  },
  "body": "(insert body here)"
}
```

### `put`
The request should be in the JSON format:
```json
{
  "headers": {
    "Header-Name": "header value"
  },
  "body": "(insert body here)"
}
```

### `delete`
The request should be in the JSON format:
```json
{
  "headers": {
    "Header-Name": "header value"
  },
  "body": "(insert body here)"
}
```
