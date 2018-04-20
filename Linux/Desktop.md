[Linux CentOS 7的图形界面安装（GNOME、KDE等）](https://jingyan.baidu.com/article/0964eca26fc3b38284f53642.html)  

```
yum groupinstall "X Window System"  
yum grouplist   
yum groupinstall "GNOME Desktop"
reboot
startx
```


[为 Linux 实例安装图形化桌面](https://help.aliyun.com/knowledge_detail/41227.html)  
```
yum groups install "MATE Desktop"
systemctl set-default graphical.target
reboot
yum install xorg-x11-drv-evdev
Xorg -configure
cp xorg.conf.new /etc/X11/xorg.conf
```


 /etc/X11/xorg.conf   
 
 ```
Section "InputDevice"
Identifier "Keyboard0"
Driver "evdev"       #修改为 evdv
Option "Device" "/dev/input/event3"
EndSection
Section "InputDevice"
Identifier "Mouse0"
Driver "evdev"       #修改为 evdv
Option "Device" "/dev/input/event5"
Option "Mode" "Absolute"
EndSection
 ```
 
 
 [忘掉VNC/RDP，拿起手中的MobaXterm轻松上手远程桌面](https://www.cnblogs.com/sjqlwy/p/mobaxterm.html)
