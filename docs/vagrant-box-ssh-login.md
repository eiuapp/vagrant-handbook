
如何通过 ssh 登录 vagrant box

得到 ssh-config

```
D:\vag-files\ubuntu16
λ  vagrant ssh-config
WARNING: Vagrant has detected the `vagrant-triggers` plugin. This plugin conflicts
with the internal triggers implementation. Please uninstall the `vagrant-triggers`
plugin and run the command again if you wish to use the core trigger feature. To
uninstall the plugin, run the command shown below:

  vagrant plugin uninstall vagrant-triggers

Note that the community plugin `vagrant-triggers` and the core trigger feature
in Vagrant do not have compatible syntax.

To disable this warning, set the environment variable `VAGRANT_USE_VAGRANT_TRIGGERS`.
Host default
  HostName 127.0.0.1
  User vagrant
  Port 2222
  UserKnownHostsFile /dev/null
  StrictHostKeyChecking no
  PasswordAuthentication no
  IdentityFile D:/vag-files/ubuntu16/.vagrant/machines/default/virtualbox/private_key
  IdentitiesOnly yes
  LogLevel FATAL

D:\vag-files\ubuntu16
```

ssh 必须带上 IdentityFile

```
λ  ssh vagrant@127.0.0.1 -p 2222
The authenticity of host '[127.0.0.1]:2222 ([127.0.0.1]:2222)' can't be established.
ECDSA key fingerprint is SHA256:/2ppXijFcqY4ls2N3vmB7tCec39reYLq3wFASj1yujM.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '[127.0.0.1]:2222' (ECDSA) to the list of known hosts.
vagrant@127.0.0.1: Permission denied (publickey).
D:\vag-files\ubuntu16
λ  ssh vagrant@127.0.0.1 -p 2222 -i D:/vag-files/ubuntu16/.vagrant/machines/default/virtualbox/private_key
Welcome to Ubuntu 16.04.6 LTS (GNU/Linux 4.4.0-145-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  Get cloud support with Ubuntu Advantage Cloud Guest:
    http://www.ubuntu.com/business/services/cloud

12 packages can be updated.
2 updates are security updates.

New release '18.04.2 LTS' available.
Run 'do-release-upgrade' to upgrade to it.


Last login: Fri Apr 19 06:30:08 2019 from 10.0.2.2
vagrant@ubuntu-xenial:~$ exit
logout
Connection to 127.0.0.1 closed.
D:\vag-files\ubuntu16
```

