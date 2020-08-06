## 基础

查看nouveau驱动
lspci | grep nouveau

使用它查看你的显卡型号
ubuntu-drivers devices

下载对应的型号的驱动，例如我的型号是GF 940MX
https://www.nvidia.com/Download/index.aspx

## 禁用nouveau驱动
sudo vim /etc/modprobe.d/blacklist-nouveau.conf  
输入
blacklist nouveau  
options nouveau modset=0
刷新刚才的更新
sudo update-initramfs -u  



## 安装新的驱动
sudo ubuntu-drivers autoinstall 
自动安装，然后重启

最后查看是否安装成功
nvidia -smi

## 额外信息
如果需要删除旧的n卡驱动
sudo apt-get remove nvidia-* sudo apt-get autoremove 

