+++
title = "windows下切换vagrant_home目录"
author = ["eiuapp"]
description = "windows下切换vagrant_home目录"
date = 2020-09-10T00:00:00+08:00
lastmod = 2020-09-23T11:33:50+08:00
draft = false
weight = 90
+++

## windows下切换vagrant\_home目录 {#windows下切换vagrant-home目录}


### step {#step}

管理员打开 cmd

```text
C:\Windows\system32>setx VAGRANT_HOME "E:\ProgramFiles\VagrantHome"

成功: 指定的值已得到保存。

C:\Windows\system32>set VAGRANT_HOME
环境变量 VAGRANT_HOME 没有定义

C:\Windows\system32>set path
Path=C:\Program Files (x86)\Common Files\NetSarang;C:\ProgramData\Oracle\Java\ja
vapath;C:\Windows\system32;C:\Windows;C:\Windows\System32\Wbem;C:\Windows\System
32\WindowsPowerShell\v1.0\;C:\Program Files\nodejs\;C:\Program Files (x86)\Calib
re2\;C:\HashiCorp\Vagrant\bin;C:\Program Files\Git\cmd;C:\Program Files\Git\ming
w64\bin;C:\Program Files\Git\usr\bin;C:\Users\tony\Anaconda;C:\Users\tony\Anacon
da\Scripts;C:\Wind\Wind.NET.Client\WindNET\bin\;C:\Users\tony\AppData\Roaming\np
m;C:\Program Files\nodejs\node.exe;C:\Program Files (x86)\Microsoft VS Code\bin
PATHEXT=.COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC

C:\Windows\system32>setx VAGRANT_HOME "E:\ProgramFiles\VagrantHome"

成功: 指定的值已得到保存。

C:\Windows\system32>set VAGRANT_HOME
环境变量 VAGRANT_HOME 没有定义

C:\Windows\system32>
```

这时，要关闭此cmd窗口，然后打开一个新的cmd窗口。

```text
C:\Users\tony>set path
Path=C:\Program Files (x86)\Common Files\NetSarang;C:\ProgramData\Oracle\Java\ja
vapath;C:\Windows\system32;C:\Windows;C:\Windows\System32\Wbem;C:\Windows\System
32\WindowsPowerShell\v1.0\;C:\Program Files\nodejs\;C:\Program Files (x86)\Calib
re2\;C:\HashiCorp\Vagrant\bin;C:\Program Files\Git\cmd;C:\Program Files\Git\ming
w64\bin;C:\Program Files\Git\usr\bin;C:\Users\tony\Anaconda;C:\Users\tony\Anacon
da\Scripts;C:\Wind\Wind.NET.Client\WindNET\bin\;C:\Users\tony\AppData\Roaming\np
m;C:\Program Files\nodejs\node.exe;C:\Program Files (x86)\Microsoft VS Code\bin
PATHEXT=.COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC

C:\Users\tony>set vagrant_home
VAGRANT_HOME=E:\ProgramFiles\VagrantHome

C:\Users\tony>
```


### ref {#ref}

-   <https://harvsworld.com/2014/change-vagrant%5C%5Fhome-directory-windows/>
