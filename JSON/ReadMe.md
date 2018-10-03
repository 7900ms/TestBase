```
Test for get url:

返回 JSON 可以 get 

自定义一个 网址和返回值
/poll
返回
"123"


有没有一个网络API，请求后返回一个json，我可以自定义这个json 内容

https://www.v2ex.com/t/459569



浏览器测试 Request URL 看得到什么 
浏览器测试1 返回JSON
1.
https://api.myjson.com/bins/e3xzc

{
  "name": "Tom"
}
http://myjson.com/api
http://myjson.com/e3xzc

> https://api.myjson.com/bins/e3xzc
> curl https://api.myjson.com/bins/e3xzc
> curl https://api.myjson.com/bins/e3xzc > test.txt

对比
> curl https://api.myjson.com/bins/e3xzc
> curl https://raw.githubusercontent.com/7900ms/TestBase/master/JSON/1.json
> curl https://raw.githubusercontent.com/7900ms/TestBase/master/JSON/NotJSON1.json

> curl -i https://api.myjson.com/bins/e3xzc // Content-Type: application/json
> curl -i https://raw.githubusercontent.com/7900ms/TestBase/master/JSON/1.json // Content-Type: text/plain
> curl -i https://raw.githubusercontent.com/7900ms/TestBase/master/JSON/NotJSON1.json  // Content-Type: text/plain

说明：
1.在处理时， Content-Type: text/plain 一般是 就是这样的。不会专门给你用 “Content-Type: application/json”
2.在用别人的提供时，看清楚 别人提供的是 “Content-Type: application/json” 就很专业 .. 
3.在给别人提供时，看清楚 告知他人 是 “Content-Type: text/plain” 还是 “Content-Type: application/json”


2.
https://api.myjson.com/bins/hojm0

{
  "name": "Tom",
  "age": "12",
  "fullName": {
    "firstName": "Tom",
    "middleName": "Tulats",
    "lastName": "Lee"
  },
  "hobby": "play basketball"
}
http://myjson.com/hojm0
> https://api.myjson.com/bins/hojm0
> curl https://api.myjson.com/bins/hojm0
> curl https://api.myjson.com/bins/hojm0 > test.txt

3.
http://httpbin.org/get

4.
http://api.douban.com/v2/movie/top250
http://api.douban.com/v2/movie/top250?start=25&count=25
http://api.douban.com/v2/movie/top250?start=0&count=1

浏览器测试1 返回JSON or 无格式(纯文本)
1.
纯文本
https://raw.githubusercontent.com/7900ms/TestBase/master/JSON/NotJSON1.json
https://raw.githubusercontent.com/7900ms/TestBase/master/JSON/1.json
注意，这个是纯文本(有空格的)
> curl https://raw.githubusercontent.com/7900ms/TestBase/master/JSON/1.json

2.
https://raw.githubusercontent.com/7900ms/TestBase/master/JSON/NotJSON2.json
https://raw.githubusercontent.com/7900ms/TestBase/master/JSON/2.json




学习区：
更多代码填充、临时服务器建立 
typicode hotel // website development local dev suffix
typicode json-server

请求后返回一个json，可以自定义这个json 内容
https://www.v2ex.com/t/459569 # mock server, https://api.myjson.com/bins/hojm0 # 延迟的效果好
https://www.v2ex.com/t/365568 # 前端后端分离项目中的 mock-server, json-server

```
