## 一 容器组件 Conatainer

Container相当于web前端中的div，用于布局，常用属性有：
- Alignment：对child组件进行对齐
  - bottomCenter:下部居中对齐
  - botomLeft: 下部左对齐
  - bottomRight：下部右对齐
  - center：纵横双向居中对齐
  - centerLeft：纵向居中横向居左对齐
  - centerRight：纵向居中横向居右对齐
  - topLeft：顶部左侧对齐
  - topCenter：顶部居中对齐
  - topRight： 顶部居左对齐
- width
- height
- color
- padding：内边距
- margin：外边距
- decoration：容器的背景和边框
  - border：边框

```dart
    body:Center(
        child:Container(
            child:new Text(
                'Hello JSPang',
                style: TextStyle(fontSize: 40.0),),
                alignment: Alignment.center,
                // EdgeInsets.fromLTRB(value1,value2,value3,value4) 代表左上右下
                padding: const EdgeInsets.all(10.0), 
                decoration:new BoxDecoration(    // 渐变
                    gradient:const LinearGradient(
                    colors:[
                        Colors.lightBlue,Colors.greenAccent,Colors.purple
                    ],
                    border:Border.all(
                        width:2.0,
                        color:Colors.red
                    )
                )
            ),
        ),
    ),
```