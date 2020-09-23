+++
title = "vagrant install solaris10"
author = ["eiuapp"]
description = "vagrant install solaris10"
date = 2020-09-10T00:00:00+08:00
lastmod = 2020-09-23T10:19:58+08:00
draft = false
weight = 90
+++

## vagrant install solaris10 {#vagrant-install-solaris10}

使用solaries安装编译nginx, 要搭建一个测试环境，所以用vagrant安装个solaris10.

```text
D:\迅雷下载
λ  vagrant.exe box add solaris10-minimal-version0.0.1 .\tnarik-boxes-solaris10-minimal-versions0.0.1.box
==> box: Box file was not detected as metadata. Adding it directly...
==> box: Adding box 'solaris10-minimal-version0.0.1' (v0) for provider:
    box: Unpacking necessary files from: file://D:/%D1%B8%C0%D7%CF%C2%D4%D8/tnarik-boxes-solaris10-minimal-versions0.0.1.box
    box: Progress: 100% (Rate: 37.8M/s, Estimated time remaining: --:--:--)
==> box: Successfully added box 'solaris10-minimal-version0.0.1' (v0) for 'virtualbox'!
D:\迅雷下载
λ  vagrant box list
solaris10-minimal-version0.0.1 (virtualbox, 0)
D:\迅雷下载
λ
```
