# 真香警告！华硕RT-AC66U-B1梅林固件升级科学上网全攻略

自从去年搬家后，网络开始变得不稳定，电视盒子经常某个时段间歇性抽风，播一会缓冲一会，而从光猫另一个口分出来的IPTV则很稳定不卡，分析可能是路由器连接设备太多了，100+块钱的TPLINK带不动，上周开始考虑置换一个更强大的路由器。知乎京东逛一圈下来，基本明确自己的需求：
* 路由器第一要求是稳定，功能再强大，网络不稳定也不能考虑。因此只考虑家用路由器领域的老牌厂商，跨界玩路由器的厂商不考虑。
* 可以预见不久未来，家庭智能设备还会越来越多，要支持连接20+台设备。
* 家里光纤已经升级成千兆网络，要支持真正的双频双千兆。
* 带USB3.0网口，这样外接硬盘，路由器可以当个简易版NAS用。
* 最好支持刷梅林固件，只要愿意折腾，科学上网不是梦。

综合以上要求，最后决定在网件R6400和华硕RT-AC66U-B1两款中选择，都是差不多500-600块之间的价位，上述条件都满足，性能差不多，两者都能刷梅林，总体风评是网件的路由器综合性能要好过华硕的，性价比更高；华硕对梅林系统的兼容性更好，刷机没那么多问题。

由于网件R6400相比便宜了近100大洋，就愉快地在京东下单了。第二天京东到货，拆开包装还是吓了一跳，R6400的外形相比之前的TPLINK要大一圈，一排的信号灯亮起来也是非常亮，光污染果然名不虚传。网件的后台管理比较简陋的，但网络确实稳定，盒子连上了5G频段的wifi，试用了一天没有卡顿过，连拖动进度条都是秒切。

![R6400变形金刚主题包装](https://upload-images.jianshu.io/upload_images/1797904-2d1b39310837f632.JPG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![R6400机身](https://upload-images.jianshu.io/upload_images/1797904-9a04d21419340447.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

于是开始研究刷梅林固件，然后发现踩坑了，原来京东卖的R6400都是变形金刚包装版本，从外包装到机身都标注为R6400，但登陆后台就会发现完整型号是R6400V2，而这两者的固件是不一样的，至今为止还没有梅林固件能完美适配R6400V2，即使勉强刷上，也会有网络不稳定降速的情况。不能忍，掏出手机又下单了华硕RT-AC66U-B1，第三天天猫到货。

![AC66U-B1外包装](https://upload-images.jianshu.io/upload_images/1797904-713898b1e3a984fc.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![AC66U-B1机身](https://upload-images.jianshu.io/upload_images/1797904-be1a77ffee313d51.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

相比R6400的霸气侧漏，AC66U-B1的外形小巧些。华硕的后台页面也比网件的更加美观、人性化些，另外，梅林固件是基于华硕路由器的定制固件，因此梅林跟华硕的管理页面基本一样，入手华硕的朋友，后续刷了梅林固件也能很快上手。
AC66U-B1的网络表现同样稳定，开始准备跟着网上教程刷梅林系统。有兴趣更多了解AC66U-B1这款路由器的同学，可以看这个帖子[【长期更新】ASUS Merlin 折腾记 + 我的 RT-AC66U B1](https://zhuanlan.zhihu.com/p/34156571)。

> 下文将专注于讲解AC66U-B1路由器刷梅林固件、装koolproxy去视频广告及购入国外vps、装ss实现科学上网的具体操作，关于其他话题延展，会适当贴出其他链接。由于AC66U-B1与AC68U的固件是一样的，下文提到的安装文件AC68U也同样适用。华为系列的路由器则需要根据给出的链接下载对应版本安装文件，其余操作攻略是通用的。

### 1. 安装梅林固件
 
梅林固件有官方版及koolshare论坛版本，只有koolshare论坛版本固件才会有软件中心能安装第三方插件，如ss和koolproxy两神器，这也是大部分人刷梅林固件的目的。因此进入[[koolshare论坛下载目录]](http://firmware.koolshare.cn/)，根据路由器型号下载对应梅林固件。
链接页面有如下两个目录，分别为旧版380及新版384梅林固件目录，关于新旧版的差异对比你可以[[点击这里]](http://114.55.26.126/archiver/tid-14080.html)，总结来说，新版更稳定，但由于社区精力有限，新版对第三方插件的支持并不友好，所以我还是选择刷旧版380固件。
![旧版380及新版384梅林固件](https://upload-images.jianshu.io/upload_images/1797904-9af160def4275ebd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

由于AC66U-B1跟AC68U的固件是一样的，如果你也是这两款路由器也想安装380旧版，直接点这里下载[[AC66U-B1/AC68U梅林固件下载目录]](http://firmware.koolshare.cn/koolshare_Merlin_Legacy_380/ASUS/RT-AC68U/)，380旧版分了X6.6-X7.9几个细分版本，我个人刷过X7.1版本，后来感觉网络不太稳定，电视盒子出现了卡顿情况，又刷了X7.7版本，没再卡顿，个人经验还是选择高版本。下载好固件就可以准备安装了。安装方法有两种，建议用第二种方法，万用万灵：
1. 傻瓜式。后台直接上传文件升级。网线一端接路由器LAN口，一端接电脑，打开浏览器，输入router.asus.com进入华硕管理后台，进入[系统设置]->[固件升级]，上传.trx格式的固件安装文件，点击升级就完事了。这种安装方式简单易懂，但也比较多限制，不能从高版本刷回低版本，不能从二次版本刷回官方版或者原版固件。
![上传安装固件页面](https://upload-images.jianshu.io/upload_images/1797904-917dc98625db01fd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2. 万能式。路由器开启救援模式，PC使用救援工具上传安装固件。首先，下载[[救援工具]](https://pan.baidu.com/s/1rxjEk0-2I1C6Z6fPbHA-LA)，然后按这篇教程操作[[华硕路由器进入救援模式及使用救援工具]](http://www.52asus.com/thread-34-1-1.html)，救援工具安装完固件后，路由器会自动重启。有时在会碰到上传到一半失败的情况，不清楚具体原因，耐心多尝试几次总会成功。

安装成功后，同样输入router.asus.com登录梅林固件后台管理页面，可以看到固件版本信息，梅林固件相比自带的后台管理，多了右侧系统信息，及左下角软件中心。有些人表示刷了梅林固件后看不到软件中心，对不起，你错刷了官方的梅林固件，按前文重新刷koolshare版固件吧。
![koolshare论坛版梅林固件后台管理页面](https://upload-images.jianshu.io/upload_images/1797904-3d90de5fff8231ae.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

刷完梅林后先别急着安装第三方插件，先在[系统管理]->[系统设置]内勾选：Format JFFS partition at next boot（下次重启格式化JFFS分区）和 Enable JFFS custom scripts and configs（开启JFFS自定义脚本），点击应用本页面设置，成功应用后重启路由器。这样可以开启JFFS分区用于存放第三方插件。

从前的软件中心是可以直接下载到ss和koolproxy的，因不可抗力因素，现在已经下线了，想装这两个插件要自己下载离线安装包进行安装。由于下载安装麻烦让人却步，但插件效果非常强大，往往给使用者带来真香体验。下面写下两款插件的手把手攻略，希望可以让一些朋友少走弯路，早日真香。
![软件中心可直接安装的插件](https://upload-images.jianshu.io/upload_images/1797904-f8726f0f626a4620.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 2. koolproxy
koolproxy的安装使用比较简单，先介绍这个。koolproxy有什么用？这么说，如果你想看电视盒子不再看前面的60秒广告，装它就对了。

下载离线安装包的难点在于不同品牌不同型号的路由器使用了不同的cpu架构，有MIPS，arm7，arm8，x64等架构，需要根据路由器cpu架构来下载离线安装包。AC66U-B1/AC68U的架构是arm7，如果你刚好是AC66U-B1/AC68U或者是arm7架构的路由器，且刷了380旧版梅林固件，可以用这个安装文件[[点我下载]](https://pan.baidu.com/s/1g3_9D3YAUwrEpSNqpTR-LA)。如果不是，看看这个帖子能不能找到适合你的版本[[梅林koolproxy多平台离线包]](https://www.right.com.cn/forum/forum-173-1.html) ，云盘精灵也有对应的下载链接[[云盘精灵-koolproxy下载页]](https://www.yunpanjingling.com/resources/5d3029474b3f416f7851e0f3)。

下载了正确版本的安装包，剩下的事情非常简单了，将下载文件koolproxy+380+armv7.tar.gz文件重命名为koolproxy.tar.gz，用**Chrome浏览器**进入软件中心的离线安装界面，上传文件后就会自动安装。

![软件中心离线安装界面](https://upload-images.jianshu.io/upload_images/1797904-9b8b7e15dcf5847d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

安装完成后，进入koolproxy插件设置页面，开启koolproxy就好了。插件还允许用户编辑过滤规则，但本身自带的规则已经够用了，至少我试了几大视频app是没有广告的。

![koolproxy插件设置](https://upload-images.jianshu.io/upload_images/1797904-4f71294492787c26.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 3. 科学上网

用ss科学上网，俗称搭梯子、翻墙，这比较复杂些。需要先购买国外vps，vps部署ss服务，本地安装ss客户端进行连接，从而实现科学上网。之前也搭建过ss，但每台设备如手机、电脑都需要单独安装ss客户端，每次手动进行连接还是比较烦人的，改由在路由器上安装ss实现透明代理是更理想的方案，设备只要连上路由器wifi就能科学上网了。对透明代理原理感兴趣的朋友，可以看这篇帖子[[透明代理技术原理]](https://linux-network-programming.readthedocs.io/zh_CN/latest/services/merlin/anti-gfw.html)。

下面本着包学包会原则，介绍实现科学上网的每个步骤要点及参考帖子。
1. 安装ss插件
你可以在这个链接下载对应版本安装包[[各版本ss离线安装包]](https://github.com/hq450/fancyss_history_package)，同样如果你是AC66U-B1/AC68U且刷了380旧版梅林固件，可以用这个安装文件[[点我下载]](https://pan.baidu.com/s/1m2UEXhAtBVfrWON_XakhXw)。将下载文件ss+380+armv7.tar.gz重命名为shadowsocks.tar.gz，在软件中心进行上传安装。

2. 购买国外vps
vps全称Virtual Private Server（虚拟专用服务器），是指将一台服务器分割成多个虚拟专享服务器。购买vps也就是购买一部分物理服务器的使用权，其中包括这台服务器的网络流量。如果服务器在国外，用ss就能把指定的网络请求发送到国外服务器，再由服务器将请求到的内容回传本地，犹如这台设备正在国外上网。
国外的老牌vps提供商当推[vultr](https://www.vultr.com/)，[搬瓦工](https://bwh88.net/)两家。个人使用对比感觉，vultr更像一家云服务器提供商，支持灵活新建服务器，备份快照，切换各地机房，更换ip，而且收费非常灵活，按时计费，然而他们各地线路在国内都不是很稳定，一到晚上高峰时段，油管看480p的视频都要缓冲半天，这就呵呵了。反观搬瓦工的优缺点跟vultr正好相反，它是一家传统的vps提供商，从界面到功能都比较简陋，然而这些对于科学上网的述求而言，并不重要，重要的是它的国内网络既快且稳！原因在于相比vultr清一色的163线路，搬瓦工在LA机房建有CN2线路网络[[详解163、CN2-GT和CN2-GIA]](https://www.xxorg.com/archives/5103)。简单来说，163是屌丝线路，CN2是高级线路，虽然两条线路从LA到国内都有100+ms延迟，但CN2线路网速非常稳定。
现在搬瓦工官网只有下图几种套餐了，每年49.99美元的套餐是最经济实惠的，使用优惠码只需要46.99美元，330+人民币/年，折合不到30人民币/月，对比vultr最低套餐$5美元/月也是有价格优势的。1T/月流量，不下载东西基本够用了。
![搬瓦工官网可选套餐](https://upload-images.jianshu.io/upload_images/1797904-16f50c5e89de2138.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
没二话，搬瓦工购入CN2线路套餐[[购买链接]](https://bwh88.net/cart.php?a=confproduct&i=2)，具体购买流程可以参考[[新手用户搬瓦工vps购买图文指导教程]](https://banwagong.cn)，CN2线路有DC3和DC8两个机房可选，又纠结了一番，参考帖子[DC3 和 DC8 哪个好？](https://www.bandwagonhost.net/1070.html)ping下两个机房地址，哪个延迟低买哪个。

![两个CN2线路机房](https://upload-images.jianshu.io/upload_images/1797904-d752a940a38207d8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3. 搭建ss服务
成功购入搬瓦工vps后，官网进入My Services页签，点选KiwiVM Control Panel进入控制台。

![](https://upload-images.jianshu.io/upload_images/1797904-4fd3b473b311985f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![搬瓦工KiwiVM控制台](https://upload-images.jianshu.io/upload_images/1797904-63c101f65d21cc9f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
可以看到搬瓦工vps默认安装了Centos 7，Status为Running状态，说明服务器已经跑起来了。以前控制台是可以傻瓜式一键搭建ss服务器，因不可抗力因素again，这个选项也被屏蔽了。那就只能终端SSH连接服务器手动搭建了。终端软件window可以用xshell，mac可以用termius。不同终端只有界面差异，操作步骤都是一样的。

* 首先，查收邮箱，搬瓦工会发送一封带有vps账号信息的邮件给你，其中包括ip、port及登录密码。
![账号信息邮件](https://upload-images.jianshu.io/upload_images/1797904-fde8808f509101d4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 终端连接服务器，填写邮件里ip、port及登录密码，用户名默认填写root，进行连接就可以登录vps，登录成功可以看到控制台显示如下字样，下面跟着几个简单步骤，在控制台输入代码就可以搭建ss了。
![终端连接成功的控制台](https://upload-images.jianshu.io/upload_images/1797904-61d23e1e6265ebbc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 安装 wget ：

```
yum install wget
```

* 执行安装ss：

```
wget –no-check-certificate -O shadowsocks.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks.sh
```

* 获取shadowsocks.sh读取权限

```
chmod +x shadowsocks.sh
```

* 运行shadowsocks.sh脚本：
```
./shadowsocks.sh
```

* 设置ss登录密码
![设置ss登录密码](https://upload-images.jianshu.io/upload_images/1797904-2502b0c05bc02e39.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 设置ss登录端口，1~65535随便指定1个
![设置ss登录端口](https://upload-images.jianshu.io/upload_images/1797904-0267240ed68a75de.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 设置ss加密方式，一般指定aes-256-cfb方式
![设置ss加密方式](https://upload-images.jianshu.io/upload_images/1797904-9c19422c134a0bd7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 最后按下任意键安装ss服务，等待安装完毕，看到下面字样就代表ss搭建好了。记住下面标红的信息，距离科学上网只剩最后一步了。

![bingo，ss搭好了~](https://upload-images.jianshu.io/upload_images/1797904-0ac9417a6ab747bb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

4. 梅林固件登录ss 
还记得第一步里在梅林固件里装好的ss吗？点开ss设置菜单，打开科学上网开关，切到[节点管理]页签，添加节点，依次填入前面的标红的ip、port、密码及加密方式信息。添加成功后，切到[账号设置]页签，选择刚添加的节点，模式一般选gfwlist模式，点击提交。看上面的运行状态，国外连接及国内连接成功就OK了。

![添加节点](https://upload-images.jianshu.io/upload_images/1797904-1d46d6845f8dd316.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![设置节点](https://upload-images.jianshu.io/upload_images/1797904-ee0ed6eecfbcdabb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


现在打开网页，不出意外就可以正常访问Google了，有CN2线路加持，油管看720p视频也没有压力。至此，科学上网探索之旅到此告一
