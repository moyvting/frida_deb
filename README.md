# frida_deb
高版本frida在低版本ios中会出现无法安装情，出现错误提示
```
dpkg-deb --control subprocess returned error exit status 2
Sub-process /usr/libexec/cydia/cydo returned an error code (1)
```
此时根据如下链接可进行修复
https://github.com/frida/frida/issues/2355

此处安放修复包，用以以后使用

修复代码如下

下载frida_16.0.8_iphoneos-arm.deb 后运行如下代码
```
mkdir frida_16.0.8_iphoneos-arm
cd frida_16.0.8_iphoneos-arm
ar -x ../frida_16.0.8_iphoneos-arm.deb
zstd -d *.zst
xz *.tar
ar r frida_16.0.8_iphoneos-arm-repacked.deb debian-binary control.tar.xz data.tar.xz
```
将打包好的deb转移到手机中，运行如下代码。
```
dpkg -i frida_16.0.8_iphoneos-arm-repacked.deb
```
