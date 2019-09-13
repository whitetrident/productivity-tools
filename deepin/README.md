<h1 align="center">生产力（deepin篇）</h1>

## 目录

- [程序](#程序)

- [禁用触摸屏](#禁用触摸屏)

- [省电模式](#省电模式)

- [提高intel网卡网速](#提高intel网卡网速)

- [rpm转deb](#rpm转deb)

- [xmind打开文件为空白](#xmind打开文件为空白)

- [自定义快捷键](#自定义快捷键)

### 程序

[包管理](https://wiki.deepin.org/wiki/%E8%BD%AF%E4%BB%B6%E5%8C%85%E7%AE%A1%E7%90%86)

包管理器命令搜索apt(8)

清除已删除包残余
```bash
dpkg -l |grep ^rc|awk '{print $2}' |sudo xargs dpkg -P
```

git安装: sudo apt install git

node跟npm配置直接用nvm来安装
```bash
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.34.0/install.sh | bash
```

#### 目录

新立得软件包管理器

gimp（ps）

viewnior （打开大文件不卡且占用内存小的看图）

dbeaver （数据库）

kdesvn  （svn图形化）

gitkraken  （git图形化）

gnome-do (类似windows下win+s的搜索程序)

chmsee （chm格式文件阅读器）

磁盘（设置磁盘的挂载选项）

[dingtalk](https://github.com/nashaofu/dingtalk)

[electron-ssr](https://github.com/lolimay/shadowsocks-deepin)

copyQ: 类似win10 win+v的剪切板历史

angrysearch: 类似windows evething的搜索

ndm (npm desktop manage)

oneclickbingwallpaper(必应壁纸)

xmind-vana

[motrix(下载工具)](https://motrix.app/zh-CN/)

filezilla

### 禁用触摸屏

/home/ooo/.config/autostart下新建xx.desktop
```bash
[Desktop Entry]
Type=Application
Exec="/home/ooo/Documents/disableTouch.sh"
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[zh_CN]=禁用触摸屏
Name=disableTouch
Comment[zh_CN]=禁用触摸屏
Comment=禁用触摸屏
```
新建脚本 读写可执行权限 755
```bash
chmod 755 ./xx.desktop
```
```bash
xinput set-prop 'ELAN2097:00 04F3:2331' 'Device Enabled' 0
```

### 省电模式

【laptop_mode_tools篇】
15.7的laptop_mode_tools在我的笔记本上，默认并没有让我的cpu进入powersave模式
当我拔掉AC后，依然没有进入powersave模式，这是导致功耗极大的原因。（当然我的笔记本是集显，没有显卡耗电问题，功耗基本集中在cpu）

于是我在/etc/rc.local加入了开机强制进入powersave模式的指令
```bash
echo 'powersave' > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo 'powersave' > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
echo 'powersave' > /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor
echo 'powersave' > /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
```

实际上这一步是最关键的，其他对laptop_mode_tools的其他配置影响不大。这一步就能降低很大功耗

【TLP篇】
安装TLP会自动卸载laptop_mode_tools
sudo apt install tlp*

安装后，不做设置就能很好的降低功耗，默认配置能够将CPU进入powersave模式，这一点优于laptop_mode_tools
不过也可以对其进行一些定制化配置，其中有一点我非常喜欢
编辑配置文件"/etc/default/tlp"

其中有一个配置能够在battery模式限制CPU最高百分比，这样又能进一步降低功耗，这一点我认为tlp胜出，并简单
```bash
# Set Intel P-state performance: 0..100 (%).
# Limit the max/min P-state to control the power dissipation of the CPU.
# Values are stated as a percentage of the available performance.
# Requires an Intel Core i processor with intel_pstate driver.
CPU_MIN_PERF_ON_AC=0
CPU_MAX_PERF_ON_AC=100
CPU_MIN_PERF_ON_BAT=0
CPU_MAX_PERF_ON_BAT=70
```

### 提高intel网卡网速

/etc/modprobe.d/iwlwifi.conf中的11n_disable=1改为11n_disable=8

### rpm转deb

rpm转换deb Deepin（Ubuntu）安装rpm软件包    1.首先安装alien和fakeroot这两个软件，alien可以将rpm转换为deb包。     在终端中输入命令          sudo apt-get install alien fakeroot          2.使用alien将rpm包转为deb包：          fakeroot alien javase*.rpm          3.转换成功，可以即刻使用这个命令来安装：          sudo dpkg -i javase*.deb

### xmind打开文件为空白

这个是 /usr/share/applications/XMind.desktop 文件的问题，把第四行的 “ %U ” 改成 “ %f ” 就好了。

### 自定义快捷键

Name=关机
Action=systemctl poweroff
Accels=XF86PowerOff;

切换启动器
dde-launcher --toggle