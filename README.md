# VScreen

## Version 0.1.0

### Common Pattern

Sender Request Format:
```json
{
  "operation": <op_code>,
  ...
}
```

Receiver Response Format:
```json
{
  "operation": <op_code>,
  "status": <status_code>
}
```

### Operations

Client

| Operation | Code |
|-----------|:----:|
| Auth      |   0  |
| Play      |   1  |
| Pause     |   2  |
| Next      |   3  |
| Add       |   4  |
| Seek      |   5  |


### Handshake

Client will initiate the communication with the following format:
```json
{
  "operation": 0,
  "version": "0.1.0",
  "password": "<this is encrypted and set during server setup>"
}
```

Server then either accept or reject the handshake. If rejected,
the server will close the connection. If accepted,
the response will look like following:
```json
{
  "status": 0
}
```

### Client Operations


#### Play

```json
{
  "operation": 1
}
```

#### Pause

```json
{
  "operation": 2
}
```

#### Next

```json
{
  "operation": 3
}
```

#### Add

```json
{
  "operation": 4,
  "url": "<video's url, e.g. https://www.youtube.com/watch?v=PtHdTnfQ_NM>"
}
```

#### Seek

`position` is in range of [0.0, 1.0]. `0.0` means the beginning.
`1.0` means the end.

```json
{
  "operation": 5,
  "position": 0
}
```