## 一 flutter的网络请求

#### 1.0  两种请求方式

flutter的网络请求有两种方式：
- 使用Http请求
- 使用HttpClient请求

#### 1.1 Http请求方式

使用Http请求方式需要引入第三方包：http。
```
dependencies:
  flutter:
    sdk: flutter

  # The following adds the Cupertino Icons font to your application.
  # Use with the CupertinoIcons class for iOS style icons.
  cupertino_icons: ^0.1.2

  http:
```

设定点击按钮时发送请求：
```dart

// 引包
import 'package:http/http.dart' as http;

// 点击时触发请求
  onPressed: (){
          var url = 'https://www.baidu.com';
          http.get(url).then((response){
            print("状态： ${response.statusCode}");
            print("正文： ${response.body}");
          });
        },
```

点击后查看控制台输出。

#### 1.2 HttpClient请求方式

使用 HttpClient 方式请求时，需要导入io以及convert包。  

示例代码：
```dart
// 引包
import 'dart:convert';
import 'dart:io';

// 然后我们写一个发送请求的方法 getData
  void getData() async {
    try {

      Uri url = Uri.parse("https://www.baidu.com");

      // 发起请求
      HttpClient httpClient = new HttpClient();
      HttpClientRequest req = await httpClient.getUrl(url);

      // 等待返回数据
      HttpClientResponse res = await req.close();

      // 使用utf8.decoder 从 res中解析数据
      var data = await res.transform(utf8.decoder).join();

      // 输出响应头
      print(data);

      // 关闭请求客户端
      httpClient.close();

    } catch(e) {
      print("请求失败：$e");
    } finally {
      print("操作结束");
    }
  }

// 最后让按钮的点击触发该方法
 onPressed: getData,
```

#### 1.3 添加请求的查询

URI中可以直接添加查询参数：
```dart
Uri uri = Uri(
    scheme: "https",
    host: "www.baidu.com",
    queryParameters: {
        "id": 100021,
        "username": "lisi"
    }
);
```