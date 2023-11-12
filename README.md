# eaidk-610

详见[发布页](https://github.com/Lasius-alienus/eaidk-610/releases/ "发布页")

- Debian系统可以通过RKDev Tools(包含在[releases](https://github.com/Lasius-alienus/eaidk-610/releases/download/Debian "releases")内)刷入emmc，也可以直接使用[balenaEtcher](https://etcher.balena.io/#download-etcher "balenaEtcher")刷入SD卡启动(emmc须存在可用主线u-boot)。

特性:
1. 驱动所有USB-A(第一次启动只能驱动usb2.0，使用'apt update && apt upgrade'更新完成后即可以使用)。
1. panforst驱动GPU，mali-t864性能基本发挥到极限。
1. CPU大核超频到2.2GHz，小核超频到1.8GHz，需要使用风冷散热或更换散热片，否则使用`armbian-config`修改到较低频率。
1. 使用6.1.50版本内核，可以随armbian主线更新kernel。
1. 预先替换了清华大学开源软件镜像源。
1. '/root/'下包含了一些软件包，如'FreeCAD'，'VeraCrypt'和'Telegram'，使用'sudo dpkg --install /root/*.deb'来安装它们。

缺陷:
1. 没有驱动type-c(不能确定的问题，dts大概率可用)。
1. 没有驱动3.5mm耳机孔。
1. 没有驱动原装mipi屏幕。
1. 等待反馈。

说明:
使用armbian官方镜像替换dtb制成，有问题在这里反馈。
默认账号`root`，密钥`1234`。

修改内容:
更换了一个来自armbian(5.15.y)官方提供的dts，修改后编译得到的dtb。
修改了`systemd-modules-load.service`这一服务的超时时间为`5s`，如果第一次启动不正常改到`10s`，之后的启动一般而言`5s`是能够正常启动的，如果不改启动会在这里卡`90s`。

- ubuntu系统可以通过RKDev Tools(包含在压缩包内)刷入emmc，也可以直接使用[balenaEtcher](https://etcher.balena.io/#download-etcher "balenaEtcher")刷入SD卡启动(emmc须存在可用主线u-boot)。

特性:
1. 驱动所有USB-A。
1. panforst驱动GPU，mali-t864性能基本发挥到极限。
1. CPU大核超频到2.2GHz，小核超频到1.8GHz，需要使用风冷散热或更换散热片，否则使用`orangepi-config`修改到较低频率。
1. 开机有跑码，不急。

缺陷:
1. 没有驱动type-c(貌似是内核源码问题，dts大概率可用)。
1. 没有驱动3.5mm耳机孔。
1. 没有驱动原装mipi屏幕。
1. 等待反馈。

说明:
使用orangepi官方镜像替换dtb制成，有问题在这里反馈。
默认账号`orangepi`，密钥`orangepi`。

修改内容:
更换了一个来自armbian(5.15.y)官方提供的dts，修改后编译得到的dtb。
修改了`systemd-modules-load.service`这一服务的超时时间为`5s`，如果第一次启动不正常改到`10s`，之后的启动一般而言`5s`是能够正常启动的，如果不改启动会在这里卡`90s`。
###通过apt更新系统后需要重新添加`timeoutstart`项目为`5s`，如果在更新时没有选择更新文件则忽略此条。

- manjaro系统只能使用[balenaEtcher](https://etcher.balena.io/#download-etcher "balenaEtcher")刷入SD卡启动(在emmc存在上面的ubuntu系统时是可以启动的，别的未测试)。

特性:
1. 驱动所有USB-A。
1. panforst驱动GPU，且使用6.1.y内核，mali-t864性能基本发挥到极限(比ubuntu更强)。
1. CPU大核超频到2.2GHz，小核超频到1.8GHz，需要使用风冷散热或更换散热片，改频率的方法不好使，自己想办法或者拿嘴吹。
1. 蓝牙可以连接音响，且声音正常。

缺陷:
1. 没有驱动type-c(同上)。
1. wifi好像不可用(要插网线使用)。
1. 没有驱动3.5mm耳机孔。
1. 没有驱动原装mipi屏幕(manjaro不给dts，反编译的我只能说尽量改)。
1. 等待反馈。

说明:
使用manjaro官方镜像替换dtb制成，有问题在这里反馈。
manjaro官方没有说支持eaidk-610，但打开`dtbs`文件夹你会发现惊喜。

修改内容:
更换了一个添加了`opp`挡位的dts，修改后编译得到的dtb。
修改了`systemd-modules-load.service`这一服务的超时时间为`5s`，如果第一次启动不正常改到`10s`，之后的启动一般而言`5s`是能够正常启动的，有的时候manjaro开机慢，保险起见可以改到`10s`，如果不改启动会在这里卡`90s`(manjaro启动不跑码，急死你)。
