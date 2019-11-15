![CLEVER DATA GIT REPO](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/0-clever-data-github.png "李聪明的数据库")

# 更改SSMS图标颜色
#### Change SSMS Icon Color
**发布-日期: 2016年11月3日 (评论)**

![#](images/change-the-ssms-icon-color-to-green.png?raw=true "#")

## Contents

- [中文](#中文)
- [English](#English)
- [SQL Logic](#Logic)
- [Build Info](#Build-Info)
- [Author](#Author)
- [License](#License) 


## 中文
当你配置完新的数据库服务器时，你可能会发现SSMS服务器图标仍然是白色而不是绿色。这是因为你忘记了在服务器防火墙上启用远程管理设置。别担心。你可以重新登录服务器并直接对它进行设置。因为你可以直接在SSMS客户端执行此操作（前提是SQL服务账户
在操作系统中具有本地权限）。

## English
Whenever you’re done configuring a new Database Server you might notice the SSMS Server Icon is still representing a white color rather than green. This is because you forgot to enable the remote admin setting on the server firewall. No worries on logging back into the server and setting it directly cause you can do this directly from the SSMS client (provided the SQL Service account has local rights in the OS).

---
## Logic
```SQL
use master;
 
set nocount on
exec master..sp_configure 'show advanced options', '1';
exec master..sp_configure 'xp_cmdshell', '1' reconfigure with override; 
exec master..xp_cmdshell 'netsh firewall set service RemoteAdmin enable'; --deprecated, but still works.
 
exec master..xp_cmdshell 'netsh advfirewall firewall set rule group="remote administration" new enable=yes';
 
go

```

![#](images/change-the-ssms-icon-color-to-green-2.png?raw=true "#")

[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

- **李聪明的数据库 Lee's Clever Data**
- **Mike的数据库宝典 Mikes Database Collection**
- **李聪明的数据库** "Lee Songming"

[![Gist](https://img.shields.io/badge/Gist-李聪明的数据库-<COLOR>.svg)](https://gist.github.com/congmingshuju)
[![Twitter](https://img.shields.io/badge/Twitter-mike的数据库宝典-<COLOR>.svg)](https://twitter.com/mikesdatawork?lang=en)
[![Wordpress](https://img.shields.io/badge/Wordpress-mike的数据库宝典-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

---
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Lee Songming](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/1-clever-data-github.png "李聪明的数据库")

