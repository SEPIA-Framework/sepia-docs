# Remote-Terminal via CLEXI

General variables:
* [clexi-server-host] - URL of CLEXI server, e.g. `localhost:8080` or `192.168.0.1:9090/clexi`
* [clexi-id] - ID of CLEXI server, by default used as authentication "password", e.g. 'clexi-123' (if your network is open to the public and your proxy has no extra password this should be a safe random hash!)
* [auth-token] - 'userId;loginToken' combination to authenticate API communication and user

## Example calls

### Server Status

#### Ping

```
Javascript Ajax call example config:
{
    "url": "http://[clexi-server-host]/ping",
    "timeout": 5000,
    "type": "GET"
}
```

### HTTP-Events Endpoint

If the default SEPIA Client is connected to a CLEXI server it will listen to CLEXI HTTP **events** forwarded to the **channel 'remote-button'** (this can be extended via client function 'SepiaFW.clexi.addHttpEventsListener').  
Its very similar to the 'remote-action' endpoint of the Assist-Server, but requires no user authentication, but the CLEXI ID and a client that actually connects to the same CLEXI server.

#### Trigger remote-button via HTTP-GET

```
Javascript Ajax call example config:
{
    "url": "http://[clexi-server-host]/event/remote-button?deviceId=o1&button=mic",
    "timeout": 5000,
    "type": "GET",
    "headers": {
		"clexi-id": "[clexi-id]"
    }
}
```

This will trigger the 'remote-button' named 'mic' (microphone) for device ID "o1". There are a number of additional buttons like 'wakeWordOn', 'wakeWordOff' or 'next', 'reload', etc.. Check the remote-action section for the Assist-Server for more details.

#### Trigger remote-button via HTTP-POST

```
Javascript Ajax call example config:
{
	"url": "http://[clexi-server-host]/event/remote-button",
	"timeout": 5000,
	"type": "POST",
	"data": "{\"deviceId\": \"o1\",\"button\": \"mic\"}",
	"headers": {
		"content-type": "application/json",
		"clexi-id": "[clexi-id]"
	}
}
```

This is the same HTTP event as seen above just as HTTP-POST call.

