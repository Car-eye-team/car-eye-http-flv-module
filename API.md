# 下列接口都是基于README.md中的配置实例给出的，`[]`中的参数是可选的，详情请查看README.md。

# 发布

## 注意，下列命令仅列出ffmpeg推流的使用方法，除此之外，[OBS](https://obsproject.com)和支持RTMP协议的摄像头也可以用来推流。

    ffmpeg -re -i MEDIAFILE -vcodec copy -acodec copy -f flv rtmp://example.com[:port]/appname/streamname

# 播放

## RTMP方式

	rtmp://example.com[:port]/appname/streamname

## HTTP-FLV方式

    http://example.com[:port]/dir?[port=xxx&]app=appname&stream=streamname

# 数据统计

## 注意，多进程模式下，下列请求只能获取一个Nginx子进程上的数据统计信息。

    http://example.com[:port]/stat

# 控制

    http://server.com/control/drop/publisher|subscriber|client[?srv=SRV&app=APP&name=NAME&clientid=CLIENTID]

`drop/publisher`表示关闭推流连接，`drop/subscriber`表示关闭播放连接，`drop/client`表示关闭推流和播放连接。
参数`srv`表示rtmp配置块中server配置块的索引，从0开始，默认是第一个。
参数`app`和`name`与上述的appname和streamname对应。
参数`clientid`表示客户端id，可以通过查看stat得到，用于精确控制。
