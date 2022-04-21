# 目的

透過 Http api 呼叫，從 server 端關閉 socket 連線。

# 說明

除了有異動和新增下面的 API ，其餘使用基本上完全一樣。

## HTTP API

**關閉 socket 連線**

``` http
GET /apps/:APP_ID/sockets/:SOCKET_ID/destroy/channels/:CHANNEL_NAME
```

其中 SOCKET_ID 可以從 `Echo.socketId();` 取得

channel_name 用來進行 leave 動作以便觸發 PresenceChannelUpdated

**列出所有 socket id**

``` http
GET /apps/:APP_ID/sockets
```

socket ids

```json

[
  "DyjRDrMKePecLHqOAAAO",
  "pdJ7IinrB8ZMH18aAAAC",
  "x-av0NW1ZXoexUKWAAAJ"
]

```

**Channel Get information about a particular channel.**

```http
GET /apps/:APP_ID/channels/:CHANNEL_NAME
```

response 增加 socketId

```json

{
    "subscription_count": 2,
    "occupied": true,
    "user_count": 1,
    "sockets": [
        "pdJ7IinrB8ZMH18aAAAC",
        "DyjRDrMKePecLHqOAAAO",
        "x-av0NW1ZXoexUKWAAAJ"
    ]
}


```

**Channel Users List of users on a channel.**

``` http
GET /apps/:appId/channels/:channelName/users
```

response 增加 socketId

example:

```json
[
    {
        "user_id": 1,
        "user_info": {
            "id": 1,
            "name": "Karick",
            "job_title": null
        },
        "socketId": "DyjRDrMKePecLHqOAAAO"
    },
    {
        "user_id": 2,
        "user_info": {
            "id": 2,
            "name": "Eason",
            "job_title": null
        },
        "socketId": "pdJ7IinrB8ZMH18aAAAC"
    },
    {
        "user_id": 3,
        "user_info": {
            "id": 3,
            "name": "Jocoonopa",
            "job_title": null
        },
        "socketId": "x-av0NW1ZXoexUKWAAAJ"
    }
]
```