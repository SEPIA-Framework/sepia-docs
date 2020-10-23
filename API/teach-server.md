# Teach-Server API

General variables:
* [teach-server-host] - URL of SEPIA Teach-Server, e.g. `localhost:20722` or `192.168.0.1:20726/sepia/teach`
* [auth-token] - 'userId;loginToken' combination to authenticate API communication and user

## Example calls

### Submit new command

#### Simple chat

```
Javascript Ajax call example config:
{
    "url": "http://[teach-server-host]/submitPersonalCommand",
    "timeout": 10000,
    "type": "POST",
    "data": {
        "environment": "all",
        "language": "de",
        "user_location": "",
        "sentence": "Hallo didli du",
        "tagged_sentence": "",
        "params": "{\"reply\":\"Hi Flanders\"}",
        "command": "chat",
        "cmd_summary": "chat;;reply=Hi Flanders;;",
        "public": "no",
        "local": "no",
        "explicit": "no",
        "overwriteExisting": true,
        "data": "{\"show_button\":false,\"button\":{\"name\":\"\",\"icon\":\"\"}}",
        "KEY": "[auth-token]",
        "client": "b1_chrome_browser_v0.21.0"
    },
    "headers": {
        "content-type": "application/x-www-form-urlencoded"
    }
}
```

#### Custom Smart Home Command 

```
Javascript Ajax call example config:
{
    "url": "http://[teach-server-host]/submitPersonalCommand",
    "timeout": 10000,
    "type": "POST",
    "data": {
        "environment": "all",
        "language": "de",
        "user_location": "",
        "sentence": "Send Robo to the living-room",
        "tagged_sentence": "",
        "params": "{\"smart_device\":\"<device>;;Cleaner\",\"action\":\"<set>\",\"smart_device_value\":\"{\\\"value\\\":\\\"zone living-room\\\", \\\"type\\\":\\\"custom\\\"}\",\"reply\":\"<1> is going to clean the living-room\"}",
        "command": "smartdevice",
        "cmd_summary": "smartdevice;;smart_device=<device>;;Cleaner;;action=<set>;;smart_device_value={\"value\":\"zone living-room\", \"type\":\"custom\"};;reply=<1> is going to clean the living-room;;",
        "public": "no",
        "local": "no",
        "explicit": "no",
        "overwriteExisting": true,
        "data": "{\"show_button\":true,\"button\":{\"name\":\"Clean LR\",\"icon\":\"&#xE60E;\"}}",
        "KEY": "[auth-token]",
        "client": "b1_chrome_browser_v0.21.0"
    },
    "headers": {
        "content-type": "application/x-www-form-urlencoded"
    }
}
```
