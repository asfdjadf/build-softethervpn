# build-softethervpn
## ManualInstall
`sudo apt update && sudo apt install build-essential checkinstall -y`
## Download softethervpn from https://www.softether-download.com/cn.aspx
`wget https://github.com/SoftEtherVPN/SoftEtherVPN_Stable/releases/download/v4.34-9745-beta/softether-vpnserver_vpnbridge-v4.34-9745-beta-2020.04.05-windows-x86_x64-intel.exe`

`tar -zxvf vpnserver.tar.gz`

cd vpnserver
make 
## Set the permission
`chmod 600 /opt/vpnserver/* && chmod 700 /opt/vpnserver/vpncmd && chmod 700 /opt/vpnserver/vpnserver`

## Init script copy this to the command line
`echo '#!/bin/sh
DAEMON=/usr/local/vpnserver/vpnserver
LOCK=/var/lock/subsys/vpnserver
test -x $DAEMON || exit 0
case "$1" in
start)
$DAEMON start
touch $LOCK
;;
stop)
$DAEMON stop
rm $LOCK
;;
restart)
$DAEMON stop
sleep 3
$DAEMON start
;;
*)
echo "Usage: $0 {start|stop|restart}"
exit 1
esac
exit 0' > /etc/init.d/vpnserver`


`mv vpnserver-init /etc/init.d/vpnserver`

`chmod 755 /etc/init.d/vpnserver`

`update-rc.d vpnserver defaults`

## start vpnserver
`/etc/init.d/vpnserver start`
