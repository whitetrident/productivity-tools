<h1 align="center">生产力（win10篇）</h1>

如果软件本身能够在Chocolatey上找到的，就直接放choco目录下了，找不到的会单放

## 目录

- [Chocolatey](#Chocolatey)

- [Dism++](#Dism++)

- [snipaste](#snipaste)

- [hummingbird](#hummingbird)

- [licecap](#licecap)

- [ocam](#ocam)

- [geek](#geek)

- [spacesniffer](#spacesniffer)

- [motrix](#motrix)

### Chocolatey

为什么需要一个包管理器？装机后最烦也是花时的地方是什么？环境配置，其实也就是装软件，各种国内软件管家东西有没有你想要的且不说，找这些软件花费时间，源还不一定安全可靠，而在羡慕嫉妒恨看着linux跟mac有着强大的包管理器的时候，你终于能用到了，Chocolatey提供了这种选择。

[像程序员一样安装程序：Chocolatey 初见](https://sspai.com/post/55309)

[Chocolatey官网](https://chocolatey.org/)

##### powershell管理员（右键你的开始菜单）

```bash
Set-ExecutionPolicy AllSigned; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

##### cmd管理员

```bash
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
```

##### 命令
命令 | 说明
---|---
choco -h  | 查看帮助
choco <command> -h   | 查看相应命令的帮助
choco install <package name> | 安装软件包
choco search <keyword> | 搜索软件包，会列出跟关键字相关的所有软件包
choco upgrade <package name> | 升级软件包
choco uninstall <package name> | 卸载软件包
choco list -l | 查看本地安装的软件包
choco outdated | 查看可升级的本地软件


##### 目录

***一行命令，自己保存这样的一行命令，下次能省很多事***
```bash
choco install bandizip BingDesktop dbeaver Firefox fsviewer gimp GoogleChrome Listary nircmd nodejs-lts potplayer powertoys Recuva shadowsocks sourcetree sublimetext3 SublimeText3.PackageControl tim tortoisesvn virtualbox winscp.install  -y
```

软件名 | 说明 | 地址
---|--- | ---
bandizip  | 解压缩软件，除了不能压缩rar，日常够用，免费，而且有着独有的自动解压命令帮你摆脱不知道压缩包内是一个文件还是一堆的文件烦恼 | https://www.bandisoft.com/bandizip/
BingDesktop | 必应壁纸，高清，而且每天会更新一个风景或人文的图，整体眼睛看着电脑上的你老婆（老公）真的有动力工作？这个软件唯一缺点就是硬要打开一个没卵用的搜索框，我都直接放边角让它隐藏让我点不到 | https://bing.ioliu.cn/
dbeaver | 免费开源且跨平台的数据库管理软件，支持中文!对我来讲比Navicat方便，因为单行查询跟保存都能用快捷键完成，而且Navicat可不免费？破解！破解你能及时享受到开发者提供的更新吗？而且哪天公司突然通知这个盗版有风险咋办？ | https://dbeaver.io/
Firefox | 火狐，跟谷歌各有千秋吧，如果日常不算坑爹的flash，火狐强过谷歌，因为插件不用科学上网，但是涉及到开发，我选择谷歌 | https://www.firefox.com.cn/
fsviewer | 看图软件，win10败笔之一就是那个照片，打开大图卡的要命。fs相比windows老版的照片查看器，支持的格式更多，打开大图也是那么顺畅，还有一定的编辑功能，占用内存小！而且如果你经常用触控板，fs更推荐了，对手势的支持很顺畅体贴，支持中文！ | https://www.faststone.org/FSViewerDetail.htm
gimp | ps的替代品，但是免费开源且跨平台，支持中文！ | https://www.gimp.org/
GoogleChrome | 谷歌浏览器，话说现在可以不用科学上网下载到谷歌了 | https://www.google.cn/chrome/index.html
Listary | 强大的搜索软件，搜索文件效率比windows自带的高，也能正常识别网页、应用的名字 | https://www.listary.com/
nircmd | 一个命令行工具，其实我只是用来命令行快捷让系统静音
nodejs-lts | node稳定版
potplayer | 本地视频播放器，支持格式众多，支持中文无广告 | http://www.potplayercn.com/
powertoys | 微软认真做起办公来还是很强的，目前只支持Win热键快捷键指南和窗口增强管理器，快点支持自定义快捷键gkd | https://www.iplaysoft.com/powertoys.html
Recuva | 数据恢复
shadowsocks | 滑稽
sourcetree | 目前win上最好用的git图形化，值得一提的是这家伙用choco安装完桌面是没有快捷方式的，用Listary可以搜出来，如果不改默认的话，目录应该是C:\Program Files (x86)\Atlassian\Sourcetree | https://www.sourcetreeapp.com/
sublimetext3 | 有了vscode后真的沦为了看代码软件... | http://www.sublimetextcn.com/
SublimeText3.PackageControl | sublimetext3的工具包，安装后顺便把这个一起安装了，免得又是卡住了
tim | 腾讯的产品真的不错，做的渣也给你出替代品 | https://office.qq.com/
tortoisesvn | svn图形化，这个坑爹啊，语言包竟然不跟本体放一块，每次更新就没中文了，中文语言包去地址上下， | https://tortoisesvn.net/
virtualbox | 虚拟机，vm是新版越来越坑爹了，这个免费
winscp.install | ftp上传,这个相对FileZilla更好用，可惜win独占

### [Dism++](http://www.chuyu.me/zh-Hans/index.html)

这是一款系统优化软件，开源免费，放心无毒，主要有垃圾清理跟系统常见控制项管理


### [snipaste](https://zh.snipaste.com/)

强大的截屏工具，免费，提供了除win跟mac版

### [hummingbird](https://github.com/thunkli/hummingbird)

是一个资源(jpg/png/webp/svg/gif/css/js/html)压缩客户端。可批量压缩

### [licecap](https://www.cockos.com/licecap/)

gif录屏工具

### ocam

mp4录屏工具，同样的时间mp4录屏比gif要小很多，可以屏幕部分录屏也可以游戏全屏录

### [geek](https://www.crystalidea.com/uninstall-tool?source=geek&campaign=app)

软件卸载工具，卸载后给你清理残留文件夹与注册表

### [spacesniffer](https://www.appinn.com/spacesniffer/)

SpaceSniffer是一个运行于 Windows 下的磁盘空间占用查看工具。可以分析出你的各个文件夹、文件大小，方便找出硬盘空间不足的罪魁祸首。

### [motrix](https://motrix.app/zh-CN/)

免费开源且跨平台支持中文的下载工具，支持下载 HTTP、FTP、BT、磁力链、百度网盘等资源