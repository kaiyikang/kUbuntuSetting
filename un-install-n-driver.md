## 基础

查看nouveau驱动
lspci | grep nouveau

使用它查看你的显卡型号
ubuntu-drivers devices
查看推荐驱动，例如：
GM107M [GeForce GTX 860M]，推荐安装的版本号是：nvidia-driver-390 - distro non-free recommended

下载对应的型号的驱动，例如我的型号是GF 940MX
https://www.nvidia.com/Download/index.aspx

## 禁用nouveau驱动
sudo vim /etc/modprobe.d/blacklist-nouveau.conf  
输入
blacklist nouveau  
options nouveau modset=0
刷新刚才的更新
sudo update-initramfs -u  



## 安装新的驱动 （参考：https://zhuanlan.zhihu.com/p/59618999）


如果同意安装推荐版本，那我们只需要终端输入：sudo ubuntu-drivers autoinstall 就可以自动安装了。

当然我们也可以使用 apt 命令安装自己想要安装的版本，比如我想安装 340 这个版本号的版本，终端输入：sudo apt install nvidia-340 就自动安装了。

安装过程中按照提示操作，除非你知道每个提示的真实含义，否则所有的提示都选择默认就可以了，安装完成后重启系统，NVIDIA 显卡就可以正常工作了。安装完成后你可以参照 https://linuxconfig.org/benchmark-your-graphics-card-on-linux 上的介绍测试你的显卡。


或者使用第三方PPA 安装
添加 PPA 软件仓库：sudo add-apt-repository ppa:graphics-drivers/ppa，需要输入用户密码，按照提示还需要按下 Enter 键。
更新软件索引：sudo apt update

最后查看是否安装成功
nvidia-smi

## 额外信息
如果需要删除旧的n卡驱动
sudo apt-get remove nvidia-* sudo apt-get autoremove 

