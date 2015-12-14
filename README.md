UMeng-OnlineConfig-iOS
==================
这是一个[友盟在线参数](http://dev.umeng.com/online-parameters/ios-doc--2/intergration)组件SDK的非官方镜像。

官方集成指南请参照[http://dev.umeng.com/online-parameters/ios-doc--2/intergration](http://dev.umeng.com/online-parameters/ios-doc--2/intergration)。

## 使用CocoaPods安装
[CocoaPods](http://cocoapods.org) 是开发 OS X 和 iOS 应用程序的一个第三方库的依赖管理工具。利用 CocoaPods，可以自动化安装第三方库。

要使用友盟用户反馈组件SDK，推荐这样配置Podfile:

```ruby
# The front repo is prior if conflicted
# CocoaPods private repo
source 'https://github.com/jcccn/PodSpecs.git'
# CocoaPods master repo
source 'https://github.com/CocoaPods/Specs.git'

platform :ios,'7.0'

# ignore all warnings from all pods
inhibit_all_warnings!

pod 'UMOnlineConfig'

```

也可以这样配置Podfile:

```ruby
# CocoaPods master repo
source 'https://github.com/CocoaPods/Specs.git'

platform :ios,'7.0'

# ignore all warnings from all pods
inhibit_all_warnings!

pod 'UMOnlineConfig', :git => 'https://github.com/jcccn/UMeng-OnlineConfig-iOS.git'

```

## 使用说明
在AppDelegate.m文件的 `- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions`方法中添加如下代码来请求更新参数：

```objective-c
[UMOnlineConfig updateOnlineConfigWithAppkey:(NSString *)key];
```

`key` 是友盟统计的appKey.

在线参数需要事先在网站上添加，上面这句代码从服务器获取参数，并缓存本地。

当在项目里需要获取某个具体参数时调用

```objective-c
[UMOnlineConfig getConfigParams:@"xxxx"];
```

xxxx为友盟服务器上事先设置好的参数id。如果你想获取所有的在线参数，请使用:

```objective-c
[UMOnlineConfig getConfigParams];
```
这两个方法都是从 `[NSUserDefaults standardUserDefaults]` 获取缓存的值， 所以上面的 `[UMOnlineConfig updateOnlineConfigWithAppkey:]` 方法要先在app启动时被调用。

详细的功能使用，请参考[官方文档](http://dev.umeng.com/online-parameters/ios-doc--2/intergration)。
