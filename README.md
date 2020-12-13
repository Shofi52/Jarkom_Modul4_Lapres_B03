# Jarkom_Modul4_Lapres_B03

## CIDR 
![CIDR](modul4/CIDR.PNG)
![CIDR_Tree](modul4/CIDR_Tree.PNG)

### 1. Membuat topologi jaringan 
``` #switch
uml_switch -unix switch1 > /dev/null < /dev/null &
uml_switch -unix switch13 > /dev/null < /dev/null &
uml_switch -unix switch15 > /dev/null < /dev/null &
uml_switch -unix switch16 > /dev/null < /dev/null &
uml_switch -unix switch19 > /dev/null < /dev/null &
uml_switch -unix switch22 > /dev/null < /dev/null &
uml_switch -unix switch25 > /dev/null < /dev/null &
uml_switch -unix switch21 > /dev/null < /dev/null &
uml_switch -unix switch18 > /dev/null < /dev/null &
uml_switch -unix switch20 > /dev/null < /dev/null &
uml_switch -unix switch17 > /dev/null < /dev/null &
uml_switch -unix switch2 > /dev/null < /dev/null &
uml_switch -unix switch3 > /dev/null < /dev/null &
uml_switch -unix switch4 > /dev/null < /dev/null &
uml_switch -unix switch5 > /dev/null < /dev/null &

#Router
xterm -T SURABAYA -e linux ubd0=SURABAYA,jarkom umid=SURABAYA eth0=tuntap,,,10.151.74.17 eth1=daemon,,,switch1 eth2=daemon,,,switch13 eth3=daemon,,,switch2 eth4=daemon,,,switch4 mem=64M &
xterm -T PASURUAN -e linux ubd0=PASURUAN,jarkom umid=PASURUAN eth0=daemon,,,switch2 eth1=daemon,,,switch3 eth2=daemon,,,switch19 mem=64M &
xterm -T PROBOLINGGO -e linux ubd0=PROBOLINGGO,jarkom umid=PROBOLINGGO eth0=daemon,,,switch3 eth1=daemon,,,switch15 eth2=daemon,,,switch16 mem=64M &
xterm -T MADIUN -e linux ubd0=MADIUN,jarkom umid=MADIUN eth0=daemon,,,switch22 eth1=daemon,,,switch25 mem=64M &
xterm -T BATU -e linux ubd0=BATU,jarkom umid=BATU eth0=daemon,,,switch4 eth1=daemon,,,switch22 eth2=daemon,,,switch21 eth4=daemon,,,switch5 A10 mem=64M &
xterm -T KEDIRI -e linux ubd0=KEDIRI,jarkom umid=KEDIRI eth0=daemon,,,switch5 eth1=daemon,,,switch18 eth2=daemon,,,switch17 mem=64M &
xterm -T BLITAR -e linux ubd0=BLITAR,jarkom umid=BLITAR eth0=daemon,,,switch17 eth1=daemon,,,switch20 mem=64M &

#Server
xterm -T MALANG -e linux ubd0=MALANG,jarkom umid=MALANG eth0=daemon,,,switch18 mem=64M &
xterm -T MOJOKERTO -e linux ubd0=MOJOKERTO,jarkom umid=MOJOKERTO eth0=daemon,,,switch13 mem=64M &

#Klien
xterm -T SAMPANG -e linux ubd0=SAMPANG,jarkom umid=SAMPANG eth0=daemon,,,switch1 mem=64M &
xterm -T BONDOWOSO -e linux ubd0=BONDOWOSO,jarkom umid=BONDOWOSO eth0=daemon,,,switch15 mem=64M &
xterm -T JOMBANG -e linux ubd0=JOMBANG,jarkom umid=JOMBANG eth0=daemon,,,switch22 mem=64M &
xterm -T JEMBER -e linux ubd0=JEMBER,jarkom umid=JEMBER eth0=daemon,,,switch16 mem=64M &
xterm -T BOJONEGORO -e linux ubd0=BOJONEGORO,jarkom umid=BOJONEGORO eth0=daemon,,,switch25 mem=64M &
xterm -T NGANJUK -e linux ubd0=NGANJUK,jarkom umid=NGANJUK eth0=daemon,,,switch21 mem=64M &
xterm -T BANYUWANGI -e linux ubd0=BANYUWANGI,jarkom umid=BANYUWANGI eth0=daemon,,,switch16 mem=64M &
xterm -T TULUNGAGUNG -e linux ubd0=TULUNGAGUNG,jarkom umid=TULUNGAGUNG eth0=daemon,,,switch20 mem=64M &
xterm -T SIDOARJO -e linux ubd0=SIDOARJO,jarkom umid=SIDOARJO eth0=daemon,,,switch19 mem=64M &
xterm -T LUMAJANG -e linux ubd0=LUMAJANG,jarkom umid=LUMAJANG eth0=daemon,,,switch17 mem=64M & 
```


### 2. Mengatur interface pada setiap UML
- Buka `/etc/network/interfaces'
- Edit file seperti yang ada pada file .txt setiap UML di folder modul4

### 3. Lakukan Routing
- Membuat file `route.sh`
- Surabaya 
```
route add -net 192.168.64.0 netmask 255.255.192.0 gw 192.168.128.2
route add -net 192.168.0.0 netmask 255.255.224.0 gw 192.168.32.2
route add -net 10.151.83.38 netmask 255.255.255.252 gw 192.168.32.2
```
- Pasuruan
```
route add -net 192.168.64.0 netmask 255.255.240.0 gw 192.168.80.2
```
-   Probolinggo
``` 
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.80.1
```
- Batu
```
route add -net 192.168.16.0 netmask 255.255.248.0 gw 192.168.128.2
route add -net 192.168.0.0 netmask 255.255.240.0 gw 192.168.8.2
route add -net 10.151.83.38 netmask 255.255.255.252 gw 192.168.8.2
```
- Kediri
```
route add -net 192.168.0.0 netmask 255.255.248.0 gw 192.168.4.2
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.16.1
```
- Madiun
```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.16.1
```
- blitar
```
route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.4.1
```
