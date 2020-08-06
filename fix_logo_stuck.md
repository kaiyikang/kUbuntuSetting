0. 安装完毕，机器重启，拔出u盘，如果是n卡独显，会有几率卡在logo处。

1.第一次修改
按住关机建，强制重启，来到引导grub画面，让光标位于ubuntu的位置，按e。
找到文字中的ro，修改成re，然后按f10，成功进入操作系统。

2. 彻底修改
sudo cp /boot/grub/grub.cfg ~/grub.cfg.bak # build a backup
sudo apt install vim

sudo chmod +w /boot/grub/grub.cfg # change only read mode to read/write mode
sudo vim /boot/grub/grub.cfg

在vim操作模式下，按/quiet 
找到包含该词的那行，在最后的位置，加一个空格，写入 acpi_osi=linux nomodeset
保存。

sudo update-grub # update grub
reboot

结束
