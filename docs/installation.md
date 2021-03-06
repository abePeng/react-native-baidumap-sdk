# 安装说明
该项目在 release 分支做了新项目的编译测试：[![build status][build-badge]][build]，可以作为参考。

## 引入项目
```bash
npm i react-native-baidumap-sdk
```
或
```bash
yarn add react-native-baidumap-sdk
```

## 配置

### Android
```bash
react-native link react-native-baidumap-sdk
```
[获取 Android 开发密钥](http://lbsyun.baidu.com/index.php?title=iossdk/guide/create-project/ak)，
在 AndroidManifest 中添加：
```xml
<application>
    <meta-data
      android:name="com.baidu.lbsapi.API_KEY"
      android:value="开发密钥" />
</application>
```

### iOS
暂时只提供 cocoapods 配置方式。

在 `ios` 目录下新建文件 `Podfile`：

```ruby
platform :ios, '8.0'

target '...' do
  pod 'yoga', path: '../node_modules/react-native/ReactCommon/yoga'
  pod 'React', path: '../node_modules/react-native', :subspecs => [
    'DevSupport',
  ]
  pod 'react-native-baidumap-sdk', path: '../node_modules/react-native-baidumap-sdk/lib/ios'
end
```

然后运行：
```bash
pod install
```

## 初始化（重要！！）
**在使用 react-native-baidumap-sdk 的组件、模块之前一定要初始化。未初始化可能导致应用崩溃，而初始化失败则会导致地图无法显示。**

其中 iOS 需要提供密钥（Android 密钥已经且只能写在 Manifest），当然，你也可以用官方提供的方法进行初始化。

[获取 iOS 开发密钥](http://lbsyun.baidu.com/index.php?title=iossdk/guide/create-project/ak)。

```javascript
import { Initializer } from 'react-native-baidumap-sdk'

Initializer.init('iOS 开发密钥').catch(e => console.error(e))
```

android 下会自动忽略 init 的参数，如果应用只支持 android 则可以不带参数。

[build-badge]: https://travis-ci.org/qiuxiang/react-native-baidumap-sdk.svg?branch=release
[build]: https://travis-ci.org/qiuxiang/react-native-baidumap-sdk
