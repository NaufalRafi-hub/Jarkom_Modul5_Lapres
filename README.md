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

4.A `nano /etc/default/isc-dhcp-server` dalam mojokerto
4.B menambahkan `INTERFACESv4="eth0"`

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/dhcprelay_mojo.jpg)

4.C `nano /etc/dhcp/dhcpd.conf` dalam mojokerto
4.D menambahkan seperti digambar

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/dhcprelay_kediri.jpg)

4.E `nano /etc/default/isc-dhcp-relay` dalam kediri
4.F menambahkan dalam SERVERS=`"10.151.77.67"`

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/dhcprelay_batu.jpg)

4.G `nano /etc/default/isc-dhcp-relay` dalam batu
4.H menambahkan dalam SERVERS=`"10.151.77.67"`

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/interfaces_sido.jpg)

4.I `nano /etc/network/interfaces` dalam sidoarjo
4.J menambahkan seeprti digambar

![alt text](https://github.com/NaufalRafi-hub/Jarkom_Modul5_Lapres/blob/main/imageprak5/interfaces_gresik.jpg)

4.K `nano /etc/network/interfaces` dalam gresik
4.L menambahkan seeprti digambar


# BAHAS SOAL
