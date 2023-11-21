# TP4 : DHCP

## I. DHCP Client

**🌞 Déterminer**

    ipconfig /all

        Serveur DHCP . . . . . . . . . . . . . : 10.33.79.254

        Bail obtenu. . . . . . . . . . . . . . : vendredi 27 octobre 2023 13:32:56
        Bail expirant. . . . . . . . . . . . . : samedi 28 octobre 2023        10:14:31



 ## II. Serveur DHCP
**🌞 Preuve de mise en place**

    ping youtube.com
    PING youtube.com (142.250.179.110) 56(84) bytes of data.
    64 bytes from reflectededge.reflected.net (142.250.179.110): icmp_seq=1 ttl=53 time=15.4 ms
    64 bytes from reflectededge.reflected.net (142.250.179.110): icmp_seq=2 ttl=53 time=14.7 ms
    64 bytes from reflectededge.reflected.net (142.250.179.110): icmp_seq=3 ttl=53 time=25.1 ms
    ^C
    --- youtube.com ping statistics ---
    3 packets transmitted, 3 received, 0% packet loss, time 2004ms
    rtt min/avg/max/mdev = 14.719/18.407/25.135/4.764 ms

**🌞 Serveur DHCP**

    dnf -y install dhcp-server

**🌞 Rendu**

    sudo nano /etc/dhcp/dhcpd.conf

    sudo cat /etc/dhcp/dhcpd.conf

    option domain-name     "tp4.dhcp";
        authoritative;
        subnet 10.4.1.0 netmask 255.255.255.0 {
    range dynamic-bootp 10.4.1.137 10.4.1.237;
    option broadcast-address 10.4.1.255;
    }

##

    sudo systemctl enable --now dhcpd
    Created symlink /etc/systemd/system/multi-user.target.wants/dhcpd.service → /usr/lib/systemd/system/dhcpd.service.

    sudo firewall-cmd --add-service=dhcp
    success

    sudo firewall-cmd --runtime-to-permanent
    success
##



    sudo systemctl status dhcpd
    dhcpd.service - DHCPv4 Server Daemon
         Loaded: loaded (/usr/lib/systemd/system/dhcpd.service; enabled; preset>
         Active: active (running) since Fri 2023-10-28 15:29:01 CEST; 4min 48s >

**🌞 Test !**

    sudo cat /etc/sysconfig/network-scripts/ifcfg-enp0s3
    DEVICE=enp0s3

    BOOTPROTO=dhcp
    ONBOOT=yes

**🌞 Prouvez que**

        ip a

     1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
        link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
        inet 127.0.0.1/8 scope host lo
        valid_lft forever preferred_lft forever
        inet6 ::1/128 scope host
        valid_lft forever preferred_lft forever
    2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state  UP group default qlen 1000
        link/ether 08:00:27:de:36:da brd ff:ff:ff:ff:ff:ff
        inet 10.4.1.137/24 brd 10.4.1.255 scope global dynamic noprefixroute enp0s3
        valid_lft 336sec preferred_lft 336sec
        inet6 fe80::a00:27ff:fede:36da/64 scope link noprefixroute
        valid_lft forever preferred_lft forever
##
    nmcli con show enp0s3

**🌞 Bail DHCP serveur**



**🌞 Nouvelle conf !**
    sudo nano /etc/dhcp/dhcpd.conf
##
    sudo cat /etc/dhcp/dhcpd.conf
    option domain-name     "tp4.dhcp";
    option domain-name-servers     1.1.1.1;
    default-lease-time 21600;
    max-lease-time 21600;
    authoritative;
    subnet 10.4.1.0 netmask 255.255.255.0 {
    range dynamic-bootp 10.4.1.137 10.4.1.237;
    option broadcast-address 10.4.1.255;
    option routers 10.4.1.254;
    }
##
    sudo systemctl restart dhcpd


**🌞 Test !**

