# Configuration for xFace app

* 应用开发者必须正确在app.xml中配置需要的插件，形如

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
* 在新建`project/www/`下面，有一份app.xml模板供参考
