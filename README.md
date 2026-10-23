# phpStudy v8.1 离线版一键安装包（小皮面板）（内含所需VC运行库）

phpStudy8.1是个很好用的PHP集成环境软件，因为近期项目需要在未联网的内网用到phpStudy，所以自己动手做成了离线版，在官方原版的基础上新增配置了PHP8.1、PHP8.3、PHP8.4、PHP8.5等版本，即目前集成了PHP5.2至PHP8.5、MySQL5.0至MySQL8.0、Apache2.4、Nginx1.15至Nginx1.25、redis3.0、FTP0.9.6、FileZilla3.50、composer1.8至composer2.5等全部版本。考虑到很多网友可能也有这个需求，所以这里共享一下phpstudy8.1离线版一键安装包。该版本已配置好的文件，无需安装，直接复制粘贴到D盘后，解压后就可以用了。

### 支持的操作系统版本

支持的操作系统版本为：Win2008 R2/2012/2016/7/10等。

### phpstudy8.1离线版安装方法

按照“安装说明.txt”，复制粘贴后解压即可正常使用。


### 安装说明

1、将phpstudy_pro.part01.rar至phpstudy_pro.part10.rar共10个压缩包下载到D盘，在“phpstudy_pro.part01.rar”文件上右键，解压缩到D盘根目录下，即：D:\phpstudy_pro\。

注意：务必解压到D盘，否则可能运行phpstudy失败。如果你不是默认目录D:\phpstudy_pro\，可以自行修改每个软件的配置文件，如php.ini文件，以php8.0.30nts为例，将里面的：extension_dir = "D:\phpstudy_pro\Extensions\php\php8.0.30nts\ext"修改为对应的目录即可。有点复杂，建议使用默认路径。

2、安装VC运行库：打开“VC运行库”目录，双击目录里的“VC_redist.x64--Visual Studio 2015、2017、2019 和 2022 年.exe”和“VC_14_redist.x64”等文件安装，安装后即可正常运行PHP8.0+各个版本。如还发现某个PHP版本运行错误或者页面加载时间过长，安装PHP版本对应的VC运行库即可。

3、打开：“D:\phpstudy_pro\COM\phpstudy_pro.exe”（可自行创建快捷方式到桌面），双击打开这个可执行文件即可运行phpstudy8.1离线版。

如需要更多PHP版本，请到官网下载：https://downloads.php.net/~windows/releases/archives/



### 【2026-10-22 更新说明】
近日，PHP曝出两个严重安全漏洞（代号“php2shell”），漏洞编号为CVE-2026-109618、CVE-2026-109619。该漏洞可导致未经身份验证的远程攻击者通过发送特制POST请求，触发内存破坏并最终实现远程代码执行，从而获取服务器控制权限。漏洞影响PHP 8.5.x＜8.5.12、PHP 8.4.x＜8.4.27、PHP 8.3.x＜8.3.36、PHP 8.2.x＜8.2.35以及8.1以前版本。由于漏洞危害严重，已导致多国网站大规模紧急下线。PHP作为一种开源编程语言，广泛应用于WordPress、Drupal、Joomla和Magento等网站平台开发。目前，PHP官方已发布最新版本（8.5.12、8.4.27、8.3.36、8.2.35）修复该漏洞，详见：https://www.php.net/archive/2026.php#2026-10-21-5 建议受影响用户及时更新至安全版本，消除安全隐患，严防发生网络攻击事件。

**目前，本离线安装包已经集成了PHP官方最新版本，请建站时尽量使用这些PHP版本：8.5.12、8.4.27、8.3.36、8.2.35。**


此外，已经针对PHP旧版本增加了临时缓解设置，以尽量减少被攻击的可能。主要更改php.ini代码设置如下：

> ; ============================================
>
> ; PHP2Shell (CVE-2026-109618 / CVE-2026-109619) 临时缓解配置
>
> ; 仅用于无法立即升级时的风险降低，并非完整修复
>
> ; ============================================
>
> ; --- 针对 CVE-2026-109619 (会话状态污染) 的缓解 ---
>
> ; 禁用会话上传进度功能即可；不要再设 cleanup=Off
>
> session.upload_progress.enabled = Off
>
> ; 通用会话加固（PHP < 5.5.2 不识别 strict_mode，属正常）
>
> session.use_strict_mode = 1
>
> session.use_only_cookies = 1
>
> session.cookie_httponly = 1
>
>
> ; --- 针对 CVE-2026-109618 (内存耗尽/OOM损坏) 的缓解 ---
>
> ; 关键：memory_limit=-1 建议在 PHP-FPM 池里用 php_admin_value 设置，
>
> ; 而不是只写在 php.ini，否则可能被应用 ini_set('memory_limit', ...) 覆盖
>
> memory_limit = -1
>
> ; 限制请求体大小；确保 upload_max_filesize < post_max_size
>
> ; 不需要上传可改为 8M
>
> post_max_size = 32M
>
> ; 输入嵌套层级；常规业务 6 一般够，复杂嵌套 API 可调到 10/16
>
> max_input_nesting_level = 6
>
> ; （仅 PHP 8.5 适用，更低版本忽略此项）关闭致命错误回溯，减少信息泄露
>
> ; fatal_error_backtraces = 0
>





### 感谢支持：

请到Gitee和GitHub给我点Star，谢谢您的支持！

Gitee：https://gitee.com/dengzhenhua/phpstudy

GitHub：https://github.com/dengcao/phpstudy

### 声明：

内含的php、phpStudy和VC运行库等版权归原作者所有，本人仅是做成离线版方便大家，如使用请遵守原版权方约定。

### 关于

开发：[邓草博客 blog.5300.cn](http://blog.5300.cn)

赞助：[品络互联 www.pinluo.com](http://www.pinluo.com)  &ensp;  [AI工具箱 5300.cn](http://5300.cn)  &ensp;  [汉语言文学网 hyywx.com](http://hyywx.com)  &ensp;  [源码社区 bbs.ym.gs](http://bbs.ym.gs)  &ensp;  [雄马 xiongma.cn](http://xiongma.cn) &ensp;  [优惠券 tm.gs](http://tm.gs)  &ensp;  [AI创作助手 aiczzs.com](http://aiczzs.com)  &ensp;  [AI一键生成 aiyjsc.com](http://aiyjsc.com)  &ensp;  [API中转站 apizz.vip](http://apizz.vip)
