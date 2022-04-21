和原本的 laravel-echo-server 完全一樣，就多了一道 api

## HTTP API

**關閉 socket 連線**

從 Server 端關閉 socket 連線，並且對傳入的 channel 進行 leave 動作以便觸發 PresenceChannelUpdated

``` http
GET /apps/:APP_ID/channels/:CHANNEL_NAME/sockets/:SOCKET_ID/disconnect
```

其中 SOCKET_ID 可以從 `Echo.socketId();` 取得