# Chat-Server API

General variables:
* [chat-server-host] - URL of SEPIA Chat-Server (aka WebSocket server), e.g. `localhost:20723` or `192.168.0.1:20726/sepia/chat`
* [auth-token] - 'userId;loginToken' combination to authenticate API communication and user
* [client] - A string that contains info about the client type and device id, e.g. 'b1_chrome_browser_v0.22.0'

## Example calls

### Server Status

#### Ping

```
Javascript Ajax call example config:
{
    "url": "http://[assist-server-host]/ping",
    "timeout": 5000,
    "type": "GET"
}
```

### Connections

#### Get Client Connections

Get a list of clients that are currently connected to the Chat-Server.  
Note: If the calling user is the administrator this endpoint will return ALL connected clients, if not it will only return the OWN clients (of this user).

```
Javascript Ajax call example config:
{
	"url": "http://[chat-server-host]/getOwnClientConnections",
	"timeout": 15000,
	"type": "POST",
	"data": {
		"client": "[client]",
		"GUUID": "uid1007",
		"PWD": "myClearTextPassword123"
	},
	"headers": {
		"content-type": "application/json"
	}
}
```

### Channels

#### Create/join/delete/get channels/get missed messages

__under construction__

### WebSocket APIs

__under construction__
