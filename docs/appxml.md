# Configuration for xFace app
## 示例
在新建`project/www/`下面，有一份app.xml模板供参考

```
<?xml version="1.0" encoding="utf-8"?>
<widget id="helloxface" version="2.0" xmlns="http://www.w3.org/ns/widgets">

  <name short="helloxface">helloxface</name>
  <icon src="icon.png" />
  <content encoding="UTF-8" src="index.html" />

  <preference name="type" readonly="true" value="xapp" />
  <preference name="mode" readonly="true" value="local" />

  <description>
      A sample widget to demonstrate some of the possibilities.
  </description>

  <author email="foo-bar@polyvi.com/" href="http://polyvi.com/">polyvi</author>

  <license> Copyright 2012-2014, Polyvi Inc. </license>

</widget>
```
## 配置项
* `type` 指定xface app类型，有效值为
   * `xapp`  xface web app
   * `napp`  xface native app，[参见](http://polyvi.github.io/openxface/guide/xFace/ams/xface_ams_native_apps.html)
* `mode` 指定xapp的运行模式，当且仅当type为xapp时有效，有效值为
   * `local` 本地模式，app在客户端本地
   * `online` 在线模式，app部署在服务器，[参见](http://polyvi.github.io/openxface/guide/xFace/ams/xface_online_app_en.html)
* `plugins` 应用开发者必须正确在app.xml中配置需要的插件，形如

```
<plugins>
    <plugin id="org.apache.cordova.contacts"/>
    <plugin id="org.apache.cordova.device"/>
    <plugin id="org.apache.cordova.statusbar"/>
    <plugin id="org.apache.cordova.network-information"/>
    <plugin id="org.apache.cordova.console"/>

    <plugin id="com.polyvi.xface.extension.security"/>
    <plugin id="com.polyvi.xface.extension.uppay"/>
    <plugin id="com.polyvi.xface.extension.calendar"/>
    <plugin id="com.polyvi.xface.extension.telephony"/>
</plugins>
```
* `access`，指定app可访问的域名白名单，不指定则为无限制，[参见](http://cordova.apache.org/docs/en/3.4.0/guide_appdev_whitelist_index.md.html#Whitelist%20Guide)