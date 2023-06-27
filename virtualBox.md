## 搭建后台运行的centos7服务器

### 1、新建虚拟电脑

<img src="noteImages\virtualBox\image-20230627105021674.png" alt="image-20230627105021674" style="zoom: 67%;" />

### 2、配置硬件

<img src="noteImages\virtualBox\image-20230627105124138.png" alt="image-20230627105124138" style="zoom: 67%;" />

### 3、创建虚拟硬盘

<img src="noteImages\virtualBox\image-20230627105155640.png" alt="image-20230627105155640" style="zoom: 67%;" />

### 4、点击下一步，点击完成，创建成功

<img src="noteImages\virtualBox\image-20230627105235695.png" alt="image-20230627105235695" style="zoom: 67%;" />

### 5、配置服务器

#### 5.1、选择系统，勾选启动顺序中的网络，然后点击光驱，点击右边的向上箭头将光驱放到第一位

<img src="noteImages\virtualBox\image-20230627111356990.png" alt="image-20230627111356990" style="zoom: 67%;" />

#### 5.2、选择网络，选择网卡2，点击启动网络连接，连接方式选择仅主机Host-only网络

<img src="noteImages\virtualBox\image-20230627111507975.png" alt="image-20230627111507975" style="zoom: 67%;" />

> 注：网卡1也要已经启动网络连接，连接方式默认为网络地址转换NAT即可

#### 5.3、点击右下角确定即配置完毕，配置完成之后的主界面如下图

<img src="noteImages\virtualBox\image-20230627111819220.png" alt="image-20230627111819220" style="zoom: 67%;" />

> 注：马赛克是因为这个地方的教程是后续添加的，soψ(._. )>

### 6、选中服务器，点击右上角启动，启动服务器(第一次需正常图形化界面启动)

<img src="noteImages\virtualBox\image-20230627105855222.png" alt="image-20230627105855222" style="zoom: 67%;" />

> 选择第一个，敲击回车

### 7、等待安装的过程，直到出现选择语言界面，如下图

<img src="noteImages\virtualBox\image-20230627110120876.png" alt="image-20230627110120876" style="zoom: 67%;" />

> 左边滑到最下面选择中文，右边选择简体中文，点击继续(可选，可以直接默认使用英文)

### 8、出现如下界面

<img src="noteImages\virtualBox\image-20230627110325509.png" alt="image-20230627110325509" style="zoom: 67%;" />

### 9、配置键盘和语言支持(可选，增加英语键盘和语言)

<img src="noteImages\virtualBox\image-20230627110625655.png" alt="image-20230627110625655" style="zoom: 67%;" />

### 10、配置系统安装位置

<img src="noteImages\virtualBox\image-20230627110905248.png" alt="image-20230627110905248" style="zoom: 67%;" />

> 选择本地标准磁盘，点击完成即可（外面不再显示黄色警告，如果还出现再次点进来选中再点击完成）

### 11、配置网络

<img src="noteImages\virtualBox\image-20230627111052091.png" alt="image-20230627111052091" style="zoom: 67%;" />

> 选择第一个网卡enp0s3，点击右边的关闭按钮变成打开，网络显示已连接即成功，点击完成

### 12、配置完成，点击开始安装

<img src="noteImages\virtualBox\image-20230627111234695.png" alt="image-20230627111234695" style="zoom: 67%;" />

### 13、设置root密码(必须)，添加用户(可选)，等待安装

<img src="noteImages\virtualBox\image-20230627112551175.png" alt="image-20230627112551175" style="zoom:67%;" />

### 14、安装完成，点击重启

<img src="noteImages\virtualBox\image-20230627113003973.png" alt="image-20230627113003973" style="zoom:67%;" />

### 15、重启之后默认选择第一个进入即可，然后输入root和密码进行登录，如下图即成功

<img src="noteImages\virtualBox\image-20230627113201065.png" alt="image-20230627113201065" style="zoom:67%;" />

### 16、检查网卡配置和网络是否连接

<img src="noteImages\virtualBox\image-20230627113402821.png" alt="image-20230627113402821" style="zoom:67%;" />

> 输入ip addr查看网卡，然后输入ping www.baidu.com查看能够连接外网(按ctrl+c终止)

### 17、配置静态ip地址

#### 17.1、查看virtualboxip地址

##### 17.1.1、右键电脑右下角wifi标志，点击打开网络设置

<img src="noteImages\virtualBox\image-20230627114723088.png" alt="image-20230627114723088" style="zoom:67%;" />

##### 17.1.2、选择更改适配器选项

<img src="noteImages\virtualBox\image-20230627114834652.png" alt="image-20230627114834652" style="zoom:67%;" />

##### 17.1.3、找到含有VirtualBox Host-Only Ethernet标志的网络，右键点击属性

<img src="noteImages\virtualBox\image-20230627114934438.png" alt="image-20230627114934438" style="zoom:67%;" />

##### 17.1.4、找到ipv4，点击右下方属性

<img src="noteImages\virtualBox\image-20230627115055535.png" alt="image-20230627115055535" style="zoom:67%;" />

##### 17.1.5、查看ip地址

<img src="noteImages\virtualBox\image-20230627115146818.png" alt="image-20230627115146818" style="zoom: 67%;" />

> 这里如果不是这样显示，配置成这样，然后点击确定

#### 17.2、进入服务器，编辑网络地址

##### 17.2.1、查看是否含有网卡配置文件(敲击tab快捷输入)

> ls /etc/sysconfig/network-scripts/

<img src="noteImages\virtualBox\image-20230627115451891.png" alt="image-20230627115451891" style="zoom:67%;" />

##### 17.2.2、编辑第二块网卡配置文件(即ifcfg-enp0s8，如果没有请先返回第5条配置服务器)

> vi /etc/sysconfig/network-scripts/ifcfg-enp0s8
>
> 编辑红框区域，如果没有就自己添加（vi编写文件，保存命令自己搜索）

<img src="noteImages\virtualBox\image-20230627120450227.png" alt="image-20230627120450227" style="zoom:67%;" />

##### 17.2.3、重启网络服务

> systemctl restart network

#### 17.3、输入ip addr查看配置是否成功

<img src="noteImages\virtualBox\image-20230627120901486.png" alt="image-20230627120901486" style="zoom:67%;" />

> 成功显示ip地址即为成功

### 18、配置xshell远程连接

<img src="noteImages\virtualBox\image-20230627121042587.png" alt="image-20230627121042587" style="zoom:67%;" />

<img src="noteImages\virtualBox\image-20230627121219491.png" alt="image-20230627121219491" style="zoom:67%;" />

> 点击确定后会弹框，选择接受并保存即可，然后如下图显示就表示远程连接成功

<img src="noteImages\virtualBox\image-20230627121323169.png" alt="image-20230627121323169" style="zoom:67%;" />