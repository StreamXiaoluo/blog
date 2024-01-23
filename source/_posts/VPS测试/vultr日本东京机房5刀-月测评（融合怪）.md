---
title: vultr日本东京机房5刀/月测评（融合怪）
date: 2024-01-19 15:26:48
tags: VPS测评
categorier: 低价VPS测试
---
测评频道: https://t.me/vps_reviews                    
版本：2024.01.16
更新日志：VPS融合怪测试(集百家之长)                       
---------------------基础信息查询--感谢所有开源项目---------------------
 CPU 型号          : Intel Core Processor (Broadwell, no TSX, IBRS)
 CPU 核心数        : 1
 CPU 频率          : 2394.454 MHz
 CPU 缓存          : L1: 32.00 KB / L2: 4.00 MB / L3: 16.00 MB
 硬盘空间          : 7.31 GiB / 22.91 GiB
 启动盘路径        : /dev/vda2
 内存              : 309.83 MiB / 954.76 MiB
 Swap              : 49.83 MiB / 2.34 GiB
 系统在线时间      : 2 days, 16 hour 35 min
 负载              : 1.00, 0.24, 0.08
 系统              : Debian GNU/Linux 12 (bookworm) (x86_64)
 AES-NI指令集      : ✔ Enabled
 VM-x/AMD-V支持    : ❌ Disabled
 架构              : x86_64 (64 Bit)
 内核              : 6.1.0-15-amd64
 TCP加速方式       : bbr
 虚拟化架构        : Microsoft Hyper-V
 NAT类型           : 开放型
 IPV4 ASN          : AS20473 The Constant Company, LLC
 IPV4 位置         : Ōi / Saitama / JP
 IPV6 ASN          : AS20473 The Constant Company, LLC
 IPV6 位置         : Shinagawa City / JP-13
 IPV6 子网掩码     : 64
----------------------CPU测试--通过sysbench测试-------------------------
 -> CPU 测试中 (Fast Mode, 1-Pass @ 5sec)
 1 线程测试(单核)得分: 		816 Scores
---------------------内存测试--感谢lemonbench开源-----------------------
 -> 内存测试 Test (Fast Mode, 1-Pass @ 5sec)
 单线程读测试:		17818.98 MB/s
 单线程写测试:		13202.46 MB/s
------------------磁盘dd读写测试--感谢lemonbench开源--------------------
 -> 磁盘IO测试中 (4K Block/1M Block, Direct Mode)
 测试操作		写速度					读速度
 100MB-4K Block		1.8 MB/s (432 IOPS, 59.24s)		1.6 MB/s (391 IOPS, 65.32s)
 1GB-1M Block		142 MB/s (135 IOPS, 7.41s)		154 MB/s (146 IOPS, 6.81s)
---------------------磁盘fio读写测试--感谢yabs开源----------------------
Block Size | 4k            (IOPS) | 64k           (IOPS)
  ------   | ---            ----  | ----           ---- 
Read       | 33.77 MB/s    (8.4k) | 100.92 MB/s   (1.5k)
Write      | 33.87 MB/s    (8.4k) | 101.45 MB/s   (1.5k)
Total      | 67.65 MB/s   (16.9k) | 202.37 MB/s   (3.1k)
           |                      |                     
Block Size | 512k          (IOPS) | 1m            (IOPS)
  ------   | ---            ----  | ----           ---- 
Read       | 167.54 MB/s    (327) | 155.43 MB/s    (151)
Write      | 176.44 MB/s    (344) | 165.79 MB/s    (161)
Total      | 343.99 MB/s    (671) | 321.23 MB/s    (312)
---------------------流媒体解锁--感谢sjlleo开源-------------------------
以下测试的解锁地区是准确的，但是不是完整解锁的判断可能有误，这方面仅作参考使用
----------------Youtube----------------
[IPv4]
连接方式: Youtube Video Server
视频缓存节点地域: 日本 东京(NRT20S05)
Youtube识别地域: 日本(JP)
[IPv6]
连接方式: Youtube Video Server
视频缓存节点地域: 日本 东京(NRT20S05)
Youtube识别地域: 日本(JP)
----------------Netflix----------------
[IPv4]
Netflix在您的出口IP所在的国家不提供服务
[IPv6]
Netflix在您的出口IP所在的国家不提供服务
---------------DisneyPlus---------------
[IPv4]
当前IPv4出口解锁DisneyPlus
区域：日本区
[IPv6]
当前IPv6出口解锁DisneyPlus
区域：日本区
解锁Youtube，Netflix，DisneyPlus上面和下面进行比较，不同之处自行判断
----------------流媒体解锁--感谢RegionRestrictionCheck开源--------------
 以下为IPV4网络测试，若无IPV4网络则无输出
============[ Multination ]============
 Dazn:					Yes (Region: JP)
 HotStar:				No
 Disney+:				No
 Netflix:				No
 YouTube Premium:			Yes (Region: JP)
 Amazon Prime Video:			Yes (Region: JP)
 TVBAnywhere+:				Yes
 iQyi Oversea Region:			JP
 Viu.com:				No
 YouTube CDN:				Tokyo 
 Netflix Preferred CDN:			Failed
 Spotify Registration:			No
 Steam Currency:			JPY
 ChatGPT:				Only Available with Web Browser
 Bing Region:				JP
=======================================
 以下为IPV6网络测试，若无IPV6网络则无输出
============[ Multination ]============
 Dazn:					Failed (Network Connection)
 HotStar:				No
 Disney+:				No
 Netflix:				No
 YouTube Premium:			Yes (Region: JP)
 Amazon Prime Video:			Unsupported
 TVBAnywhere+:				Failed (Network Connection)
 iQyi Oversea Region:			Failed
 Viu.com:				Failed
 YouTube CDN:				Tokyo 
 Netflix Preferred CDN:			Failed
 Spotify Registration:			No
 Steam Currency:			Failed (Network Connection)
 ChatGPT:				No
 Bing Region:				JP
=======================================
---------------TikTok解锁--感谢lmc999的源脚本及fscarmen PR--------------
 Tiktok Region:		【JP】
-------------------欺诈分数以及IP质量检测--本脚本原创-------------------
数据仅作参考，不代表100%准确，如果和实际情况不一致请手动查询多个数据库比对
以下为各数据库编号，输出结果后将自带数据库来源对应的编号
ipinfo数据库 ①  | scamalytics数据库 ②  | virustotal数据库 ③  | abuseipdb数据库 ④  | ip2location数据库   ⑤
ip-api数据库 ⑥  | ipwhois数据库     ⑦  | ipregistry数据库 ⑧  | ipdata数据库    ⑨  | ipgeolocation数据库 ⑩
欺诈分数(越低越好): 44②
abuse得分(越低越好): 0④
IP类型: 
  使用类型(usage_type):hosting①  Data Center/Web Hosting/Transit⑤  hosting⑧  business⑨  
  公司类型(company_type):hosting①  business⑧  
  云服务提供商(cloud_provider):  Yes⑧ 
  数据中心(datacenter):  Yes⑥   No⑨ 
  移动网络(mobile):  No⑥ 
  代理(proxy):  No① ②   Yes⑥ ⑦ ⑧ ⑨ ⑩ 
  VPN(vpn):  No① ②   Yes⑦ ⑧ 
  TOR(tor):  No① ② ⑦ ⑧ ⑨ 
  TOR出口(tor_exit):  No⑧ 
  搜索引擎机器人(search_engine_robot):② 
  匿名代理(anonymous):  Yes⑦ ⑧   No⑨ 
  攻击方(attacker):  No⑧ ⑨ 
  滥用者(abuser):  No⑧ ⑨ 
  威胁(threat):  No⑧ ⑨ 
  iCloud中继(icloud_relay):  No① ⑧ ⑨ 
  未分配IP(bogon):  No⑧ ⑨ 
黑名单记录统计(有多少个黑名单网站有记录): 无害0 恶意0 可疑0 未检测89 ③
Google搜索可行性：YES
端口25检测:
  本地: No
  163邮箱：No
------以下为IPV6检测------
欺诈分数(越低越好): 38②
abuse得分(越低越好): 0④
IP类型: Data Center/Web Hosting/Transit⑤
----------------三网回程--感谢zhanghanyun/backtrace开源-----------------
国家: JP 城市: Ōi 服务商: AS20473 The Constant Company, LLC
北京电信 219.141.136.12  测试超时
北京联通 202.106.50.1    联通4837[普通线路]           
北京移动 221.179.155.161 移动CMI [普通线路]           
上海电信 202.96.209.133  电信163 [普通线路]           
上海联通 210.22.97.1     联通4837[普通线路]           
上海移动 211.136.112.200 移动CMI [普通线路]           
广州电信 58.60.188.222   电信163 [普通线路]           
广州联通 210.21.196.6    联通4837[普通线路]           
广州移动 120.196.165.24  移动CMI [普通线路]           
成都电信 61.139.2.69     电信163 [普通线路]           
成都联通 119.6.6.6       联通4837[普通线路]           
成都移动 211.137.96.205  移动CMI [普通线路]           
---------------------回程路由--感谢fscarmen开源及PR---------------------
依次测试电信/联通/移动经过的地区及线路，核心程序来自ipip.net或nexttrace，请知悉!
广州电信 58.60.188.222
18.33 ms  *  共享地址
0.88 ms  *  局域网
1.31 ms  *  局域网
4.25 ms  AS2914  日本, 东京都, 东京, ntt.com
0.79 ms  AS2914  日本, 东京都, 东京, ntt.com
110.80 ms  AS2914  中国, 广东, 广州, ntt.com
111.81 ms  AS4134  中国, 广东, chinatelecom.com.cn, 电信
111.88 ms  AS4134  中国, 广东, 广州, chinatelecom.com.cn, 电信
115.44 ms  AS4134  中国, 广东, 深圳, chinatelecom.com.cn, 电信
114.25 ms  AS4134  中国, 广东, 深圳, chinatelecom.com.cn, 电信
广州联通 210.21.196.6
21.99 ms  *  共享地址
0.93 ms  *  局域网
0.81 ms  *  局域网
0.64 ms  AS2914  日本, 东京都, 东京, ntt.com
1.80 ms  AS2914  日本, 东京都, 东京, ntt.com
1.38 ms  AS2914  日本, 东京都, 东京, ntt.com
59.46 ms  AS4837  中国, 广东, 广州, chinaunicom.com, 联通
73.48 ms  AS4837  中国, 广东, 广州, chinaunicom.com, 联通
67.05 ms  AS17816  中国, 广东, 深圳, chinaunicom.com, 联通
67.85 ms  AS17623  中国, 广东, 深圳, chinaunicom.com, 联通
63.18 ms  AS17623  中国, 广东, 深圳, chinaunicom.com, 联通
广州移动 120.196.165.24
0.27 ms  *  共享地址
0.93 ms  *  局域网
0.31 ms  *  局域网
8.31 ms  AS1299  日本, 大阪府, 大阪, telia.com
112.98 ms  AS1299  美国, 加利福尼亚州, 洛杉矶, telia.com
158.91 ms  AS1299  美国, 加利福尼亚州, 圣何塞, telia.com
160.39 ms  AS1299  美国, 加利福尼亚州, 圣何塞, telia.com
154.38 ms  AS58453  美国, 加利福尼亚州, 圣何塞, chinamobile.com, 移动
280.66 ms  AS58453  中国, 广东, 广州, chinamobile.com, 移动
320.46 ms  AS9808  中国, 广东, 广州, chinamobile.com, 移动
311.76 ms  AS9808  中国, 广东, 广州, chinamobile.com, 移动
172.70 ms  AS9808  中国, 广东, 广州, chinamobile.com, 移动
174.23 ms  AS9808  中国, 广东, 广州, chinamobile.com, 移动
173.31 ms  AS56040  中国, 广东, 深圳, chinamobile.com, 移动
--------------------自动更新测速节点列表--本脚本原创--------------------
位置		 上传速度	 下载速度	 延迟	  丢包率
Speedtest.net	 8261.33 Mbps	 6630.24 Mbps	 0.31	  NULL
日本东京	 754.86 Mbps	 3589.83 Mbps	 1.04	  28.6%
中国香港	 761.05 Mbps	 507.00 Mbps	 54.32	  NULL
联通海南	 147.60 Mbps	 990.09 Mbps	 125.74	  NULL
联通Fuzhou	 83.17 Mbps	 289.37 Mbps	 230.06	  6.0%
电信Nanjing5G	 74.17 Mbps	 0.97 Mbps	 224.02	  24.7%
移动Chengdu	 55.31 Mbps	 748.60 Mbps	 408.82	  13.0%
------------------------------------------------------------------------
 总共花费      : 9 分 32 秒
 时间          : Gum Qun 19  7:25:08 saaku UTC 2024
------------------------------------------------------------------------