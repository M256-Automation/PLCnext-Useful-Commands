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
ot, to get only the basic info

```
cat /etc/plcnext/arpversion | grep -i Arpversion | awk '{print $2}'
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
Move file in /usr/local/lib and then
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

### Memory Check
```
top
```


### Check Profinet Name
if you can log in to the PLC then you can take a look at the contents of this file:
```
nano /opt/plcnext/config/Io/PnS/PnS.local.config
```

### Python
#### Check Python version
```python3 --version```

### List all clients connected to server over 80 port
```
netstat -tn 2>/dev/null | grep -E '\s[0-9.]+:80\s' | awk '{print $5}' | cut -d : -f 1 | sort | uniq -c | sort -nr
```
Where:
| command                 | description                                   |
|-------------------------|-----------------------------------------------|
| netstat -tn 2>/dev/null	| returns informations all tcp/tcp6 connections |
|grep -E '\s[0-9.]+:80\s'	| filters rows that contains ip addres with 80 port using regular expressions |
|awk '{print $5}'	| prints only column 5th that is described as "Foreign Address" that contains connected client ip address with his remote port|
|cut -d : -f 1	| extracts only ip address for connected client|
|sort	| sorts rows to let them to be counted with next command (uniq command)|
|uniq -c	| counts (-c) neighbouring rows and print them as: number_of_rows row_text|
|sort -nr	| makes numeric sort (-n) and reverse result (-r) |



### Ora attuale
```
date
```


### Ora in UTC
```
date -u
```

### Ora e la timezone (come testo e come variazione oraria)
```
date +"%Z %z"
```

### Timezone configurata come zona geografica
```
cat /etc/timezone
```


---------------------------------------------------------------------------------------------------------------------------


For the following commands thanks to: https://github.com/plcnextusa/PLCnext-Guides/blob/master/Useful%20Linux%20Commands


### Grant root access to an user:
```
usermod -aG sudo username
```

### Give SSH rights to root:
```
  nano /etc/ssh/sshd_config   (remove comment # from the line which says permit root login yes)
```

### Clear log file from Docker Container:
  ```
  echo "" > $(docker inspect --format='{{.LogPath}}' <container_name_or_id>)
```
### Return Firmware version of the PLCnext Controller via CLI
```
grep Arpversion /etc/plcnext/arpversion
```

### Shows the product name from terminal
```
cat /etc/device_data/phoenixsign/production_data | grep 'DEVNAME=' | awk -F '\"' '{print $2}' | sed 's/\"//g'
```
### Shows the mac address from the terminal
  ```
  cat /sys/class/net/eth0/address
  ```
### Shows the IP address from the terminal
  ```
  ifconfig eth0 | awk '/inet addr/ {gsub("addr:", "", $2); print $2}'
```

### Tells the current state of the SD card
```
./usr/sbin/sdcard_state.sh getStatus
```
### Get the device the PLC boots off of (internal or external SD card)
```
./usr/sbin/sdcard_state.sh getBootDevice
```

### Disable the SD card slot
```
./usr/sbin/sdcard_state.sh request_deactivation
```
Then reboot the PLC for the change to go into effect.

### Enable the SD card slot
```
./usr/sbin/sdcard_state.sh request_activation
```
Then reboot the PLC for the change to go into effect.

### Set the date and time to current
```
date -s "$(curl -s --head http://google.com | grep ^Date: | sed 's/Date: //g')"
```

### Get the memory usage of the PLCnext (%)
```
free -m | awk 'NR==2{printf "%.2f\n",$3*100/$2 }’
```
### Get the CPU usage of the PLCnext (%)
```
top -bn1 | grep "Cpu(s)" | sed "s/.*, *\([0-9.]*\)%* id.*/\1/" | awk '{print 100 - $1}'
```
### Restart the PLCnext Runtime
```
(root user) /etc/init.d/plcnext restart
(admin user) sudo /etc/init.d/plcnext restart
```
## Get the PLC's UUID
```
cat /etc/device_data/phoenixsign/cloud_uuid
```
### Shows the product information in the terminal. Serial number, and all data on the hardware.
```
cat /etc/device_data/phoenixsign/production_data
```
### Change the timezone of the PLCnext to local time zone

#### Viewing available timezones:
  ```
  cd /usr/share/zoneinfo
  ls
```
####  Re-Link the correct timezone:
  ```
  sudo unlink /etc/localtime 
  sudo ln -s /usr/share/zoneinfo/[ZONE NAME HERE] /etc/localtime
```

