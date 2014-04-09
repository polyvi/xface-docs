# xFace 3.2.0

## 概述

xface 3.2.0 基于 Cordova 3.x开发，对结构进行了彻底调整，主要有以下几点重要变化

1. 直接完全集成Cordova源码，减少大量重复开发，并向社区标准靠近
2. 全新的架构，插件和引擎完全解耦，方便用户配置使用和打包
3. 全新的workflow，基于Cordova CLI开发的xface CLI，为开发者提供灵活的开发工具
4. 重新设计的打包系统，更加简洁

## 使用CLI的开发流程
[CLI guide](http://gitlab.polyvi.com/xface/xface-docs/blob/master/docs/cli.md)

## 传统开发方式
依然支持emulator + player的开发方式

## 资源
* [Plugin Server](http://plugins.polyvi.net:5984/) 查找可用插件以及id、version等信息
* [SDK](http://192.168.2.209:8081/)
* [xcps] ()


## 和xFace 3.1.x对比

1. navigator.network.connection.type 变更为 navigator.connection.type
[参考文档](http://192.168.2.209:8081/classes/cordova-plugin-network-information.html)

2. 使用Cordova file与filetransfer源码后，部分参数的含义有所变化，比如不再支持相对路径，请参考
[file plugin](https://github.com/apache/cordova-plugin-file/blob/master/doc/index.md)和[file-transfer plugin](
https://github.com/apache/cordova-plugin-file-transfer/blob/master/doc/index.md)

3. setting/local storage
   a. local storage在v31中是app隔离的，但v32中，是html5原生的，不区分app
   b. xface-extension-setting插件已经被废弃

4. Notification.confirm(string, function, string, string) is deprecated.  Use Notification.confirm(string, function, string, array).
参考[v32文档](
http://cordova.apache.org/docs/en/3.3.0/cordova_notification_notification.md.html#notification.confirm)和[v31](
http://apollo.polyvi.com/doc/xFaceSDK/classes/Notification.html#method_confirm)

5. navigator.splashscreen show与hide接口不再支持传入参数
参考[v32文档](
http://cordova.apache.org/docs/en/3.3.0/cordova_splashscreen_splashscreen.md.html#Splashscreen)和[v31](
http://apollo.polyvi.com/doc/xFaceSDK/classes/SplashSreen.html#method_hide)

6. StatusBar支持更多接口 
参考[v32文档](
https://github.com/apache/cordova-plugins/blob/master/statusbar/README.md)和[v31](
http://apollo.polyvi.com/doc/xFaceSDK/classes/StatusBar.html)

7. camera.getPicture cameraOptions支持更多参数
参考[v32文档](http://cordova.apache.org/docs/en/3.3.0/cordova_camera_camera.md.html#cameraOptions)和[v31](
http://apollo.polyvi.com/doc/xFaceSDK/classes/Camera.html#method_getPicture)

   **xFace v3.1 cameraOptions**
 [quality, destinationType, sourceType, targetWidth, targetHeight, encodingType, mediaType, allowEdit, correctOrientation, saveToPhotoAlbum, cropToSize]

   **xFace v3.2 cameraOptions**
[quality, destinationType, sourceType, targetWidth, targetHeight, encodingType, mediaType, allowEdit, correctOrientation, saveToPhotoAlbum, *popoverOptions, cameraDirection, cropToSize*]

8. 不再支持xFace.AMS.closeApplication()接口，关闭应用请调用xFace.app.close()

9. ams/security/zip/advanced-file-transfer 等插件不再仅限于相对路径，增加对绝对路径（以“/”或“file://”开头）以及cdvfile://localhost/<filesystemType>/<path to file>的支持。
也就是说，支持以下形式的路径：

   a. 相对app workspace的相对路径，例如："myPath/test.file"
   b. 以“/”开头的绝对路径，例如："/myPath/..."
   c. file://协议URL，例如："file:///myPath/..."
   d. cdvfile://localhost/\<filesystemType>/\<path to file>

   注意：

   * v3.1.x “**/**package.file” 的含义为**相对路径**（相对app workspace）
   * v3.2.0 “**/**package.file” 的含义为**绝对路径**

## 应用开发需要注意的新变化
* [app.xml](http://gitlab.polyvi.com/xface/xface-docs/blob/master/docs/appxml.md)
* [config.xml](http://gitlab.polyvi.com/xface/xface-docs/blob/master/docs/config.md)
* file plugin的变化较大，请仔细阅读[文档](http://gitlab.polyvi.com/xface/cordova-plugin-file/blob/master/doc/index.md)