# Configuration for xFace app
app.xml描述xface application的属性和配置，每一个app必须包含一份有效的app.xml
## 示例
在新建`project/www/`下面，有一份app.xml模板供参考

```
<?xml version='1.0' encoding='UTF-8'?>

    <!-- id: 应用的唯一标识符, version: 应用的版本号 -->
    <widget id="com.polyvi.myapp" version="2.0" xmlns="http://www.w3.org/ns/widgets">

        <!-- short: 应用名称的简称, 值: 应用的名称 -->
        <name short="MXA">myxFaceApp</name>

        <!-- src: 应用的图标地址, 相对app根目录路径 -->
        <icon src="icon.png" />

        <!-- src: 应用的入口地址, 不同类型的应用设置不一样
             1.web app类型
                 local app 的取值: 相对app根目录路径
                 web app 的取值: 应用所在服务器的地址的绝对路径
             2.native app类型
                 Android 的取值: apk的package id
                 iOS 的取值: ipa的custom scheme URL -->
        <content encoding="UTF-8" src="index.html" />

        <!-- type: 应用的类型
             value: xapp (表示web app类型); napp (表示native app类型) -->
        <preference name="type" readonly="true" value="xapp" />

        <!-- mode: 应用的部署策略, 该项仅在type属性为"xapp"时有效
             value: local 应用及其资源部署在客户端
                    online 应用及其资源部署在服务器 -->
        <preference name="mode" readonly="true" value="local" />

        <!-- engine: 引擎最低版本的要求
             value: 引擎版本号 -->
        <preference name="engine" readonly="true" value="3.1.0" />

        <!-- plugins: 用于配置应用所需的插件 -->
        <plugins>
            <!-- id: 插件的唯一标识符
                 version: 插件的版本号(如果不写，如第二项plugin标签，则默认是最新版本) -->
            <plugin id='org.apache.cordova.contacts' version='1.0.1'/>
            <plugin id='com.polyvi.xface.extension.ams'/>
        </plugins>

        <description>
            A sample widget to demonstrate some of the possibilities.
        </description>
        <author email="foo-bar@polyvi.com/" href="http://polyvi.com/">polyvi</author>
        <license> Copyright 2012-2013, Polyvi Inc. </license>

    </widget>
```
## 配置项
* `content` 应用的入口地址, 不同类型的应用设置不一样

   1. web app类型

      local app 的取值: 相对app根目录路径

      web app 的取值: 应用所在服务器的地址url

   2. native app类型

      Android 的取值: apk的package id

      iOS 的取值: ipa的custom scheme URL

* `type` 指定xface app类型，有效值为
   * `xapp`  xface web app
   * `napp`  xface native app，[参见](http://polyvi.github.io/openxface/guide/xFace/ams/xface_ams_native_apps.html)
* `mode` 指定xapp的部署策略，当且仅当type为xapp时有效，有效值为
   * `local` 本地模式，app部署在客户端本地
   * `online` 在线模式，app部署在服务器，[参见](http://polyvi.github.io/openxface/guide/xFace/ams/xface_online_app_en.html)
* `plugins` 应用开发者必须正确在app.xml中配置需要的插件，形如

   ```
<plugins>
    <plugin id="org.apache.cordova.contacts"/>
    <plugin id="org.apache.cordova.device"/>
    <plugin id="org.apache.cordova.statusbar"/>
    <plugin id="com.polyvi.xface.extension.security"/>
    <plugin id="com.polyvi.xface.extension.uppay"/>
</plugins>
   ```
* `access`，指定app可访问的域名白名单，不指定则为无限制，[参见](http://cordova.apache.org/docs/en/3.4.0/guide_appdev_whitelist_index.md.html#Whitelist%20Guide)