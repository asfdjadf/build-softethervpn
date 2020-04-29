# build-softethervpn
## ManualInstall
sudo apt update && sudo apt install build-essential checkinstall -y
## Download softethervpn from https://www.softether-download.com/cn.aspx
wget https://github.com/SoftEtherVPN/SoftEtherVPN_Stable/releases/download/v4.34-9745-beta/softether-vpnserver_vpnbridge-v4.34-9745-beta-2020.04.05-windows-x86_x64-intel.exe

tar -zxvf vpnserver.tar.gz

cd vpnserver
make 
## Set the permission
chmod 600 /opt/vpnserver/* && chmod 700 /opt/vpnserver/vpncmd && chmod 700 /opt/vpnserver/vpnserver
