# Assist-Server API

General variables:
* [assist-server-host] - URL of SEPIA Assist-Server, e.g. `localhost:20721`
* [auth-token] - 'userId;loginToken' combination to authenticate API communication and user

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

### Text-To-Speech

#### Get TTS Info

```
Javascript Ajax call example config:
{
    "url": "http://[assist-server-host]/tts-info",
    "timeout": 10000,
    "type": "POST",
    "data": {},
    "headers": {
        "content-type": "application/x-www-form-urlencoded"
    }
}
```

#### Generate Speech

```
Javascript Ajax call example config:
{
    "url": "http://[assist-server-host]/tts",
    "timeout": 10000,
    "type": "POST",
    "data": {
		"text": "Hello World",
		"lang": "en",
		"voice": "default",
		"gender": "default",
		"mood": 5
        "KEY": "[auth-token]",
        "client": "b1_chrome_browser_v0.22.0"
    },
    "headers": {
        "content-type": "application/x-www-form-urlencoded"
    }
}
```

