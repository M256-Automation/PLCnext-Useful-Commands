# __PLCnext Useful Commands__
A list of useful commands on PLCnext terminal

### FW update (*.raucb file placed in /opt/plcnext)
```
sudo update-axcf2152
```

### Check firmware version:
```
cat /etc/plcnext/arpversion
```

### Reboot
```
sudo reboot
```

### Reset 1 - without deleting FW update
```
sudo recover-axcf2152 1      
```

### Reset 2 - deleting FW update - factory default
```
sudo recover-axcf2152 2      
```

### PLC start/stop/restart
```
sudo /etc/init.d/plcnext start
```
```
sudo /etc/init.d/plcnext stop
```
```
sudo /etc/init.d/plcnext restart
```

### Check log file as stream:
```
tail -f -n 20 /opt/plcnext/logs/Output.log
```

where "-n 20" is the number of previous lines to show 

### Transfer C++ cross-compiled libraries .so
move file in /usr/local/lib and then
```
cd /usr/local/lib
ln -sf _nomelibreria_.so
sudo ldconfig
```

### IP Assignment
```
ifconfig eth0 192.168.1.x netmask 255.255.255.0
```

### Gateway Assignment
```
route add default gateway 192.168.1.1
```

### DNS Assignment
```
sudo echo "nameserver 8.8.8.8" > /etc/resolv.conf
```

### DNS Check?
```
cat /etc/resolv.conf 
```

### File search
```
find . -name tecmint.txt
```
Looks in the current directory and all sub-directories

With _root_ you can search in _every_ directory

### Guix
```
guix package  --search=zabbix
guix install zabbix-agentd
```

## Memory Check
```
top
```
