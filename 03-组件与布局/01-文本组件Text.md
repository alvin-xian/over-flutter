## 一 万物皆组件

在理解Dart时，需要用到Java当年的理念：“万物皆对象”，那么在flutter这个UI框架中，也需要这样理解：“万物皆组件”。  

常见组件有：
- Text：文本组件


## 二 文本组件 Text

Text属性：
- TextAlign: 对其方式，常见值有：
  - left
  - center
  - right
  - start: 开始处对其
  - end: 结尾处对其
- maxLines: 设置最多显示的函数
- overflow: 文本溢出时如何处理
  - clip: 溢出直接切断，剩余文字不会显示
  - ellipsis: 溢出部分显示省略号，常用
  - fade: 溢出部分进行上下渐变
- style: 属性极多，参照下列代码，或者参考网址https://docs.flutter.io/flutter/painting/TextStyle-class.html

```dart
          child: Text(
            'hello world hello world hello world hello world hello world hello world',
            textAlign: TextAlign.right,
            maxLines: 1,
            overflow: TextOverFlow.ellipsis,
            style: TextStyle(
                fontSize: 20.0,
                color: Color.fromARGB(255, 255, 100, 100),
                decoration: TextDecoration.underline,
                decorationStyle:TextDecorationStyle.solid,
            )
          ),
```