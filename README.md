# Jarkom_Modul5_Lapres
Laporan Resmi Praktikum Modul 5 Jaringan Komputer 2020 Kelompok C07 (0099 &amp; 0157)
# PRE-SOAL
## langkah 1 membuat topologi sesuai di soal dalam CPT
## langkah 2 melakukan subnetting & routing CIDR / VLSM

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/vlsm_table.png)

## langkah 3 menconfig dalam uml
3.A membuat topologi

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/topologiprak5.jpg)

3.B membuat interfaces
#### Surabaya

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/surabaya.jpg)

#### Batu

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/batu.jpg)

#### Kediri

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/topologiprak5.jpg)

#### Malang, Mojokerto, dan Madiun

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/malang-madiun.jpg)

#### Probolinggo, Sidoarjo, dan Gresik

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/probo-gresik.jpg)

### langkah 4 memberikan ip untuk Sidoarjo da Gresik menggunakan DHCP Server

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/dhcpserv_mojo.jpg)

4.A `apt-get update` dan `apt-get install isc-dhcp-server` lalu `nano /etc/default/isc-dhcp-server` dalam mojokerto

4.B menambahkan `INTERFACESv4="eth0"` lalu `service isc-dhcp-server restart`

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/dhcprelay_mojo.jpg)

4.C `nano /etc/dhcp/dhcpd.conf` dalam mojokerto

4.D menambahkan seperti digambar

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/dhcprelay_kediri.jpg)

4.E `apt-get update` dan `apt-get install isc-dhcp-relay` lalu `nano /etc/default/isc-dhcp-relay` dalam kediri

4.F menambahkan dalam SERVERS=`"10.151.77.67"`

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/dhcprelay_batu.jpg)

4.G `nano /etc/default/isc-dhcp-relay` dalam batu

4.H menambahkan dalam SERVERS=`"10.151.77.67"`

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/interfaces_sido.jpg)

4.I `nano /etc/network/interfaces` dalam sidoarjo

4.J menambahkan seprti digambar

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/interfaces_gresik.jpg)

4.K `nano /etc/network/interfaces` dalam gresik

4.L menambahkan seprti digambar


# BAHAS SOAL
### NO.1

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/one.jpg)

langkah :
+ `nano one.sh` pada Surabaya
+ `iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to 10.151.76.34`
+ `bash one.sh`
+ lakukan ping pada masing-masing client

### NO.2

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/two.jpg)

langkah :
+ `nano two.sh` pada Surabaya
+ `iptables -A FORWARD -p tcp --dport 22 -d 10.151.77.64/29 -i eth0 -j DROP`
+ `bash two.sh`
+ lakukan testing dengan ` nc 10.151.77.66 22`

### NO.3

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/three.jpg)

langkah :
+ `nano three.sh` pada malang dan mojokerto
+ tulis `iptables -A INPUT -p icmp -m connlimit --connlimit-above 3 --connlimit-mask 0 -j DROP`
+ `bash three.sh`
+ lakukan testing ping 

### NO.4

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/four.jpg)

langkah :
+ `nano four.sh` pada malang
+ tulis sesuasi keinginan soal 7:00 - 17:00 hari senin sampe jumat selain itu di reject

`iptables -A INPUT -s 192.168.0.2/24 -m time --timestart 07:00 --timestop 17:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT

iptables -A INPUT -s 192.168.0.2/24 -m time --timestart 17:01 --timestop 06:59 -j REJECT

iptables -A INPUT -s 192.168.0.2/24 -m time --timestart 07:00 --timestop 17:00 --weekdays Sat,Sun -j REJECT`

+ `bash four.sh`
+ `date`
+ `date -s '2020-12-21 08:00:00'`

### NO.5

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/five.jpg)

langkah :
+ `nano five.sh` pada malang
+ tulis sesuasi keinginan soal 17:00 - 07:00 hari senin sampe jumat selain itu di reject

`iptables -A INPUT -s 192.168.1.0/24 -m time --timestart 07:01 --timestop 16:59 -j REJECT`

+ `bash five.sh`
+ `date`

### NO.6

langkah :
+ `nano six.sh` pada surabaya
+ `iptables -A INPUT -s 192.168.1.0/24 -m time --timestart 07:01 --timestop 16:59 -j REJECT`
+ `bash six.sh`

### NO.7

langkah :
+ `nano seven.sh` pada surabaya, malang, dan mojokerto
+ lalu input `iptables -N LOGGING 

iptables -A FORWARD -j LOGGING 

iptables -A LOGGING -m limit --limit 2/min -j LOG --log-prefix "IPTables-Dropped: " --log-level 4 

iptables -A LOGGING -j DROP`

+ `bash seven.sh`
