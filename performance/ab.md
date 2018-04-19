# 压测工具 - Apache ab

Apache ab全称ApacheBench，有Apache提供的一个轻量级压测工具，windows、linux下均有对应版本。

## 安装方法

#### windows

到[Apache Http Server](https://httpd.apache.org/download.cgi#apache24https://httpd.apache.org/download.cgi#apache24)官网下载集成软件包 [XAMPP](http://www.apachefriends.org/en/xampp.html) 或 [WampServer](http://www.wampserver.com/)。安装完成后，在`%installPath%/apache/bin`找到ab.exe。

![windows-ab-location](../assets/imgs/windows-ab-location.png)

#### linux

到[Apache Http Server](https://httpd.apache.org/download.cgi#apache24https://httpd.apache.org/download.cgi#apache24)官网下载下载`httpd-{version}.tar.gz`包进行源码安装。安装完毕后在`%installPath%/apache/bin`找到ab。

![apache-http-server-linux-source-targz](../assets/imgs/apache-http-server-linux-source-targz.png)

## 使用方法

以linux下ab为例，windows使用同理。

### ab命令参数

![ab-cmd-options](../assets/imgs/ab-cmd-options.png)

上图红框标记为ab常用参数，含义如下：

- `-n` 请求总数。
- `-c` 并发数。
- `-H` 添加任意Http请求头，包括cookie、user agent等，可添加多个。
- `-p` 当压测post请求时，指定post数据文件路径。
- `-T` 当压测post请求时，指定post数据格式，`application/json`或`application/x-www-form-urlencoded`。

### 实战使用

压测对象为鹅漫U品页面和cgi。

#### 样例1 - 压测GET请求

```bash
./ab -c 800 -n 10000 -k -H "Cookie: uin=o0502383519; skey=@P1crrtHu7;" -H "Accept-Encoding: gzip, deflate"  "http://mall.vip.qq.com/?debug=1&mqqRelogin=false"
```

http://mall.vip.qq.com/?debug=1&mqqRelogin=false 页面从cookie中取出参数校验用户登录态，故通过`-H`参数指定用户cookie。另一`-H`参数则指定了客户端可接收编码格式gzip，目的让Server对响应数据进行压缩。  
`-k`即在http请求头插入`Connection: keep-alive`。命令共模拟800个用户同时请求页面10000次。

#### 样例2 - 压测POST请求

```bash
./ab -T "application/json;charset=UTF-8" -H "User-Agent: Mozilla/5.0 (iPhone; CPU iPhone OS 9_1 like Mac OS X) AppleWebKit/601.1.46 (KHTML, like Gecko) Version/4.0 Chrome/37.0.0.0 Mobile MQQBrowser/6.8 TBS/036823 Safari/537.36 V1_AND_SQ_6.5.3_398_YYB_D QQ/6.5.3.2855 NetType/WIFI WebP/0.3.0 Pixel/1080" -p post.json -c 800 -n 10000 "http://uapi.vip.qq.com/Api/api.brand.condition" 
```

通过`-T`参数指定了post请求参数编码格式为`application/json`，`-p`指定post请求参数文件路径post.json，post.json文件内容如下。

```json
{"brand_id": 16, "page": 1, "per_page": 10}
```

## 测试结果参数详解

```bash
[root@Tencent-SNG /usr/local/apache/bin]# ./ab -T "application/json;charset=UTF-8" -H "X-UmallAPI-Authorization: eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1aWQiOjE0MywiZXhwIjoxNTI2NDQwMTgxLCJwbGF0Zm9ybSI6IiJ9.nYdx1b9RZj1H6ap8_Gkp0UBGj785z7xCZsGtZDtFy9U" -p post.json -c 400 -n 4000 "http://uapi.vip.qq.com/Api/api.cart.seeRecommend"
This is ApacheBench, Version 2.3 <$Revision: 1706008 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking uapi.vip.qq.com (be patient)
Completed 400 requests
Completed 800 requests
Completed 1200 requests
Completed 1600 requests
Completed 2000 requests
Completed 2400 requests
Completed 2800 requests
Completed 3200 requests
Completed 3600 requests
Completed 4000 requests
Finished 4000 requests


Server Software:        nginx
Server Hostname:        uapi.vip.qq.com
Server Port:            80

Document Path:          /Api/api.cart.seeRecommend
Document Length:        27483 bytes

Concurrency Level:      400
Time taken for tests:   43.532 seconds          #本次测试共消耗时间
Complete requests:      4000                    #完成请求数
Failed requests:        0                       #失败请求数
Total transferred:      110620000 bytes
Total body sent:        1356000
HTML transferred:       109932000 bytes
Requests per second:    91.89 [#/sec] (mean)    #[核心指标] 吞吐率，表示每秒处理的请求数
Time per request:       4353.157 [ms] (mean)    #[核心指标] 每个用户平均等待的时间，等于 Time taken for tests / (Complete requests / Concurrency Level)
Time per request:       10.883 [ms] (mean, across all concurrent requests) #[核心指标] 服务器平均请求处理的时间，为Requests per second吞吐率的倒数
Transfer rate:          2481.59 [Kbytes/sec] received
                        30.42 kb/s sent
                        2512.01 kb/s total

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        4    5   0.2      5       6
Processing:   323 4022 2834.2   3500   13962
Waiting:      318 4017 2834.2   3496   13957
Total:        328 4027 2834.2   3505   13967

Percentage of the requests served within a certain time (ms)
  50%   3505
  66%   4931
  75%   5794
  80%   6366
  90%   7991
  95%   9818
  98%  10857
  99%  12236
 100%  13967 (longest request)
```







