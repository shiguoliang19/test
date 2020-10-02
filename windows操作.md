管理员身份运行

```cmd
rem 系统属性
sysdm.cpl
rem 控制面板
control
rem 禁用网卡
netsh interface set interface "WLAN" disabled
rem 启用网卡
netsh interface set interface "WLAN" enabled
rem 查看电脑插入的usb记录
reg query HKLM\System\currentcontrolset\enum\usbstor /s >c:\usb.txt
```

