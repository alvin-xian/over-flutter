## 一 图片引入方式

图片引入方式有多种：
- Image.asset:加载项目资源目录中的图片（相对路径）
- Image.network:网络资源图片
- Image.file:加载本地图片（绝对路径），跟包体无关。
- Image.memory: 加载Uint8List资源图片

```dart
    return MaterialApp(
      title: 'Image Widget',
      home: Scaffold(
        body: Center(
          child: Container(
            child: new Image.network(
              'https://cdn.jsdelivr.net/gh/flutterchina/website@1.0/images/flutter-mark-square-100.png',
              scale: 1.0,
            ),
          ),
        ),
      ),
    );
```

## 二 图片变形

根据图片的父级容器来，使用fit可以控制图片拉伸和挤压：
- BoxFit.fill:全图显示，图片会被拉伸，并充满父容器。
- BoxFit.contain:全图显示，显示原比例，可能会有空隙。
- BoxFit.cover：显示可能拉伸，可能裁切，充满（图片要充满整个容器，还不变形）。
- BoxFit.fitWidth：宽度充满（横向充满），显示可能拉伸，可能裁切。
- BoxFit.fitHeight ：高度充满（竖向充满）,显示可能拉伸，可能裁切。
- BoxFit.scaleDown：效果和contain差不多，但是此属性不允许显示超过源图片大小，可小不可大。  

##  三 图片的混合模式

图片混合模式（colorBlendMode）和color属性配合使用，能让图片改变颜色：
```dart
child:new Image.network(
  'https://cdn.jsdelivr.net/gh/flutterchina/website@1.0/images/flutter-mark-square-100.png',
    color: Colors.greenAccent,
    colorBlendMode: BlendMode.darken,
),
```

## 四 图片重复 repeat

- ImageRepeat.repeat : 横向和纵向都进行重复，直到铺满整个画布。
- ImageRepeat.repeatX: 横向重复，纵向不重复。
- ImageRepeat.repeatY：纵向重复，横向不重复。