# Configuration for xFace

## 示例
```
<?xml version='1.0' encoding='utf-8'?>
<widget id="com.polyvi.xfaceapp" version="0.0.1" xmlns="http://www.w3.org/ns/widgets" xmlns:cdv="http://cordova.apache.org/ns/1.0">
    <preference name="AllowInlineMediaPlayback" value="false" />
    <preference name="AutoHideSplashScreen" value="false" />
    <preference name="BackupWebStorage" value="cloud" />
    <preference name="DisallowOverscroll" value="true" />
    <preference name="EngineVersion" value="3.2.0" />
    
    <feature name="LocalStorage">
        <param name="ios-package" value="CDVLocalStorage" />
    </feature>
    <feature name="AdvancedFileTransfer">
        <param name="ios-package" value="XAdvancedFileTransferExt" />
    </feature>
    <feature name="Calendar">
        <param name="ios-package" value="XCalendarExt" />
    </feature>
    <feature name="Messaging">
        <param name="ios-package" value="XMessagingExt" />
    </feature>
    <feature name="Umeng">
        <param name="ios-package" value="XUmengExt" />
        <param name="onload" value="true" />
        <preference name="UmengAppKey" value="533a174456240b022b073127" />
        <preference name="UmengReportPolicy" value="" />
        <preference name="UmengChannel" value="" />
    </feature>
    
    <pre_install_packages>
        <app_package id="com.polyvi.circle" name="com.polyvi.circle" />
    </pre_install_packages>
    
    <name>xface app</name>
    <description>
        A sample Apache xFace application that responds to the deviceready event.
    </description>
    <author email="dev@cordova.apache.org" href="http://cordova.io">
        xFace Team
    </author>
    <content src="index.html" />
    <access origin="*" />
</widget>
```
* xface直接引用[cordova config](http://cordova.apache.org/docs/en/3.4.0/config_ref_index.md.html#The%20config.xml%20File)的定义，请仔细阅读注意每一项的含义(本文档不重复cordova已有配置项)
* 使用CLI时，在新建`project/`下面，有一份config.xml模板供参考
* 应用开发者不用填写<feature>，只需要在app.xml中指定所用插件即可
## xFace 新增配置项
### Common
* EngineVersion

   `<preference name="EngineVersion" value="3.1.x" />`
   
   当前xFace版本号

### Android
* WorkDir
   配置应用工作目录设定策略，有效值是"1","2","3"。

   - `<preference name="WorkDir" value="3" />`
   - 1：仅手机内存 2：仅外部存储（FlashROM及SD/TF扩展卡） 3：外部存储优先
   - 默认值是*3*

### iOS
* Umeng

   ```
<preference name="UmengAppKey" value="533a174456240b022b073127" />
<preference name="UmengReportPolicy" value="" />
<preference name="UmengChannel" value="" />
   ```
   当且仅当使用umeng统计分析插件时有效，请参考[Umeng插件](http://gitlab.polyvi.com/xface/xface-extension-umeng/blob/dev/README.md)
   
* extra-lib

   ```
<preference name="LibRunningMode" value="optimized" />
<preference name="CustomLaunchImageFile" value="" />
   ```
   
   当且仅当使用extra-lib插件时有效，请参考[extra-lib插件](http://gitlab.polyvi.com/xface/xface-extra-lib/blob/dev/ios/doc/index.md)
