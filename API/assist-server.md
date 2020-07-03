# Assist-Server API

General variables:
* [assist-server-host] - URL of SEPIA Assist-Server, e.g. `localhost:20721`
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

### Authentication

#### Validation

```
Javascript Ajax call example config:
{
	"url": "http://[assist-server-host]/authentication",
	"timeout": 5000,
	"type": "POST",
	"data": {
		"action": "validate",
		"client": "[client]",
		"GUUID": "uid1007",
		"PWD": "myClearTextPassword123"
	},
	"headers": {
		"content-type": "application/json"
	}
}
```

**Note:** Instead of "GUUID" and "PWD" you can use "KEY". The "KEY" field is build using the GUUID (user ID) and a hashed version of the password OR the token received via previous logins (if its still valid).  
Build instructions (example Node.js): `KEY = GUUID + ";" + crypto.createHash('sha256').update(PWD + "salty1").digest('hex');`  
  
Example result (reduced):
```
{
	"result": "success",
	"access_level": 1,
	"uid": "uid1007",
	"user_name": {
		"nick": "Boss"
	},
	"user_lang_code": "de",
	"keyToken": "80730fd2...",
	"keyToken_TS": 1593077546936,
	"user_roles": [
		"user",
		"developer",
		"smarthomeguest"
	],
	"email": "test@sepia.localhost"
}
```

### Assist Endpoints

#### Interpret / Understand / Interview / Answer

```
Javascript Ajax call example config:
{
	"url": "http://[assist-server-host]/answer",
	"timeout": 10000,
	"type": "POST",
	"data": {
		text: "Hello how are you?",
		lang: "en",
		time: 1593104326980,
		time_local: "2020.06.25_18:59:00",
		user_location: "{\"latitude\":\"52.52\",\"longitude\":\"13.37\",\"city\":\"Berlin\",\"country\":\"Germany\"}",
		custom_data: {
			prefTempUnit: "C"
		},
		"KEY": "[auth-token]",
		"client": "[client]"
	},
	"headers": {
		"content-type": "application/x-www-form-urlencoded"
	}
}
```

**Note:** The same data can be sent to the endpoints `/interpret`, `/understand`, `/interview` and `/answer` (as given in the example) each giving back a result that represents a different step in the NLU/conversation process.  
Additional state variables are available but not yet documented.

### Remote Actions

#### Remote trigger

```
Javascript Ajax call example config:
{
	"url": "http://[assist-server-host]/remote-action",
	"timeout": 5000,
	"type": "POST",
	"data": {
		"action": "{\"key\":\"mic\", \"language\":\"de\"}",
		"type": "hotkey",
		"targetChannelId": "",
		"targetDeviceId": "b1",
		"KEY": "[auth-token]",
		"client": "[client]"
	},
	"headers": {
		"content-type": "application/x-www-form-urlencoded"
	}
}
```

**Note:** Support depends on specific client app. 'language' action parameter is currently ignored by main client (HTML app v0.22.0).  
Since client v0.22.1 'action' can be either a string or object.  
Possible 'key' values are:
* `mic` - triggers microphone
* `F4` - same as 'mic' but respects app settings for 'useWakeWord'
* `ao` - triggers always on mode
* `back`, `next`, `prev` - navigates UI

#### Remote sync (since client v0.22.1)

```
Javascript Ajax call example config:
{
	"url": "http://[assist-server-host]/remote-action",
	"timeout": 5000,
	"type": "POST",
	"data": {
		"action": {
			"events": "myView",
			"forceUpdate": false,
			"updateLocation": false
		},
		"type": "sync",
		"targetChannelId": "",
		"targetDeviceId": "b1",
		"KEY": "[auth-token]",
		"client": "[client]"
	},
	"headers": {
		"content-type": "application/x-www-form-urlencoded"
	}
}
```

Possible 'events' values are 'myView' (supports 'updateLocation'), 'timer' and 'alarm' (client v0.22.1).


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
		"mood": 5,
		"KEY": "[auth-token]",
		"client": "[client]"
	},
	"headers": {
		"content-type": "application/x-www-form-urlencoded"
	}
}
```

