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
```
范例1 - Python Requests
r = requests.get('https://api.github.com/events')
r.text (utf-8) 或 r.content(二进制)
参考
python下载文件的三种方法 https://blog.csdn.net/AaronWu2012/article/details/52565151 # requests 
https://blog.csdn.net/xie_0723/article/details/51361006 # utf-8 或 二进制
http://docs.python-requests.org/zh_CN/latest/user/quickstart.html

范例1 - Java 自定义类 Request request 
request.getResponseTextFromURL("http://w.com");
用法
public class DataBunch {
    public int tmpTick;
    public Dataset dataset;

    public DataBunch(){
        this.tmpTick = 0;
        this.dataset = new Dataset();
    }
    public static class Dataset {
        public java.util.List<String> urls;
        public java.util.List<String> results;
        private Request request;

        public dataset(){
            this.urls = new ArrayList<String>();
            this.results = new ArrayList<String>();

            this.urls.add("https://api.myjson.com/bins/hojm0");
            this.urls.add("https://api.myjson.com/bins/we414");
            this.urls.add("https://api.myjson.com/bins/we41z");
            this.urls.add("https://api.myjson.com/bins/we4s3");
            this.urls.add("https://api.myjson.com/bins/we4se");
        }
        public void fill(){
            for (int i = 0; i < urls.size(); i++) {
                String result = this.request.getResponseTextFromURL(this.urls[i]);
                this.results.add(result);
            }
        }
        public void getResults(){
            for (int i = 0; i < results.size(); i++) {
                System.out.println(results[i]);
            }
        }
    }
}

关于 Request 类
显然是 一个封装了的类，可以直接用 
String url = "http://w.com";
String result = this.request.getResponseTextFromURL(url); // 会卡进程，所以 最好 如果做写入 在新进程里做 写入 (类似 多线程 共享一个变量：一个线程，修改了 一个 list实例，另一个线程访问到 这种修改
一个 list 实例，在一个线程的修改(list.addItem)，可以被，另一个线程访问到 已更新的list )

自定义的 Request 类，是封装了一个用于 get URL content 的类。以下是 Java 里用于 get URL content 的类：
1. java.net.HttpURLConnection，这是一个用于 get URL content 的类 👍🏽
HttpURLConnection 继承自 URLConnection (URLConnection or HttpURLConnection)
基于它们自己 "封装" 就行了。主要是类似
HttpURLConnection con
con.getInputStream
con.setConnectTimeout(30000);  
con.setReadTimeout(30000);  
G HttpURLConnection or URLConnection
* https://developer.android.com/reference/java/net/HttpURLConnection
Android 6.0(API 23) SDK后，Android的网络请求强制使用HttpUrlConnection，并且SDK中也移除了 HttpClient 库，同时也移除了SSL 和Notification的setLatestEventInfo方法
https://www.jianshu.com/p/2910114bb78b # 使用URL直接读取网络资源，使用URLConnection提交Get请求或Post请求

HttpURLConnection 网络超时异常 (返回空字符，重新开始一个获取)
https://segmentfault.com/q/1010000000604508
https://zhuanlan.zhihu.com/p/24723946
http://unirest.io/java.html # Unirest.setTimeouts(long connectionTimeout, long socketTimeout);

2. java.net.URL ，通过 java.net.URL 来获取资源
http://www.runoob.com/java/java-url-processing.html
https://stackoverflow.com/questions/1359689/how-to-send-http-request-in-java/17639826#17639826

3. HttpClient，这是 Android SDK 自带的用于 get URL content 的类 
HttpClient 相比 “传统 JDK 自带的 HttpURLConnection”，增加了易用性和灵活性 (然而 'Apache HTTPClient' 已经过时了!!)。但是 需要引入 
https://blog.csdn.net/wangpeng047/article/details/19624529 
Apache HttpComponents 
https://stackoverflow.com/questions/1359689/how-to-send-http-request-in-java/1359723#1359723 
https://www.jianshu.com/p/2910114bb78b # 'Apache HTTPClient' 已经过时了 

* HttpURLConnection is over than 'Apache HTTPClient'
从 HttpClient 切换到 HttpURLConnection 
https://blog.csdn.net/fengyuzhengfan/article/details/49253073
https://stackoverflow.com/questions/9551058/urlconnection-or-httpclient-which-offers-better-functionality-and-more-efficie/15524143#15524143 


G python requests text java
https://stackoverflow.com/questions/9600327/is-there-an-equivalent-to-pythons-request-module-in-java-for-working-on-rest-ba
https://stackoverflow.com/questions/1359689/how-to-send-http-request-in-java
(HttpUrlConnection or HttpClient)


```
