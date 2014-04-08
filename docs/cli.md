# xFace CLI
## 安装
* 需要安装Android或iOS SDK
* 需要安装[NodeJS](http://nodejs.org/)
* `$ npm install -g xface`

## 使用
```
# 创建xface app project
$ xface create helloxface com.polyvi.helloxface HelloxFace

# 添加支持的平台
$ cd helloxface
$ xface platform add android

# 添加需要的plugin
$ xface plugin search device    # 查找插件是否存在并获得id
$ xface plugin add org.apache.cordova.device
$ xface plugin add com.polyvi.extension.zip

# 开发app, app位于helloxface/www

# 测试
$ xface emulate android
$ xface run android
```

可以使用参数`-d`显示debug信息，帮助错误诊断

## 开发App
xface默认在`yourproject/www`下生成一个app模版，开发者只需要修改该模版app或者放入、编辑自己的app即可。CLI会自动把这里的app添加到最终生成的可执行文件包中。

## 文档 
* xface-cli基于cordova-cli，兼容cordova-cli所有常用接口，**请必须先阅读它的[文档](http://cordova.apache.org/docs/en/3.4.0/guide_cli_index.md.html#The%20Command-Line%20Interface)**
* 使用命令行帮助，在命令行中直接键入`xface`或`xface help`回车即可
