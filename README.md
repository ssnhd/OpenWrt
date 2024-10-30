# OpenWrt 常见疑问


---
## 安装 iStoreOS

1. Mac 电脑安装 [balenaEtcher](https://etcher.balena.io/) 软件
2. 下载 [iStoreOS](https://fw.koolcenter.com/iStoreOS/x86_64_efi/) 固件
3. 打开 balenaEtcher，从文件烧录选择刚下载好的 iStoreOS 固件，再选择 U 盘，最后点击**现在烧录**
4. 将 U 盘插上路由器，开机按 Delete 键进入 BIOS，选择 U 盘启动，保存并重启
5. 显示屏上代码跑完，输入 `quickstart` 回车键
6. 选择第二项「Instal1 X86」，回车键
7. 选择硬盘、清除硬盘分别回车键
8. 开始将 U 盘上的内容克隆到路由器硬盘
9. 拔下 U 盘，重启。

**老毛桃 PE**
1. Windows 安装[老毛桃](https://www.laomaotao.net/)
2. 将 U 盘插上电脑，打开老毛桃制作 U 盘启动器
3. 制作好后，将 OpenWrt 固件和 IMG 写盘工具存到 U 盘根目录
4. 将 U 盘插上路由器，开机按 Delete 键进入 BIOS，选择 U 盘启动，保存并重启
5. 清除路由器硬盘并保存
6. 打开我的电脑里 IIMG写盘工具，选择路由器硬盘，选择固件开始写入
7. 好了后重启，拔下 U 盘。

## 删除 OpenWrt 登录密码
1. 打开 OpenWrt 终端，输入 `root` 回车键
2. 输入路由器密码，回车键
3. 输入 `passwd -d root` 回车键

## 恢复出厂设置
1. 进入 OpenWrt 后台，输入 `root` 回车后输入密码
2. 输入 `firstboot` 回车键
3. 输入 `reboot` 回车键

## 查看网口型号
1. 打开 OpenWrt 终端，输入 `root` 回车键
2. 输入路由器密码，回车键
3. 输入 `lspci -nn | grep Ethernet`
4. 会出现下面代码即网口型号（几个网口就出现几列）
```
01:00.0 Ethernet controller [0200]: Intel Corporation Ethernet Controller I225-V [8086:15f3] (rev 03)
02:00.0 Ethernet controller [0200]: Intel Corporation Ethernet Controller I225-V [8086:15f3] (rev 03)
03:00.0 Ethernet controller [0200]: Intel Corporation Ethernet Controller I225-V [8086:15f3] (rev 03)
04:00.0 Ethernet controller [0200]: Intel Corporation Ethernet Controller I225-V [8086:15f3] (rev 03)
```

你也可以输入 `ethtool -i eth0` 来查看单个网口型号，其中 `eth0` 是您想要查看的网卡的名称。
```
driver: igc
version: 5.10.176
firmware-version: 
expansion-rom-version: 
bus-info: 0000:01:00.0
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes
supports-priv-flags: yes
```
