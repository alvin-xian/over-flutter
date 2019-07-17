## 一 flutter简介  

flutter是谷歌开源的移动UI框架，用于在iOS和Andorid上构建高质量的**原生**用户界面。flutter基于谷歌开发的dart语言构建。  

博主认为的flutter最大卖点：
- 跨平台：其跨平台完全不同于当前的两种成熟实现方式：ionic（移动端内嵌chrome），reactnative（js桥接，将前端view生成为原生view），flutter由自己实现GDI，GPU渲染：使用GPU渲染方式，官方说法是可达120fps。

## 二 fluttter环境安装

#### 2.0 基础环境要求

在配置flutter环境之前，需要安装java、git环境。  

注意：mac需要提前安装 Xcode 7.2 或者以上版本。  

flutter下载地址：https://flutter.dev/docs/development/tools/sdk/releases 

#### 2.1 win安装

前奏：由于flutter等工具下载时会遇到网络问题，推荐使用一些镜像：
```
export PUB_HOSTED_URL=https://pub.flutter-io.cn
export FLUTTER_STORAGE_BASE_URL=https://storage.flutter-io.cn
```

步骤一：解压安装，配置环境
```
# 解压安装:将下载的win版本flutter安装包解压到 C:\Dev\flutter

# 配置环境变量：将flutter命令配置为全局使用

# 测试flutter
flutter -h          # 需要时间较长                                              
```

步骤二：检测环境
```
flutter doctor      # 检测flutter环境命令

# 根据 检测要求进行缺失环境安装，比如安装证书：
flutter doctor --android-licenses
```

步骤三：AndroidStudio安装，这是目前最好的flutter开发工具，https://developer.android.com/
```
# 安装flutter插件：打开AndroidStudio--Preference--Plugins--搜索flutter---install即可

# 启动AndroidStudio，并 create a new  flutter project，注意此时会去下载谷歌gradle，速度极慢，耐心等待，失败后反复试验

```

#### 2.2 mac安装

前奏：由于flutter等工具下载时会遇到网络问题，推荐使用一些镜像：
```
export PUB_HOSTED_URL=https://pub.flutter-io.cn
export FLUTTER_STORAGE_BASE_URL=https://storage.flutter-io.cn
```

步骤一：解压安装，配置环境
```
# 解压安装
cd ~                                                            # 假设安装在该用户目录下
unzip ~/Downloads/flutter_macos_v1.2.1-stable.zip               # flutter安装包下载位置

vim ~/.bash_profile
# 添加
export PUB_HOSTED_URL=https://pub.flutter-io.cn                 # 国内用户需要设置
export FLUTTER_STORAGE_BASE_URL=https://storage.flutter-io.cn   # 国内用户需要设置
export PATH=~/flutter/bin:$PATH

source ~/.bash_profile

# 注意，如果使用的是zsh，需要 vim ~/.zshrc，添加上述命令，添加：source ~/.bash_profile

# 测试安装是否成功
flutter -h          # 需要时间较长                                              
```

步骤二：检测环境
```
flutter doctor      # 检测flutter环境命令

# 根据 Android toolchain 一栏要求执行下列命令：
flutter doctor  --android-licenses

# 根据 iOS toolchain 一栏以下的提示依次安装缺失组件
```

步骤三：AndroidStudio安装，这是目前最好的flutter开发工具，https://developer.android.com/
```
# 安装flutter插件：打开AndroidStudio--Preference--Plugins--搜索flutter---install即可

# 启动AndroidStudio，并 create a new  flutter project，注意此时会去下载谷歌gradle，速度极慢，耐心等待，失败后反复试验

```

## 三 运行flutter项目

如果想要使用iOS虚拟机，那么你的电脑必须是MacOS，在AS软件上直接可以启动iOS虚拟机（因为你已经安装了Xcode）  

如果想要使用安卓虚拟机，无论是mac，还是win，都需要安装AVD虚拟机：
```
# 点击Android Studio中的上方菜单tool -AVD Manager选项。出现新建菜单，选择Create Virtual Device.....依次走下去即可
```

步骤五：运行flutter工程
```
# 点击debug按钮，让Flutter程序跑起来，或者直接点击 run 按钮，其实是执行：flutter run
```

## 四 flutter更新

升级flutter命令：
```
flutter upgrade
```

如果只想升级依赖，而不升级flutter：
```
flutter packages get        # 获取pubspec.yaml文件中列出的所有依赖包
flutter packages upgrade    # 获取pubspec.yaml文件中列出的所有依赖包的最新版本
```

如果想切换flutter的分支：
```
# 可以在pubspec.yaml文件中指定Flutter SDK的依赖项,例如，以下代码片段指定flutter和flutter_test包使用Flutter SDK。

name: hello_world
dependencies:
  flutter:
    sdk: flutter
dev_dependencies:
  flutter_test:
    sdk: flutter
```

贴士：  
不要使用pub get或pub upgrade命令来管理你的依赖关系。相反，应该使用flutter packages get或flutter packages upgrade。如果您想手动使用pub，则可以通过设置FLUTTER_ROOT环境变量来直接运行它。

## 五 一些错误贴士

出现：`Waiting for another flutter command to release the startup lock.`解决：
```
# 杀死一切dart进程
# 删除(your_flutter_directory/flutter/bin/cache/lockfile)
# 重启 AS
```