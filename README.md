# K8CscanAggressor
K8Cscan for Cobalt Strike 3.x Aggressor Script
### K8Cscan
K8Cscan一款专用于大型内网渗透的高并发插件化扫描神器，包含信息收集、网络资产、漏洞扫描、密码爆破、漏洞利用，支持批量A段/B段/C段以及跨网段扫描。5.3版本内置27个功能模块,通过各种协议以及方法快速获取目标网络存活主机IP、计算机名、工作组、网络共享、网卡物理地址、操作系统版本、网站域名、Web中间件、路由器（Cisco）、数据库等网络资产信息,内置MS17-010(SMB漏洞)、Weblogic漏洞检测，内置6种密码认证爆破3种数据库(Mysql、Oracle、MSSQL)、FTP密码爆破(文件服务器)、SSH密码爆破(Linux主机)、IPC/WMI两种方式爆破Windows主机密码，Web指纹识别模块可识别62种Web应用。高度自定义插件支持.NET程序集、DLL(C#/Delphi/VC)、PowerShell等语言编写的插件以及无编程功底通过配置INI加载任意程序命令，可快速扩展扫描或利用能力。支持Cobalt Strike联动使用27个功能扫描目标内网或跳板扫描外网目标，可快速拓展内网进行横向移动。
### CS脚本
Cscan 5.3支持Cobalt Strike,内置27个功能模块<br>
加载脚本K8Cscan.cna,通过Cscan help查看用法<br>
https://github.com/k8gege/K8CscanAggressor<br>
### 应用场景
CS命令行下扫描目标内网,无需代理转发扫描收集信息、密码爆破等<br>
跳板扫描外网资产(即无需代理直接通过在控机器扫描其它目标资产)<br>
### 0.Cobalt Strike联动
![](https://github.com/k8gege/K8CScan/blob/master/Images/CobaltStrike.gif)
### 1.SmbScan MS17-010漏洞扫描
IP、SMB漏洞、机器名、操作系统版本<br>
![SmbScan](https://github.com/k8gege/K8CScan/blob/master/Images/MS17010.PNG)
### 2.OSscan 操作系统探测
通过SMB、多端口、Banner等方式探测（存活主机、主机名、域名、操作系统版本、开放服务等）<br>
![OSscan](https://github.com/k8gege/K8CScan/blob/master/Images/OSscan.PNG)
### 3.OnlinePC 存活主机扫描
也支持检测主机名/域名是否存活,结果IP、Mac、机器名<br>
![OnlinePC](https://github.com/k8gege/K8CScan/blob/master/Images/OnlinePC.PNG)
### 4.WebScan Web扫描
内网站点扫描，获取服务器Banner、网页标题<br>
![WebScan](https://github.com/k8gege/K8CScan/blob/master/Images/WebScan.PNG)
### 5.FtpScan FTP密码扫描
需上传user.txt和pass.txt至beacon工作目录<br>
![FtpScan](https://github.com/k8gege/K8CScan/blob/master/Images/FtpScan.PNG)
### 6.WmiScan Win方式爆破Windows密码（IPC被拒绝时可尝试WMI）
Wmi方式批量爆破内网主机帐密,需上传user.txt和pass.txt至工作目录<br>
![WmiScan](https://github.com/k8gege/K8CScan/blob/master/Images/WmiScan.PNG)
### 7.CiscoScan 思科设备扫描
(IP、设备型号、主机名、Boot、硬件版本)<br>
![CiscoScan](https://github.com/k8gege/K8CScan/blob/master/Images/CiscoScan.PNG)
### 8.UrlScan C段域名URL扫描
通过源码获取域名或URL，但不验证IP,适用于内网扫描时，目标域名指向外网IP<br>
或者通过域名判断内网站点是何产品，比如出现cisco.com域名，说明此为cisco设备<br>
![UrlScan](https://github.com/k8gege/K8CScan/blob/master/Images/UrlScan.PNG)
### 9.SameWeb C段旁站扫描
通过源码获取域名并验证IP，返回正确的同服站点,非bing或爱站等方式,即内网不可上网也可扫描<br>
验证IP主要适用于，外网扫描时旁站，因为获取的域名指向外网时，无法通过IP判断是否属于同服<br>
![SameWeb](https://github.com/k8gege/K8CScan/blob/master/Images/SameWeb.PNG)
### 10.WeblogicExp & WeblogicPoc
Weblogic漏洞扫描两个模块,一个是只扫描是否存在漏洞，另一个是扫描并且GetShell<br>
![WeblogicExp](https://github.com/k8gege/K8CScan/blob/master/Images/WeblogicExp.PNG)
### 11.EnumMSSQL 枚举局域网MS SQL SERVER数据库主机
和PowerUpSql一样不一定能获取到SQL版本
![](https://github.com/k8gege/K8CScan/blob/master/Images/EnumMSSQL.PNG)
### 12.EnumShare 枚举局域网共享资源
![](https://github.com/k8gege/K8CScan/blob/master/Images/EnumShare.PNG)
### 13.MssqlScan MSSQL数据库密码爆破
![](https://github.com/k8gege/K8CScan/blob/master/Images/MssqlScan.PNG)
### 14.MysqlScan MySQL数据库密码爆破
![](https://github.com/k8gege/K8CScan/blob/master/Images/MysqlScan.PNG)
### 15.SSHscan SSH主机密码爆破
![](https://github.com/k8gege/K8CScan/blob/master/Images/SSHscan.PNG)
### 16.OracleScan Oracle数据库密码爆破
![](https://github.com/k8gege/K8CScan/blob/master/Images/OracleScan.PNG)
### 17.HostIP 域名解析/主机名转IP
![](https://github.com/k8gege/K8CScan/blob/master/Images/HostIP.PNG)
### 18.WhatCMS 指纹识别支持62种CMS
url.txt指定站点或批量站点扫描,也可扫描整个C段部分web端口对应CMS
![](https://github.com/k8gege/K8CScan/blob/master/Images/WhatCMS.png)
### 19.IpcScan Windows密码爆破(Wmi被拒绝时可尝试Ipc)
![](https://github.com/k8gege/K8CScan/blob/master/Images/IpcScan.PNG)
### 20.WebScan2 Web信息扫描含CMS识别
url.txt指定站点或批量站点扫描,也可扫描整个C段中Web信息
![](https://github.com/k8gege/K8CScan/blob/master/Images/WebScan2.PNG)
### 21.EnBase64/DeBase64  Base64密码批量加密解密
![](https://github.com/k8gege/K8CScan/blob/master/Images/Base64.PNG)
### 22.EnHex/DeHex  Hex密码批量加密解密(3种格式)
![](https://github.com/k8gege/K8CScan/blob/master/Images/DeHex.PNG)
### 23.SmbScan Windows密码爆破(Wmi被拒绝时可尝试,记录错误日志)
![](https://github.com/k8gege/K8CScan/blob/master/Images/SmbScan.png)
### 24.PhpStudyPoc PhpStudy后门检测
![](https://github.com/k8gege/K8CScan/blob/master/Images/PhpStudyPoc.PNG)
### 25.DomainIP 域名解析
![](https://github.com/k8gege/K8CScan/blob/master/Images/DomainIP.gif)
### 26.SubDomain 子域名爆破
需域名字典SubDomain.dic<br>
例子: Cscan baidu.com SubDomain<br>
![](https://github.com/k8gege/K8CScan/blob/master/Images/SubDomain.gif)
### 27.WebDir Web目录扫描
![](https://github.com/k8gege/K8CScan/blob/master/Images/WebDir.PNG)
