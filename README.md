除了 API 有些許不同，其餘基本上完全一樣。

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

**Channel Users List of users on a channel.**

``` http
GET /apps/:appId/channels/:channelName/users
```

這條的回傳增加 socketId，方便管理 socket 連線

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