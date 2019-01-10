# VScreen

## Version 0.1.0

### Handshake

Client will initiate the communication with the following format:
```json
{
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

Client will have the following operations:

| Operation | Code |
|-----------|:----:|
| Play      |   0  |
| Pause     |   1  |
| Next      |   2  |
| Add       |   3  |
| Seek      |   4  |

#### Play

```json
{
  "operation": 0
}
```

#### Pause

```json
{
  "operation": 1
}
```

#### Next

```json
{
  "operation": 2
}
```

#### Add

```json
{
  "operation": 3,
  "url": "<video's url, e.g. https://www.youtube.com/watch?v=PtHdTnfQ_NM>"
}
```

#### Seek

`position` is in range of [0.0, 1.0]. `0.0` means the beginning.
`1.0` means the end.

```json
{
  "operation": 4,
  "position": 0
}
```