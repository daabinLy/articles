# Debian的用法

## 版本

Debian总是同时至少维护三个版本：stable，testing和unstable。

stable是最新的官方发行版，也是推荐安装的版本。目前是version 7，代码名wheezy，2013年5月4日首次发行。2014年10月18日发布7.7版。

testing是正在测试、将要成为stable的版本，会包含更新的软件。目前的testing版是jessie。

unstable是当前正在积极开发的，包含有最新的软件，但可能不稳定、并且有错误。目前的unstable版是sid。

- The next release of Debian is codenamed jessie
- Debian 7 (wheezy)
- Debian 6.0 (squeeze)
- Debian GNU/Linux 5.0 (lenny)
- Debian GNU/Linux 4.0 (etch)
- Debian GNU/Linux 3.1 (sarge)
- Debian GNU/Linux 3.0 (woody)
- Debian GNU/Linux 2.2 (potato)
- Debian GNU/Linux 2.1 (slink)
- Debian GNU/Linux 2.0 (hamm)

## apt

### 软件源

apt的源列表存放在`/etc/apt/sources.list`文件。

```bash
deb http://mirrors.ustc.edu.cn/debian wheezy-backports main non-free contrib
deb http://mirrors.ustc.edu.cn/debian wheezy-proposed-updates main contrib non-free
deb http://mirrors.ustc.edu.cn/debian-security wheezy/updates main contrib non-free
deb-src http://mirrors.ustc.edu.cn/debian wheezy-backports main non-free contrib
deb-src http://mirrors.ustc.edu.cn/debian wheezy-proposed-updates main contrib non-free
deb-src http://mirrors.ustc.edu.cn/debian-security wheezy/updates main contrib non-free
deb http://http.us.debian.org/debian wheezy-backports main contrib non-free
deb http://security.debian.org wheezy/updates main contrib non-free
```

sources.list文件的每一行就是一个软件源。它的格式分成四个部分。

1. deb或者deb-src（表示deb包或者源代码）。
2. debian镜像的地址，标准的结构下这个地址目录下有dists、pool等子目录。
3. 第三部分为版本目录，即`http://mirrors.163.com/debian/dists/`下的子目录，我们要选择想要使用的版本，比如我们要用testing，则此部分为testing。注意Unstable和Sid是相同的，目前来说，Testing和Wheezy是相同的，Stable和Squeeze是相同的。
4. 第四部分为第三部分目录下的子文件夹，通常是main、contrib、non-free三个文件夹（ubuntu的命名与此不同），分别代表自由软件，半自由软件和非自由软件。通常我们将这三个都写上，以空格分开。

Debian系统升级

```bash
sudo aptitude update
sudo aptitude dist-upgrade
```
### 安装和卸载软件

apt-get install命令用来安装软件。

```bash
$ sudo apt-get remove [软件名]
```

apt-get remove命令用来卸载软件（保留配置文件）。

```bash
$ sudo apt-get remove [软件名]
```

apt-get purge用来彻底卸载软件（包括删除配置文件）。

```bash
$ sudo apt-get purge [软件名]
```

### 升级

apt-get update命令用来更新本地的软件信息库。

```bash
$ sudo apt-get update
```

升级单个软件，只要重新使用apt-get install即可。

```bash
$ sudo apt-get install [软件名] 
```

apt-get upgrade命令升级所有本地已安装的软件。

```bash
$ sudo apt-get upgrade 
```

### 搜索软件

apt-cache search命令用来搜索软件。

```bash
$ apt-cache search [搜索词] 
```

## /etc/network/interfaces

/etc/network/interfaces is Debian's network card configing file. 

```bash
auto eth0
iface eth0 inet dhcp
```

```bash
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.254
```