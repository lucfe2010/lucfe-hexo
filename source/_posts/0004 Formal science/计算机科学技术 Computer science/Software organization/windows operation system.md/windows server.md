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