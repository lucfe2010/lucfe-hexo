# Computer science

Dim datestr As String = "" datestr = Format(Now(), "yyyy/MM/dd H:mm:ss ffff") 用户定义的日期/时间格式（Format 函数）

## qawfe

HTML中<，>，&等有特殊含义（<，>，用于链接签，&用于转义），不能直接使用。这些符号是不显示在我们最终看到的网页里的，那如果我们希望在网页中显示这些符号，就要用到HTML转义字符串（Escape Sequence）

显示 说明 实体名称 实体编号
 空格 &nbsp; &#160;
< 小于 &lt; &#60;
> 大于 &gt; &#62;
& &符号 &amp; &#38;
" 双引号 &quot; &#34;
© 版权 &copy; &#169;
® 已注册商标 &reg; &#174;
™ 商标（美国） ™ &#8482;
× 乘号 &times; &#215;
÷ 除号 &divide; &#247;

## 如何卸载windows的服务？卸载服务？

找到一个需要卸载的服务

双击打开

![Alt text](</assets/images/Computer Science/image.png>)

如何我们需要复制下来这个服务的名称

![Alt text](</assets/images/Computer Science/image-1.png>)

然后再cmd下输入 sc delete 服务名称来卸载服务

输入完成之后回车即可

卸载完成

![Alt text](</assets/images/Computer Science/image-2.png>)

安装到服务器的Windows Service卸载的时候出错了，结果在服务列表中就一直驻留，并且系统进程一直在运行，怎么都杀不掉。

最后终于找到办法了：

1.常规做法，批处理命令卸载

Net Stop ServiceName
sc delete ServiceName
pause

2.如果还是没办法，那就继续尝试

a.找到系统注册表，删掉服务的注册表信息，通常路径在：HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services 找到你的Service服务的名字，然后把整个文件夹删掉

b.如果还是在继续运行，service列表中还显示的话，用管理员权限打开cmd 命令 sc delete serviceName,如果提示 “the specified service is marked as deletion”。

导致windows service不能部署，也不能被删除，使用 SC 命令也不奏效。确实冒了一把冷汗。经过10几分钟的折腾，终于弄明白了：原来是windows service database缓存的原因，reboot server可以完美解决问题。但实际上我们可以尝试:

1. 关闭所有windows service控制面板。

2. 查找windows service的PID：SC queryex service_name

3. 杀掉进程：taskkill /PID service_pid /f

这样就再也不用担心windows service部署了。

至此就可以完全卸载掉了。

### 基于 LDAP 的 AD 域服务器搭建及其使用

1.1 AD 域服务

什么是目录（directory）呢？

日常生活中使用的电话薄内记录着亲朋好友的姓名、电话与地址等数据，它就是 telephone directory（电话目录）；计算机中的文件系统（file system）内记录着文件的文件名、大小与日期等数据，它就是 file directory（文件目录）。

如果这些目录内的数据能够由系统加以整理，用户就能够容易且迅速地查找到所需的数据，而 directory service（目录服务）提供的服务，就是要达到此目的。在现实生活中，查号台也是一种目录；在 Internet 上，百度和谷歌提供的搜索功能也是一种目录服务。

Active Directory 域内的 directory database（目录数据库）被用来存储用户账户、计算机账户、打印机和共享文件夹等对象，而提供目录服务的组件就是 Active Directory （活动目录）域服务（Active Directory Domain Service，AD DS），它负责目录数据库的存储、添加、删除、修改与查询等操作。一般适用于一个局域网内。

在 AD 域服务（AD DS）内，AD 就是一个命名空间（Namespace）。利用 AD，我们可以通过对象名称来找到与这个对象有关的所有信息。

在 TCP/IP 网络环境内利用 Domain Name System（DNS）来解析主机名与 IP 地址的对应关系，也就是利用 DNS 来解析来得到主机的 IP 地址。除此之外，AD 域服务也与 DNS 紧密结合在一起，它的域命名空间也是采用 DNS 架构，因此域名采用 DNS 格式来命名，例如可以将 AD 域的域名命名为 moonxy.com。

1.2 AD域对象与属性

AD 域内的资源以对象（Object）的形式存在，例如用户、计算机与打印机等都是对象，而对象则通过属性（Attriburte）来描述其特征，也就是说对象本身是一些属性的集合。例如，创建一个账户张三，则必须添加一个对象类型（object class）为用户的对象（也就是用户账户），然后在这个用户账户内输入张三的姓名、登录账户、电话号码和电子邮件等信息，这其中的用户账户就是对象，而姓名、登录账户等数据就是该对象的属性，张三就是对象类型为用户（user）的对象。

1.3 AD 域控制器 DC

AD 域服务（AD DS）的目录数据存储在域控制器（Domain Controller，DC）内。一个域内可以有多台域控制器，每台域控制器的地位几乎是平等的，它们各自存储着一份几乎完全相同的 Active Directory。当在任何一台域控制器内添加了一个用户账户后，此账户默认被创建在此域控制器的 Active Directory，之后会自动被复制（replicate）到其他域控制器的 Active Directory，以便让所有域控制器内的 Active Directory 数据都能够同步（synchronize）。

当用户在域内某台计算机登录时，会由其中一台域控制器根据其 Active Directory 内的账户数据，来审核用户输入的账户与密码是否正确。如果是正确的，用户就可以登录成功；反之，会被拒绝登录。域控制器是由服务器级别的额计算机来扮演的，例如 Windows Server 2012 和 Windows Server 2008 R2 等。

通常，域控制器的 Active Directory 数据库是可以被读写的，除此之外，还有 Active Directory 数据库是只可以读取、不可以被修改的只读域控制器（Read-Only Domain Controller，RODC）。例如，某子公司位于远程网络，如果安全措施并不像总公司一样完备，则可以使用 RODC。

1.4 LDAP

LDAP（Lightweight Directory Access Protocol），轻量目录访问协议，是一种用来查询与更新 Active Directory 的目录服务通信协议。AD 域服务利用 LDAP 命名路径（LDAP naming path）来表示对象在 AD 内的位置，以便用它来访问 AD 内的对象。

LDAP 数据的组织方式：

![Alt text](</assets/images/Computer Science/image-3.png>)

LDAP 名称路径如下：

![Alt text](</assets/images/Computer Science/image-4.png>)

标识名称（distinguished Name，DN）：它是对象在 Active Directory 内的完整路径，DN 有三个属性，分别是 CN，OU，DC。

DC (Domain Component)：域名组件；

CN (Common Name)：通用名称，一般为用户名或计算机名；

OU (Organizational Unit)：组织单位；

例如，如上用户账户，其 DN 为：

CN=张三,OU=Web前端组,OU=软件开发部,DC=moonxy,DC=com

其中 DC（Domain Component）表示 DNS 域名中的组件，例如 moonxy.com 中的 moonxy 与 com；OU为组织单位（Organization Unit）；CN为通用名称（Common Name），一般为用户名或服务器名。除了DC与OU之外，其他都利用CN来表示，例如用户与计算机对象都属于CN。上述DN表示法中的 moonxy.com 为域名，软件研发部、Web前端组都是组织单位。此 DN 表示账户张三存储在 moonxy.com\软件研发部\Web前端组路径中。

相对标识名称（Relative Distinguished Name，RDN）：RDN用来代表DN完整路径中的部分路径，例如上面路径中的 CN=张三与 OU=Web前端组等都是 RDN。

Base DN：LDAP 目录树的最顶部就是根，也就是所谓的 "Base DN"，如 "DC=moonxy,DC=com"。

除了 DN 与 RDN 这两个对象名称外，另外还有如下两个名称：

全局唯一标识符（Global Unique Identifier，GUID）：GUID 是一个128位的数值，系统会自动为每个对象指定一个唯一的GUID。虽然可以改变对象的名称，但是其GUID永远不会改变。

用户主体名称（User Principal Name，UPN）：每个用户还可以有一个比DN更短、更容易记忆的 UPN，例如上面的张三隶属于 moonxy.com，则其 UPN 可以为 `zhangsan@moonxy.com`。用户登录时所输入的账户名最好是 UPN，因为无论此用户的账户被移动到哪一个域，其 UPN 都不会改变，因此用户可以一直使用同一个名称来登录。

AD 与 LDAP 的关系：LDAP 是一种用来访问 AD 数据库的目录服务协议，AD DS 会通过 LDAP 名称路径来表示对象在 AD 数据库中的位置，以便用它来访问 AD 数据库内的对象。LDAP 的名称路径包括有 DN、RDN。

openLDAP（Linux），Active Directory（Microsoft）等是对 LDAP 目录访问协议的具体实现，除了实现协议的功能，还对它进行了扩展。

1.5 全局编录

虽然在域树内的所有域共享一个 Active Directory，但是 Active Directory 数据却分散在各个域内，而每个域仅存储该域本身的数据。因此，为了让用户、应用程序能够快速找到位于其他域内的资源，在 AD 域服务器内设计了全局编录（Global Catalog，GC）。

全局编录的数据存储在域控制器内，这台域控制器被称为全局编录服务器，它存储着林内所有域的 AD 内的每个对象。不过只存储对象的部分属性，这些属性都是常用来搜索的属性，例如用户的电话号码、登录账户名等。全局编录让用户即使不知道对象位于哪一个域内，仍然可以快速的找到所需的对象。

用户登录时，全局编录服务器还负责提供该用户所属的通用组的信息；用户利用 UPN 登录时，它会负责提供该用户隶属于哪一个域的信息。

一个林内的所有域树共享相同的全局编录，而林内的第一台域控制器默认就是全局编录服务器。必要时，也可以另外指派其他域控制器来当做全局编录服务器。

### 降噪耳机

 是指利用某种方法达到降低噪音的一种耳机。降噪耳机有两种分别为：主动降噪耳机和被动降噪耳机。
主动降噪功能就是通过降噪系统产生与外界噪音相等的反相声波，将噪音中和，从而实现降噪的效果。被动式降噪耳机主要通过包围耳朵形成封闭空间，或者采用硅胶耳塞等隔音材料来阻挡外界噪声。

### home assistant

小米有米家APP、苹果有homekit、华为有智慧生活……，而我只想自己手机里只有一个智能家居APP，而不是小米米家、欧瑞博、博联broadlink、海尔智家、美的美居、萤石等一堆APP，并且我也不想操控空调我打开美的美居，想看下摄像头又得打开萤石APP，控制插座又打开博联APP，反复在不同APP间跳转。这些对终端消费者来说都是十分糟糕的体验，也是各个智能家居厂商各自为政造成的恶果。而home assistant可以同时接入小米、博联、美的、海康威视等等智能家居，实现了各品牌智能家居的统一管理，一下这个世界就清净舒服多了。

### Cygwin

Cygwin是一个在windows平台上运行的类UNIX模拟环境，是Cygnus Solutions公司开发的自由软件（该公司开发的著名工具还有eCos，不过现已被Redhat收购）。它对于学习UNIX/Linux操作环境，或者从UNIX到Windows的应用程序移植，或者进行某些特殊的开发工作，尤其是使用GNU工具集在Windows上进行嵌入式系统开发，非常有用。随着嵌入式系统开发在国内日渐流行，越来越多的开发者对Cygwin产生了兴趣。

### 1. 国内公共DNS 国内可用的 IPv4 公共加密 DNS：DoH/DoT/DoQ

1.1 腾讯 DNS
腾讯 DNS 基于 BGP Anycast 技术，不论用户身在何地，都可就近访问服务。支持谷歌 ECS 协议，配合 DNSPod 权威解析，可以给用户提供出最准确的解析结果，承诺不劫持解析结果。

IPv4：119.29.29.29
DoH：<https://doh.pub/dns-query>
DoH：<https://1.12.12.12/dns-query>
DoH：<https://120.53.53.53/dns-query>
DoH：<https://sm2.doh.pub/dns-query> (国密)
DoT：dot.pub
DoT：1.12.12.12
DoT：120.53.53.53
1.2 阿里 DNS
阿里 DNS 线路支持包括电信、移动、联通、鹏博士、广电网、教育网及海外 150 个国家或地域，支持用户 ECS 扩展技术，智能解析；支持 DoT/DoH 协议，保护用户隐私，安全防劫持。

IPv4：223.5.5.5
IPv4：223.6.6.6
DoH：<https://223.5.5.5/dns-query>
DoH：<https://223.6.6.6/dns-query>
DoH：<https://dns.alidns.com/dns-query>
DoT：dns.alidns.com

国内 IPv6 DNS
下一代互联网国家工程中心 IPv6 DNS
下一代互联网国家工程中心（CFIEC），由北京市发改委于 2012 年认定的北京市工程研究中心，并于 2015 年由国家发改委批复升级为国家地方联合工程研究中心。

IPv6：240C::6666
IPv6：240C::6644
DoT：dns.ipv6dns.com
DoH：<https://dns.ipv6dns.com/dns-query>
DNS64：240c::64 #纯 IPv6 访问 IPv4，需同时具备 DNS64 和 NAT64 服务可以
阿里云 IPv6 DNS
IPv6：2400:3200::1
IPv6：2400:3200:baba::1
DoH：<https://2400:3200::1/dns-query>
DoH：<https://2400:3200:baba::1/dns-query>
红鱼 rubyfish IPv6 DNS
DoT：v6.rubyfish.cn
DoH：<https://v6.rubyfish.cn/dns-query>
腾讯 IPv6 DNS
2402:4e00::
