# Teach-Server API

General variables:
* [teach-server-host] - URL of SEPIA Teach-Server, e.g. `localhost:20722`
* [auth-token] - 'userId;loginToken' combination to authenticate API communication and user

## Example calls

### Submit new command

´´´
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
´´´
