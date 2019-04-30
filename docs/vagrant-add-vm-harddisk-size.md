vagrant 增加硬盘容量实践记录

https://www.jianshu.com/p/b1acd5d8d53e

严格来说,这篇文章,应该属于virtualbox

## env

- os: windows10
- virtualbox: 6.0
- powershell: 管理员权限打开

## 找到 VM 所在文件夹. ##

管理/全局设置/默认虚拟电脑位置 

打开virtualbox面板, 点击vm, 设置,存储,选中,明细,位置

```bash
C:\Program Files\soft\cmder
λ  cd 'C:\Users\a\VirtualBox VMs\ubuntu16_default_1555655333404_65452\'
C:\Users\a\VirtualBox VMs\ubuntu16_default_1555655333404_65452警告: Missing git support, install posh-git with 'Install-Module posh-git' and restart cmder.
PS>ls


    目录: C:\Users\a\VirtualBox VMs\ubuntu16_default_1555655333404_65452


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2019/4/29     18:08                Logs
d-----        2019/4/20     11:47                Snapshots
-a----        2019/4/29     18:08         196608 ubuntu-xenial-16.04-cloudimg-configdrive.vmdk
-a----        2019/4/30      8:23    10298523648 ubuntu-xenial-16.04-cloudimg.vmdk
-a----        2019/4/29     18:09           7596 ubuntu16_default_1555655333404_65452.vbox
-a----        2019/4/29     18:08           6804 ubuntu16_default_1555655333404_65452.vbox-prev

```

## 确保 VBoxManage 命令可用

如果在有安装VIRTUALBOX的情况下,而没有找到VBoxManage命令,是因为没有把此命令加入到环境变量.

https://www.jianshu.com/p/a665cf386b0e

在 powershell 下, `VBoxManage --help`


## 执行改格式的命令 ##

```bash
PS>VBoxManage clonehd "ubuntu-xenial-16.04-cloudimg.vmdk" "ubuntu-xenial-16.04-cloudimg.vdi" --format vdi
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
Clone medium created in format 'vdi'. UUID: 406ede3a-b9d8-4b60-9675-893eb9141145
C:\Users\a\VirtualBox VMs\ubuntu16_default_1555655333404_65452警告: Missing git support, install posh-git with 'Install-Module posh-git' and restart cmder.
```

resize
单位为M，20480即为20G

```bash
PS>VBoxManage modifyhd "ubuntu-xenial-16.04-cloudimg.vdi" --resize 40960
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
C:\Users\a\VirtualBox VMs\ubuntu16_default_1555655333404_65452警告: Missing git support, install posh-git with 'Install-Module posh-git' and restart cmder.
PS>
```

## 重新挂载 ##

`ubuntu16_default_1555655333404_65452`是文件夹名,或者说是VM名

```bash
PS>VBoxManage storageattach ubuntu16_default_1555655333404_65452 --storagectl "SCSI" --port 0 --device 0 --type hdd --medium ubuntu-xenial-16.04-cloudimg.vdi
C:\Users\a\VirtualBox VMs\ubuntu16_default_1555655333404_65452警告: Missing git support, install posh-git with 'Install-Module posh-git' and restart cmder.
```

--storagectl "SCSI" 根据不同的操作系统类型不通，常见的还有 "SATA Contr"

## vagrant up ##

```bash
PS>cd D:\vag-files\ubuntu16\
D:\vag-files\ubuntu16
λ  vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Clearing any previously set forwarded ports...
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
    default: Adapter 2: bridged
==> default: Forwarding ports...
    default: 222 (guest) => 3333 (host) (adapter 1)
    default: 2376 (guest) => 2375 (host) (adapter 1)
==> default: Running 'pre-boot' VM customizations...
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:22
    default: SSH username: vagrant
    default: SSH auth method: private key
D:\vag-files\ubuntu16
λ  ==> default: Waiting for cleanup before exiting...
Vagrant exited after cleanup due to external interrupt.
D:\vag-files\ubuntu16
```

通过 `du -h` 查看.

