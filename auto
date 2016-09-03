#!/bin/sh
#################################################
# Family Brother Squad #
#################################################
clear

echo ""
echo "Firewall with IP Tables"
echo "Starting here bro.. "
echo "......................"
echo "......................"
echo ""
echo ""
echo "ICEWALL"
echo "Starting KAY ICEWALL "
echo "......................"
echo "......................"
echo ""
#untuk scheck system IP #
echo ""
echo "IP Address dan Interface system anda : "
echo ""
/sbin/ifconfig
echo ""

# untuk mengaktifkan system forwarding #
echo "1" > /proc/sys/net/ipv4/ip_forward

# kita mulai untuk scriptnya, perhatikan penjelasannya #

/sbin/iptables -L # ini perintah untuk melihat status policy #
/sbin/iptables -F # ini perintah untuk membersihkan semua policy #
/sbin/iptables -A INPUT -j ACCEPT # menerima smua paket masuk #
/sbin/iptables -A INPUT -p tcp -j REJECT --reject-with tcp-reset # reset smua paket tcp masuk #
/sbin/iptables -A OUTPUT -j ACCEPT # menerima smua paket kluar #
/sbin/iptables -A INPUT -p tcp --dport 25 -j REJECT # matiin smtp port service #
/sbin/iptables -A INPUT -p tcp --dport 23 -j REJECT # matiin telnet port service #
/sbin/iptables -A INPUT -p tcp --dport 21 -j REJECT # matiin ftp port service #
/sbin/iptables -A INPUT -p tcp --dport 22 -j ACCEPT # terima ssh port service #
/sbin/iptables -A INPUT -p icmp --icmp-type echo-request -j REJECT # menolak echo request luar #
/sbin/iptables -A OUTPUT -p tcp -d 127.0.0.1 -s 0.0.0.0/0 -j REJECT # menolak ping ke lo dari luar #
/sbin/iptables -A OUTPUT -p tcp --dport 80 -j ACCEPT # Hidupin web port service keluar #
/sbin/iptables -A OUTPUT -p tcp --dport 22 -j ACCEPT # Hidupin ssh port service keluar #


# Untuk ip masquerade #
# gunakan eth0 untuk interface dgn ip public (dari ISP anda) #
# eth1 gunakan sebagai gateway client dengan ip 192.168.x.x #
# untuk mengaktifkan fungsi ini, hilangkan tanda kress nya #
#/sbin/iptables -A POSTROUTING -t nat -s 192.168.0.0/24 -j MASQUERADE -o eth0

# Simpan konfigurasi #
clear
echo ""
echo "Simpan security setting ... "
echo ""
/sbin/iptables-save > /etc/iptables/rules.v4 #menyimpan perintah ip tables#
/sbin/iptables-save > dump  #menyimpan config#
echo ""
echo "Restart firewall ini ... "
echo ""
/etc/init.d/iptables-persistent restart
echo ""
echo "firewall ... OK Beb"
echo ""
echo "Creatd By Mas Dahni "
echo ""
