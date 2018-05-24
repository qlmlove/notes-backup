
## 执行下边命令

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE

## 输出报错

Executing: /tmp/apt-key-gpghome.IbS492SRkm/gpg.1.sh --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE
gpg: failed to start the dirmngr '/usr/bin/dirmngr': 没有那个文件或目录
gpg: connecting dirmngr at '/run/user/0/gnupg/d.hdko37ye61fh3rf45pjymggp/S.dirmngr' failed: 没有那个文件或目录
gpg: keyserver receive failed: No dirmngr

## 解决办法

sudo apt-get install dirmngr

