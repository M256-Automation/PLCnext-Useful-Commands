# __PLCnext Useful Commands__
A list of useful commands on PLCnext terminal

## FW update (dopo aver copiato il file *.raucb in /opt/plcnext)
sudo update-axcf2152

## check firmware version:
cat /etc/plcnext/arpversion

## Reboot
sudo reboot

## Reset without deleting FW update
sudo recover-axcf2152 1      

## Reset deleting FW update - factory default - tutto quello che hai messo nel PLC viene cancellato
sudo recover-axcf2152 2      

## PLC start/stop/restart
sudo /etc/init.d/plcnext start

sudo /etc/init.d/plcnext stop

sudo /etc/init.d/plcnext restart

## Check log file in diretta:
tail -f -n 20 /opt/plcnext/logs/Output.log

dove "-n 20" significa che vengono mostrate subito le ultime 20 righe del file 

## Transfer C++ libraries .so, move file in /usr/local/lib and then
cd /usr/local/lib
ln -sf _nomelibreria_.so
sudo ldconfig

## Assegnazione IP
ifconfig eth0 192.168.1.x netmask 255.255.255.0

## Assegnazione gateway
route add default gateway 192.168.1.1

## Assegnazione DNS
sudo echo "nameserver 8.8.8.8" > /etc/resolv.conf

## Quale DNS è configurato?
$ cat /etc/resolv.conf 

## Cercare file
find . -name tecmint.txt

cerca il file nella cartella corrente e tutte le sue sottocartelle

lanciato come _root_ ha libero accesso a tutte le cartelle 

## guix
guix package  --search=zabbix

guix install zabbix-agentd

## memory
top

