title: windows
date: 2015-06-15 22:38:01
tags:
    - windows
---

# PowerShell

http://www.howtogeek.com/50236/customizing-your-powershell-profile/
如果无法加载文件，
用管理员执行一次set-executionpolicy remotesigned即可


```
route delete 0.0.0.0 mask 0.0.0.0 172.18.0.1
route delete 10.10.10.0
route delete 172.18.0.0
route delete 172.21.0.0
route delete 172.22.0.0
route add 10.10.10.0 mask 255.255.255.0 10.10.11.111
route add 172.18.0.0 mask 255.255.0.0 172.18.0.1 IF 12
route add 172.21.0.0 mask 255.255.0.0 172.18.0.1 IF 12
route add 172.22.0.0 mask 255.255.0.0 172.18.0.1 IF 12
pause

route print
```
