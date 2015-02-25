---
layout: post
category: network
tags: [network, vpngate, vpn, linux]
title: "use vpngate client under linux"
---
{% include JB/setup %}

#1. 从网站 http://www.softether-download.com/ 下载 SoftEther VPN 代码

![](/images/2015-02-25-01-download-softether-vpn-client.png)

#2. 将下载的文件解压到本地，编译

    $ tar zxvf softether-vpnclient-v4.14-9529-beta-2015.02.02-linux-x64-64bit.tar.gz
    $ cd vpnclient
    $ make

阅读并接受协议条款，完成编译过程

#3. 启动 vpn client 服务。使用普通用户启动 vpn client 服务，会提示你某些特权功能无法使用，因此推荐使用 root 用户来启动 vpn client 服务：

    $ sudo ./vpnclient start

#4. 使用 vpncmd 命令连接到本地 vpn client 服务创建本地虚拟网卡，这里使用普通用户即可：

    $ ./vpncmd
    vpncmd 命令 - SoftEther VPN 命令行管理工具
    SoftEther VPN 命令行管理工具 (vpncmd 命令)
    Version 4.14 Build 9529   (Simplified_Chinese)
    Compiled 2015/02/02 17:53:35 by yagi at pc30
    Copyright (c) SoftEther VPN Project. All Rights Reserved.

    通过使用 vpncmd 程序，可以取得以下成果。

    1. VPN Server 或 VPN Bridge 的管理。
    2. VPN Client 的管理。
    3. 使用 VPN 工具 (证书创建和网络传输速度测试工具)

    选择 1, 2 或 3: 2

    指定的主机名或正在运行的目标 VPN Client 计算机的 IP 地址。
    如果不输入任何内容并且按下回车键，将连接到本地主机 (这台电脑)。
    目标 IP 地址的主机名:localhost

    连接到 VPN Client "localhost"。

    VPN Client>help
    您可以使用下面的 66 命令:
     About                    - 显示版本信息
     AccountAnonymousSet      - 设定连接设置的用户认证种类为匿名认证
     AccountCertGet           - 获取用于连接设置的客户端证书
     AccountCertSet           - 设置连接设置的用户认证类型为用户证书认证
     AccountCompressDisable   - 禁用连接设置进行通信时的数据压缩
     AccountCompressEnable    - 启用连接设置进行通信时的数据压缩
     AccountConnect           - 使用连接设置，开始连接 VPN Server
     AccountCreate            - 创建新的连接设置
     AccountDelete            - 删除连接设置
     AccountDetailSet         - 设置接续设置的高级通信设置
     AccountDisconnect        - 断开连接中的连接设置
     AccountEncryptDisable    - 禁用连接设置进行通信时的加密
     AccountEncryptEnable     - 启用连接设置进行通信的加密
     AccountExport            - 导出连接设置
     AccountGet               - 取得连接设置的设置
     AccountImport            - 导入连接设置
     AccountList              - 获取连接设置列表
     AccountNicSet            - 设置连接设置时使用的虚拟 LAN 卡
     AccountPasswordSet       - 设定连接设置的用户证类型为密码认证
     AccountProxyHttp         - 将连接设置的连接方法设置为通过 HTTP 代理服务器连接

     AccountProxyNone         - 将连接设置的连接方法直接设置为 TCP/IP 连接
     AccountProxySocks        - 将连接设置的连接方法设置为通过 SOCKS 代理服务器连接

     AccountRename            - 更改连接设置名称
     AccountRetrySet          - 设置连接设置的连接失败或断开时建立重新连接的次数和
                                间隔
     AccountSecureCertSet     - 将连接设置的用户认证类型设置为智能卡认证
     AccountServerCertDelete  - 删除连接设置的服务器固有证书
     AccountServerCertDisable - 禁用连接设置服务器证书验证选项
     AccountServerCertEnable  - 启用连接设置服务器证书验证选项
     AccountServerCertGet     - 获取连接设置的服务器固有证明书
     AccountServerCertSet     - 设置连接设置的服务器固有证明书
     AccountSet               - 设定连接设置连接终端
     AccountStartupRemove     - 解除连接设置的启动连接
     AccountStartupSet        - 设定连接设置的启动连接
     AccountStatusGet         - 获取当前连接设置的状态
     AccountStatusHide        - 设置成在连接到 VPN Server 时不显示连接状态和错误的
                                画面
     AccountStatusShow        - 设置成在连接到 VPN Server 时显示连接状态和错误的画
                                面
     AccountUsernameSet       - 设置用于连接的连接设置的用户名
     CertAdd                  - 添加信任的证明机构的证书
     CertDelete               - 删除信任的证明机构的证书
     CertGet                  - 获得新任的证明机构的证书
     CertList                 - 获取信任的证明机构的证书列表
     Check                    - 检测 SoftEther VPN 是否能正常运行
     KeepDisable              - 禁用保持互联网连接功能
     KeepEnable               - 启动 Internet 保持连接功能
     KeepGet                  - 获取保持互联网连接的功能
     KeepSet                  - 设置 Internet 保持连接功能
     MakeCert                 - 创建新的 X.509 证书和密钥 (1024 位)
     MakeCert2048             - 创建新的 X.509 证书和密钥 (2048 位)
     NicCreate                - 新的虚拟 LAN 卡的创建
     NicDelete                - 删除虚拟 LAN 卡
     NicDisable               - 禁用虚拟 LAN 卡
     NicEnable                - 启用虚拟 LAN 卡
     NicGetSetting            - 获取虚拟 LAN 卡的设置
     NicList                  - 获取虚拟 LAN 卡列表
     NicSetSetting            - 更改虚拟 LAN 卡设置
     NicUpgrade               - 升级虚拟 LAN 卡设备驱动
     PasswordGet              - 获取为连接到 VPN 客户服务的密码的设定
     PasswordSet              - 为连接到 VPN 客户服务的密码的设定
     RemoteDisable            - 禁止 VPN 客户服务的远程管理
     RemoteEnable             - 允许 VPN 客户服务的远程管理
     SecureGet                - 获取使用的智能卡种类的 ID
     SecureList               - 获取可用的智能卡种类列表
     SecureSelect             - 选择要使用的智能卡种类
     TrafficClient            - 在用户模式下，运行网络流量速度测试工具
     TrafficServer            - 在服务器模式下，运行网络流量速度测试工具
     VersionGet               - 获取 VPN 客户服务的版本信息

    参考每个命令的使用，输入 "命令名称 ?" 来查看帮助。
    命令成功完成。

    VPN Client>RemoteEnable
    RemoteEnable 命令 - 允许 VPN 客户服务的远程管理
    命令成功完成。

    VPN Client>NicCreate
    NicCreate 命令 - 新的虚拟 LAN 卡的创建
    虚拟 LAN 卡名: senic

    命令成功完成。

    VPN Client>NicList
    NicList 命令 - 获取虚拟 LAN 卡列表
    项目            |价值
    ----------------+----------------------------------------------
    虚拟网络适配器名|senic
    状态            |已启用
    MAC 地址        |******
    版本            |Version 4.14 Build 9529   (Simplified_Chinese)
    命令成功完成。

    VPN Client>

这里建立了一个名为 *senic* 的虚拟网卡

#5. 在 [vpn gate 网站首页](http://www.vpngate.net/)找到一个可用的 vpn 服务器

![](/images/2015-02-25-02-vpn-server1.png)

![](/images/2015-02-25-02-vpn-server2.png)

如图，ip 218.161.13.220，tcp 端口 995

下面是我的 vpn 配置文件 *tw1.vpn* ：

    # VPN Client VPN Connection Setting File
    #
    # This file is exported using the VPN Client Manager.
    # The contents of this file can be edited using a text editor.
    #
    # When this file is imported to the Client Connection Manager
    #  it can be used immediately.

    declare root
    {
     bool CheckServerCert false
     uint64 CreateDateTime 0
     uint64 LastConnectDateTime 0
     bool StartupAccount false
     uint64 UpdateDateTime 0

     declare ClientAuth
     {
      uint AuthType 0
      string Username vpn # 用户名
     }
     declare ClientOption
     {
      string AccountName tw1 # 账户名称
      uint AdditionalConnectionInterval 1
      uint ConnectionDisconnectSpan 0
      string DeviceName senic # 虚拟网卡名称
      bool DisableQoS false
      bool HalfConnection false
      bool HideNicInfoWindow false
      bool HideStatusWindow false
      string Hostname 218.161.13.220 # ip 地址
      string HubName vpngate # hub 名称
      uint MaxConnection 1
      bool NoRoutingTracking false
      bool NoTls1 false
      bool NoUdpAcceleration false
      uint NumRetry 4294967295
      uint Port 995 # 端口号
      uint PortUDP 0
      string ProxyName $
      byte ProxyPassword $
      uint ProxyPort 0
      uint ProxyType 0
      string ProxyUsername $
      bool RequireBridgeRoutingMode false
      bool RequireMonitorMode false
      uint RetryInterval 15
      bool UseCompress false
      bool UseEncrypt true
     }
    }

使用 vpncmd 命令导入账户设置：

    $ ./vpncmd
    VPN Client>AccountImport
    AccountImport 命令 - 导入连接设置
    导入源文件名: ~/tw1.vpn

    连接设置 "tw1" 已导入。
    命令成功完成。

    VPN Client>AccountGet tw1
    AccountGet 命令 - 取得连接设置的设置
    项目                         |价值
    -----------------------------+------------------
    VPN 连接设置名称             |tw1
    目标 VPN Server 主机名       |218.161.13.220
    目标 VPN Server 端口号       |995
    目标 VPN Server 虚拟 HUB 名称|vpngate
    代理服务器类型               |直接的 TCP/IP 连接
    验证服务器证书               |禁用
    用于连接的设备名             |senic
    验证类型                     |匿名身份验证
    用户名                       |vpn
    VPN 通信中使用的 TCP 的连接数|1
    建立每个 TCP 连接的间隔      |1
    每个 TCP 连接的连接周期      |无限
    使用半双工模式               |禁用
    通过 SSL 加密                |启用
    数据压缩                     |禁用
    通过网桥 / 路由模式连接      |禁用
    通过监测模式连接             |禁用
    不要调整路由表               |禁用
    不要使用 QoS 控制功能        |禁用
    命令成功完成。

    VPN Client>AccountConnect tw1
    AccountConnect 命令 - 使用连接设置，开始连接 VPN Server
    命令成功完成。

    VPN Client>AccountList
    AccountList 命令 - 获取连接设置列表
    项目                   |价值
    -----------------------+-----------------------------------------
    VPN 连接设置名称       |tw1
    状态                   |已连接
    VPN Server 主机名(地址)|218.161.13.220:995 (直接的 TCP/IP 连接)
    虚拟 HUB 名称          |vpngate
    虚拟网络适配器名       |senic
    命令成功完成。

    VPN Client>

#6. 修改路由表

VPN 连接成功后， SoftEther VPN 仍然没法使用，我们需要先手动修改路由表信息：

##首先打开路由转发功能

打开系统配置文件：

    $ cd /etc
    $ sudo cp sysctl.conf sysctl.conf_old
    $ vim sysctl.conf

打开路由转发功能：

    net.ipv4.ip_forward=1

重新载入配置文件，使修改立即生效：

    $ sudo sysctl -p

虚拟网卡动态获取 IP 地址：

    $ ip addr show vpn_senic
    7: vpn_senic: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN group default qlen 500
        link/ether **:**:**:**:**:** brd ff:ff:ff:ff:ff:ff
        inet6 ****::***:****:****:****/64 scope link
           valid_lft forever preferred_lft forever
    $ sudo dhclient vpn_senic
    $ ip addr show vpn_senic
    7: vpn_senic: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN group default qlen 500
        link/ether **:**:**:**:**:** brd ff:ff:ff:ff:ff:ff
        inet 10.211.1.2/16 brd 10.211.255.255 scope global vpn_senic
           valid_lft forever preferred_lft forever
        inet6 ****::***:****:****:****/64 scope link
           valid_lft forever preferred_lft forever
    $ ip neigh
    ***
    10.211.254.254 dev vpn_senic lladdr 00:ac:50:16:c8:27 REACHABLE

可以看到，经过 DHCP 过程，vpn_senic 虚拟网卡动态获取到了 IP 地址 ：10.211.1.2/16。

查看当前路由：

    $ ip route
    default via 192.168.100.1 dev eth0  proto static
    10.211.0.0/16 dev vpn_senic  proto kernel  scope link  src 10.211.1.2
    ***

记住本地默认路由，若后面配置失败导致无法访问网络，可以重新设置回原来的默认路由以恢复网络。

删除默认路由，添加两条新的路由：

    $ sudo ip route add 218.161.13.220/32 via 192.168.100.1 dev eth0 proto static
    $ sudo ip route del default
    $ sudo ip route add default via 10.211.254.254 dev vpn_senic
    $ ip route
    default via 10.211.254.254 dev vpn_senic
    10.211.0.0/16 dev vpn_senic  proto kernel  scope link  src 10.211.1.2
    ***
    218.161.13.220 via 192.168.100.1 dev eth0
    $ ping 8.8.8.8
    PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
    64 bytes from 8.8.8.8: icmp_seq=1 ttl=44 time=65.2 ms
    64 bytes from 8.8.8.8: icmp_seq=2 ttl=44 time=65.0 ms
    64 bytes from 8.8.8.8: icmp_seq=3 ttl=44 time=65.1 ms
    ^C
    --- 8.8.8.8 ping statistics ---
    3 packets transmitted, 3 received, 0% packet loss, time 2000ms
    rtt min/avg/max/mdev = 65.040/65.139/65.241/0.082 ms

[](http://lukeluo.blogspot.com/2013/11/how-to-set-up-softehter-vpn-client.html)
