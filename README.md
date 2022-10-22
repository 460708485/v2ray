# v2ray


# -

自建v2ray教程很简单，整个教程分三步：

第一步：购买VPS服务器

第二步：一键部署VPS服务器

第三步：一键加速VPS服务器 （五合一的TCP网络加速脚本）

【前言】

v2ray的优势：v2ray支持的传输方式有很多，包括：普通TCP、HTTP伪装、WebSocket流量、普通mKCP、mKCP伪装FaceTime通话、mKCP伪装BT下载流量、mKCP伪装微信视频流量，不同的传输方式其效果会不同，有可能会遇到意想不到的效果哦！当然国内不同的地区、不同的网络环境，效果也会不同，所以具体可以自己进行测试。现在v2ray客户端也很多了，有windows、MAC、linux和安卓版。

第一步：购买VPS服务器

VPS服务器需要选择国外的，首选国际知名的vultr，速度不错、稳定且性价比高，按小时计费，能够随时开通和删除服务器，新服务器即是新ip。

vultr注册地址：https://www.vultr.com/?ref=9252898 （vps最低2.5美元/月，vultr全球25个服务器位置可选，包括洛杉矶、韩国、新加坡、日本、德国、荷兰等。支持支付宝和paypal付款。）

![image](https://user-images.githubusercontent.com/12781529/197231905-0e7da003-d616-46fa-990b-f877ab7e252f.png)

虽然是英文界面，但是现在的浏览器都有网页翻译功能，鼠标点击右键，选择网页翻译即可翻译成中文。

注册并邮件激活账号，充值后即可购买服务器。充值方式是支付宝或paypal，使用paypal有银行卡（包括信用卡）即可。paypal注册地址：https://www.paypal.com （paypal是国际知名的第三方支付服务商，注册一下账号，绑定银行卡即可购买国外商品）

注意：2.5美元套餐只提供ipv6 ip，一般的电脑用不了，所以建议选择3.5美元及以上的套餐。

vultr实际上是折算成小时来计费的，比如服务器是5美元1个月，那么每小时收费为5/30/24=0.0069美元 会自动从账号中扣费，只要保证账号有钱即可。如果你部署的服务器实测后速度不理想，你可以把它删掉（destroy），重新换个地区的服务器来部署，方便且实用。因为新的服务器就是新的ip，所以当ip被墙时这个方法很有用。当ip被墙时，为了保证新开的服务器ip和原先的ip不一样，先开新服务器，开好后再删除旧服务器即可。在账号的Billing选项里可以看到账户余额。



vultr改版了，最新开通服务器步骤如图：
![image](https://user-images.githubusercontent.com/12781529/197232018-0d6927c7-8767-4b7a-b5d6-c121c49337bb.png)

选择“Cloud Compute”。


选择“Regular Performance”。如果选择这个，在下面选择具体套餐的时候，最低是3.5美元/月（也要看服务器位置），流量是500GB/月；5美元是1T流量/月。

如果选择前面3个，在下面选择具体套餐的时候，最低是6美元/月，但6美元是2T流量/月。也就是，对流量需求较高的可以选择前面3个。


选择服务器位置。不同的服务器位置速度会有所不同，有的服务器的最低价格会不同，一般纽约等位置的价格最低，有3.5美元/月的，可根据自己的需求来选择。

电信用户推荐洛杉矶服务器；联通、移动用户推荐韩国、洛杉矶服务器。其它位置也可以尝试。


点击图中的系统名字，会弹出具体系统版本，推荐Debain10 （不要选CentOS7！）


选择服务器套餐。根据自己的需求来选择，如果服务器位置定了，套餐不影响速度，影响流量和配置，一般用的人数少，选择低配置就够了。

![image](https://user-images.githubusercontent.com/12781529/197232083-f2f52410-e3bb-4e2f-b1b9-49de124857ee.png)

关闭自动备份，这个是收费的，可以关闭它。


最后点击“Deploy Now”开始部署，等2~3分钟就差不多了。此时也会收到vultr官方发来的“Cloud Server Activated”邮件提醒。

完成购买后，找到系统的密码记下来，部署服务器时需要用到。vps系统的密码获取方法如下图：



删掉服务器步骤如下图：

删除服务器时，先开新的服务器后再删除旧服务器，这样可以保证新服务器的ip与旧ip不同。




第二步：部署VPS服务器

购买服务器后，需要部署一下。因为你买的是虚拟东西，而且又远在国外，我们需要一个叫Xshell的软件来远程部署。Xshell windows版下载地址：

国外云盘1下载 国外云盘2下载

如果你是Mac苹果电脑操作系统，更简单，无需下载xshell，系统可以直接连接VPS。直接打开Terminal终端，输入：ssh root@43.45.43.21（将45.45.43.21换成你的IP），之后输入你的密码就可以登录了（输入密码的时候屏幕上不会有显示）


如果不能用Mac自带的终端连接的话，直接网上搜“Mac连接SSH的软件”，有很多，然后通过软件来连接vps服务器就行，具体操作方式参考windows xshell。Mac成功连接vps后剩下的操作和windows一样。

部署教程：

下载windows xshell软件并安装后，打开软件


选择文件，新建


随便取个名字，然后把你的服务器ip填上


连接国外ip即服务器时，软件会先后提醒你输入用户名和密码，用户名默认都是root，密码是你购买的服务器系统的密码。



如果xshell连不上服务器，没有弹出让你输入用户名和密码的输入框，表明你开到的ip是一个被墙的ip，遇到这种情况，重新开新的服务器，直到能用xshell连上为止，耐心点哦！如果同一个地区开了多台服务器还是不行的话，可以换其它地区。
连接成功后，会出现如上图所示，之后就可以复制粘贴代码部署了。

Ubuntu 16+ / Debian 8+ 系统 v2ray一键部署管理脚本：

安装命令：

source <(curl -sL https://multi.netlify.app/v2ray.sh) --zh

升级命令(保留配置文件更新)：

source <(curl -sL https://multi.netlify.app/v2ray.sh) -k

卸载命令：

source <(curl -sL https://multi.netlify.app/v2ray.sh) --remove

如果输入安装命令后提示curl: command not found，那是因为服务器系统没有自带curl命令，安装一下curl。

CentOS系统安装curl命令：yum install -y curl

Debian/Ubuntu系统安装curl命令：apt-get install -y curl

安装完成后，输入v2ray可进入管理页面。脚本来自Jrohy/multi-v2ray。

脚本演示

复制上面安装命令代码到VPS服务器里，复制代码用鼠标右键的复制，然后在vps里面右键粘贴进去，因为ctrl+c和ctrl+v无效。接着输入数字1来安装。安装完成后，如果想修改、查看配置等，可以输入v2ray进行管理页面，不用重复安装脚本。



安装速度很快，安装结束后默认有个kcp协议帐号，如果不想用kcp协议，可以输入v2ray管理页面来进行传输方式的更改。（推荐websocket协议）




注意：如果安装后提示“Failed to start V2Ray Service”，即v2ray无法启动成功，输入以下3条命令：

sed -i "s/v2ray -config/v2ray run -config/g" /etc/systemd/system/v2ray.service.d/10-donot_touch_single_conf.conf

systemctl daemon-reload

systemctl restart v2ray

如果以上命令还是无法启动，将服务器的v2ray版本退回到指定版本，输入命令：

v2ray update v4.45.2

之后再重启下v2ray就可以了: 输入命令v2ray–数字1服务管理–数字3重启服务

如果选择的是CentOS系统，还需要关闭vps防火墙来开放端口，相关命令如下：

查看防火墙状态命令：firewall-cmd --state

停止firewall命令：systemctl stop firewalld.service

禁止firewall开机启动命令：systemctl disable firewalld.service

注意：账号无法使用，可能原因：客户端与服务端的设备系统时间相差过大。解决方法如下：

1、一般国外的VPS的镜像都是默认的国外时区，使用起来不是很方便。可以把它修改成北京时间，就会方便很多。
修改中国时区代码如下：

\cp -f /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

2、利用NTP同步时间协议

CentOS系统先安装NTP：yum install ntp ntpdate -y

如果是Ubuntu/Debian系统执行下面2条命令来安装NTP

apt-get update

apt-get install ntp ntpdate -y

安装NTP后， 按照顺序依次执行以下3条命令，分别是停止NTP服务、同步NTP时间、启动NTP服务：

service ntpd stop

ntpdate us.pool.ntp.org

service ntpd start

执行完成后，VPS上就是相对精确的时间设置了。很多依赖于系统时间的应用程序也就能正常工作了。注意：当vps重启后输入date来检查下时间，如果时间不是最新的，再执行以上3条命令即可。

除了通过NTP来同步时间以外，还可以手动修改vps系统时间，需要先修改中国时区，之后输入时间命令，格式（数字改为和自己电脑时间一致，误差30秒以内）：date -s "2020-2-02 19:14:00"

第三步：一键加速VPS服务器

五合一的TCP网络加速脚本，包括了BBR原版、BBR魔改版、暴力BBR魔改版、BBR plus、Lotsever(锐速)安装脚本。可用于KVMXen架构，不兼容OpenVZ（OVZ）。支持Centos 6+ / Debian 7+ / Ubuntu 14+，BBR魔改版不支持Debian 8。

wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh"

chmod +x tcp.sh

./tcp.sh
如果提示 wget: command not found 的错误，这是你的系统精简的太干净了，wget都没有安装，所以需要安装wget。CentOS系统安装wget命令: yum install -y wget Debian/Ubuntu系统安装wget命令:apt-get install -y wget

安装完成后，脚本管理命令为：./tcp.sh


操作方法：先安装内核，重启vps让内核生效，再启动对应的加速即可。数字1的BBR/BBR魔改内核对应数字4、5、6的BBR加速、BBR魔改加速和暴力BBR魔改版加速。数字2的BBRplus内核对应数字7的BBRplus加速。数字3的锐速加速内核对应数字8的锐速加速。

以安装暴力BBR魔改版加速为例，我们先安装对应的内核，输入数字1


内核安装完成后，输入y进行重启，重启才能让内核生效

注意：当服务器重启后，日期可能恢复成了默认，最好重启后输入date检查下。


重启完成后，输入数字6来启动暴力BBR魔改版加速

![image](https://user-images.githubusercontent.com/12781529/197232278-c49fc0d4-dffb-405d-a315-212d1a2ef5c4.png)


输入./tcp.sh查看最终是否启动成功。

如果想换一个加速，输入数字9进行卸载加速，然后进行同样的操作，安装内核再安装对应内核的加速即可。

注意：如果在安装内核环节出现这样一张图，注意选择NO


【v2ray客户端下载及使用方法】

客户端使用教程： v2ray各平台图文使用教程

浏览器代理设置成Socks(5) 127.0.0.1 和1080 即可通过v2ray代理上网。

谷歌浏览器chrome可配合switchyomega插件来使用，下载插件：switchyomega


安装插件，打开chrome，打开扩展程序，将下载的插件拖动到扩展程序页面，添加到扩展。

完成添加，会跳转到switchyomega页面，点跳过教程，然后点击proxy，如图填写，最后点击应用选项。
常见问题参考解决方法：

1、账号无法使用，可能原因一：客户端与服务端的设备系统时间相差过大。

a、一般国外的VPS的镜像都是默认的国外时区，使用起来不是很方便。可以把它修改成北京时间，就会方便很多。
修改中国时区代码如下：

\cp -f /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

b、利用NTP同步时间协议

CentOS系统先安装NTP：yum install ntp ntpdate -y

如果是Ubuntu/Debian系统执行下面2条命令来安装NTP

apt-get update

apt-get install ntp ntpdate -y

安装NTP后，按照顺序依次执行以下3条命令，分别是停止NTP服务、同步NTP时间、启动NTP服务：

service ntpd stop

ntpdate us.pool.ntp.org

service ntpd start

执行完成后，VPS上就是相对精确的时间设置了。很多依赖于系统时间的应用程序也就能正常工作了。 注意：当vps重启后输入date来检查下时间，如果时间不是最新的，再执行以上3条命令即可。

除了通过NTP来同步时间以外，还可以手动修改vps系统时间，需要先修改中国时区，之后输入时间命令，格式（数字改为和自己电脑时间一致，误差30秒以内）：date -s "2020-2-02 19:14:00"

2、账号无法使用，可能原因：vps防火墙端口没有放开或者本地电脑 防火墙、杀毒软件阻挡代理软件。

关闭vps防火墙即可开放所有端口，本地电脑防火墙和杀毒软件手动关闭即可。

查看vps防火墙状态命令：

firewall-cmd --state

停止firewall命令：

systemctl stop firewalld.service

禁止firewall开机启动命令：

systemctl disable firewalld.service

3、搭建的账号之前能用，突然不能用了，怎么解决？

如果ip不能ping通，xshell不能直接连接vps服务器，说明ip被墙了，需要开新服务器换ip。

如果ip能ping，xshell能直接连接vps服务器，说明ip没有被墙，多半是端口被封了，优先换端口。

如果ip和端口都没问题，可以尝试来更换传输协议，比如Websocket、TCP、mKCP等，测试哪种协议最适合自己的网络环境。
