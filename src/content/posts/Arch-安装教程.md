---
title: Arch 安装教程
published: 2024-02-15 12:15:51
tags: [arch]
author: yuechu
---

# arch安装教程+部分问题解决

#### 网络配置

```
# 进入iwctl
iwctl

# 获取device名称 我这里是 wlan0，后面注意wlan0替换成你自己device
device list 

# 扫描附近wifi
station wlan0 scan

# 获取所有可连接wifi名字
station wlan0 get-networks
station wlan0 connect [wifi名]

#输入密码
# ctrl+c 退出 iwctl
```

#### 硬盘分区

```shell
cfdisk /dev/sda
```

选择gpt，然后new新建efi分区，300~500M类型是EFI

4G类型是swap，剩下的空间全部new为默认，然后选择write，输入yes完成写入，然后退出

![](https://img.yuechucard.space/blog/arch/1.png)

输入

```shell
lsblk -f
```

![](https://img.yuechucard.space/blog/arch/2.png)

出现三个sda即为成功

#### 格式化

```shell
mkfs.ext4 /dev/sda3 //格式化sda3
```

```
mkswap /dev/sda2
```

```
mkfs.fat -F 32 /dev/sda1
```

![](https://img.yuechucard.space/blog/arch/3.png)

#### 挂载

```
mount /dev/sda3 /mnt
```

```
mount --mkdir /dev/sda1 /mnt/boot
```

```
swapon /dev/sda2
```

#### 安装

```
pacstrap -K /mnt base linux linux-firmware base-devel
```

#### 挂载信息载入系统

```shell
genfstab -U /mnt >> /mnt/etc/fstab
```

#### 进入创建的系统

```
arch-chroot /mnt
```

![](https://img.yuechucard.space/blog/arch/4.png)

#### 设置时区

```shell
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
```

#### 对准时间

```shell
hwclock --systohc
```

#### 下载nano也可以使用vim

```shell
pacman -S nano
```

#### 切换到etc目录使用nano编辑locale.gen文件来设置语言

```shell
cd /etc
nano locale.gen
```

![](https://img.yuechucard.space/blog/arch/5.png)

#### 将en_US.UTF-8 UTF-8前面的#去掉

![](https://img.yuechucard.space/blog/arch/6.png)

ctrl+o保存ctrl+x退出

#### 加载配置

```shell
locale-gen
```

##### 创建locale.conf

```shell
touch locale.conf
```

##### 编辑locale.conf(编辑时会自动创建所以不执行上一条也行)

```shell
nano locale.conf
```

输入

```shell
LANG=en_US.UTF-8
```

ctrl+o保存ctrl+x退出

#### 设置用户

##### 设置root密码(输入时密码不可见，输就完事了不用担心，要输入两次)

```shell
passwd
```

![](https://img.yuechucard.space/blog/arch/7.png)

##### 新建用户(***表示你想起的用户名)

```
useradd -m ***
```

##### 设置密码(***表示你想起的用户名)

```
passwd ***
```

##### 管理权限

```shell
nano sudoers
```

##### 在root那一行输入(***表示你上面所设置的用户名)

```
*** ALL=(ALL) ALL
```

![](https://img.yuechucard.space/blog/arch/8.png)

ctrl+o保存ctrl+x退出

##### 编辑hostame然后输入一个名字保存

```shell
nano hostname
```

![](https://img.yuechucard.space/blog/arch/9.png)

ctrl+o保存ctrl+x退出

#### 更新一下

```
pacman -Sy
```

#### 安装os-prober

```shell
pacman -S grub efibootmgr os-prober
```

##### 返回根目录

```shell
cd /
nano /etc/default/grub
```

##### 取消最后一行注释

![](https://img.yuechucard.space/blog/arch/10.png)

#### 安装grub

```shell
grub-install --target=x86_64-efi --efi-directory=boot --bootloader-id=grub
```

##### 生成配置文件

```shell
grub-mkconfig -o /boot/grub/grub.cfg
```

##### 网络配置

```shell
pacman -S networkmanager
```

##### 开机自启动

```
systemctl enable NetworkManager
```

##### 退出并重启

```shell
exit
reboot
```

安装成功！！！

![](https://img.yuechucard.space/blog/arch/11.png)

# 安装KDE

输入用户名：root

密码是你设置的且输入时不可见

![](https://img.yuechucard.space/blog/arch/12.png)

更新一下库

```shell
pacman -Sy
```

#### 安装KDE（根据提示按回车和输入y）

```shell
pacman -S sddm xorg plasma konsole kate filelight dolphin ark
```

安装完成后reboot重启即可进入KDE

根据图示进入终端

![](https://img.yuechucard.space/blog/arch/13.png)

```shell
sudo pacman -Sy
#然后输入密码
sudo pacman -S neofetch
neofetch
```

![](https://img.yuechucard.space/blog/arch/14.png)

安装完成

# Xshell远程连接

```shell
pacman -Sy
pacman -S openshh
nano /etc/ssh/sshd_config  #修改下图内容
```

![](https://img.yuechucard.space/blog/arch/15.png)

#### 设置开机启动

```
systemctl enable sshd.service 开机启动
 
systemctl start sshd.service 立即启动
```

#### 查看ip

```
ip addr
```

![](https://img.yuechucard.space/blog/arch/16.png)

在Xshell中输入ip跟账号密码即可连接成功

![](https://img.yuechucard.space/blog/arch/17.png)

![](https://img.yuechucard.space/blog/arch/18.png)

# Xshell出现警告

WARNING! The remote SSH server rejected X11 forwarding request.

```shell
nano /etc/ssh/sshd_config
```

将下图改为yes

![](https://img.yuechucard.space/blog/arch/19.png)

重启ssh服务

```
systemctl restart sshd.service
```

# 以下是使用时遇到的一些问题及解决方案，不是安装教程

# [安装archlinuxcn-keyring报错](https://www.archlinuxcn.org/archlinuxcn-keyring-manually-trust-farseerfc-key/)

新系统中安装 archlinuxcn-keyring 包前需要手动信任 farseerfc 的 key archlinuxcn 社区源的 keyring 包 archlinuxcn-keyring 由 farseerfc 的 key 签署验证，而 Arch Linux 官方 keyring 中包含了 farseerfc 的 key 。自12月初 archlinux-keyring 中删除了一个退任的 master key 导致 farseerfc 的 key 的信任数不足，由 GnuPG 的 web of trust 推算为 marginal trust，从而不再能自动信任 archlinuxcn-keyring 包的签名。 如果你在新系统中尝试安装 archlinuxcn-keyring 包时遇到如下报错：

error: archlinuxcn-keyring: Signature from "Jiachen YANG (Arch Linux Packager Signing Key) <farseerfc@archlinux.org>" is marginal trust 请使用以下命令在本地信任 farseerfc 的 key 。此 key 已随 archlinux-keyring 安装在系统中，只是缺乏信任：

```shell
sudo pacman-key --lsign-key "farseerfc@archlinux.org"
```

之后继续安装

```shell
sudo pacman -S archlinuxcn-keyring
```

```
sudo ./install.sh 报错
改为
sudo sh ./install.sh
```

删除文件夹

```
rm -rf ***
```

