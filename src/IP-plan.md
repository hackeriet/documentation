# IP plan

## Log

```
6 jan 2019: ONLINE AGAIN - IP plan moved to <https://ip.hackeriet.no/>

PM kfh@freenode if you need the login password (temporary solution until
management pw is in hackerpass).

5 oct 2018: fikset problemer med nettet innover i gangen: (1.) det var
en annen DHCP server (192.168.0.0/24) på en av kablingspunktene. denne
kabelen ble identifisert og merket med en firkant grå sølvtape. (2.)
satt opp ett aksesspunt med en unify g/n jeg fant på labben.
aksesspunktet (hausmania) ble satt på samme fysiske sted som et defunct
privat aksesspunkt (AirlinkNNNNN), på 1 etasje, innerst til høyre. (3.)
ekstra 5 porter svitsj ble tapet til veggen TODO: optimalisére vekk.

sept 2018: (currently offline) IP plan moved to
<https://ip.hackeriet.no/> PM kfh@freenode if you need the login
password. (but ip.hackeriet.no crashed during power utage sept 2018, so
this is currently offline)

29 sept 2018: switch innover i gangen byttet ut med dum 16 port switch
kablet rett til vlan10 så folk kommer på nett. (ikke alle kabler er
koblet til). den gamle switchen laget rare viftelyder og blinket rødt,
denne er skrudd av men er fortsatt på stedet.
```

## IP list

This is the authoritative list of how/what is using the IPv4-adresses we
routed to us.

### vlan2 | 10.10.2.1/24 | no ipv6 | hausmania,adm | BROKEN, no router! |

Previously called "kontor", repurposed for anything official/non-tenant
business of Hausmania.

### vlan3 | 10.10.3.1/24 | 2a02:ed06:3::1/64 | wired,hackeriet | moon |

```
  10.10.3.10   no ipv6                   johan.hackeriet.no                   canon printer
  10.10.3.11   no ipv6                   ottman.hackeriet.no                  xerox phaser printer
  10.10.3.15   no ipv6                   hackeriet-door                       "Source code repo":https://github.com/hackeriet/door
  10.10.3.16   dhcp6                     hackeriet-button.haus.hackeriet.no   space status button pi (eth fallback)
  10.10.3.17   dhcp6                     hackeriet-button.haus.hackeriet.no   space status button pi (wlan)
  10.10.3.20   no ipv6                   dc-ap1                               access point, possibly physically on vlan130. hackeriet / hackeriet mgmt pw.
  10.10.3.21   2001:16d8:eee2:3::21      razor.hackeriet.no                   (SDR station)
  10.10.3.22   2a02:ed06:3::10:10:3:22   -                                    vend-lcd (LCD screen on vending machine)
  on dhcpv4    autoconf ipv6 (in DNS)    vending.hackeriet.no                 
```

### vlan10 | 10.10.10.1/24 | 2a02:ed06:10::1/64 | hausmania,tenants | moon |

The wired network used by Hausmania tenants. Sometimes available over
Wifi as well.

### vlan20 | 10.0.20.1/24 | 2a02:ed06:20::1/64 | hausmania,infra | pit-sw |

VLAN for units tied to the building itself. (doors, access points,
related infrastructure)

```
  on dhcp   no   ap,hackeriet   unifi managed
  on dhcp   no   ap,serverrom   unifi managed
```

DHCPv4 running on pit-sw handing out 10.0.20.50-254. (configured, but
untested per 2017-10-14)

### vlan23 | 10.0.23.1/24 | 2a02:ed06:23::1/64 | mgmt | pit-sw |

This network is used for management of infrastructure like switches,
routers and similar. No bmc/ipmi hosts, those live on vlan 230 below.

```
  10.0.23.3    no   hackeriet-sw                                                            (Catalyst 2960G) nettlaug@ / hauspw
  10.0.23.5    no   haus-core-sw                                                            (Catalyst 2960G) nettlaug@, hauspw. in the basement.
  10.0.23.6    no   haus-4etg-sw                                                            (Procurve 2626 J4900B) manager / hauspw. forth floor by door to room 1405.
  10.0.23.8    ?    haus-3etg-sw                                                            third floor by door to room 1309. (not in place yet)
  10.0.23.9    no   haus-musikk-sw                                                          (J8164A) hallway outside https://hackeriet.no/hausrom/2102.html , between musikk and hvite brakker.
  10.0.23.10   no   haus-2etg-sw                                                            (Procurve 2626 / J4900B) Outside https://hackeriet.no/hausrom/1209.html 2nd floor, outside Mons' room/capoeira room
  10.0.23.11   no   hack-tor1-sw                                                            admin / adminpw. at top of rack one, brocade fcx648
  10.0.23.12   ?    unconfigured. apc power distribution unit. admin / hackeriet mgmt pw.
  10.0.23.13   ?    hackeriet-ap1. (tidl. humla1130ap\\-1)                                  admin / hackeriet mgmt pw.
  10.0.23.14   no   pit-sw                                                                  Cisco 3560E nettlaug / hackeriet mgmt pw.
  10.0.23.15   no   brocade-sw                                                              testsvitsj
  10.0.23.16   no   hole-sw (lo0)                                                           Cisco 3560
```

### vlan25 | 10.0.25.0/24 | 2a02:ed06:25::1/64 | wlan,public,haus | pit-sw |

Not in use. No IPv4 NAT anywhere.

### vlan130 | 185.35.202.192/26 | 2a02:ed06::/64 | srv,hackeriet | pit-sw |

```
  185.35.202.194                    2a02:ed06::194                                                                 adrianf (guleadrian)
  185.35.202.195                    2a02:ed06::1000                                                                mynt.hackeriet.no (zulu, lasse)
  185.35.202.196                    2a02:ed06::196                                                                 plague.hackeriet.no (lafa)
  185.35.202.197                    2a02:ed06::197                                                                 nux.hackerietno ([nixops](https://github.com/hackeriet/nixops), sgo)
  182.35.202.198                    2a02:ed06::198                                                                 ip.hackeriet.no (kfh)
  185.35.202.199                    ...                                                                            mulder vm (atluxity)
  185.35.202.200                    2a02:ed06::200                                                                 tepewqukumatz.hackeriet.no (huayra)
  185.35.202.201                    2a02:ed06::201                                                                 bane.hackeriet.no (atluxity)
  185.35.202.202                    2a02:ed06::202                                                                 blade.hackeriet.no
  185.35.202.203                    2a02:ed06::203                                                                 host003.hackeriet.no (capitol)
  185.35.202.204                    2a02:ed06::204                                                                 tone2.hackeriet.no (capitol)
  185.35.202.205                    2a02:ed06::205                                                                 cereal.hackeriet.no (comotion)
  185.35.202.206                    2a02:ed06::206                                                                 hyperboria.hackeriet.no (sgo)
  185.35.202.207                    2a02:ed06::207                                                                 ns1.hackeriet.no (sjn)
  185.35.202.208                    2a02:ed06::208                                                                 foo.hackeriet.no (sjn)
  185.35.202.209                    2a02:ed06::209                                                                 henrik.hackeriet.no (capitol)
  185.35.202.210                    2a02:ed06::210                                                                 mas (lasse)
  185.35.202.211                    2a02:ed06::211                                                                 sshow.hackeriet.no (sshow)
  185.35.202.212                    2a02:ed06::212                                                                 nat64.hackeriet.no (capitol)
  185.35.202.213                    2a02:ed06::face:b00k                                                           ldap002.hackeriet.no (capitol)
  185.35.202.214                    2a02:ed06::214 2a02:ed06::f00b:39ff:fec5:9585 2a02:ed06::f00b:39ff:fec5:9586   login.hackeriet.no (bezaban)
  185.35.202.215                    2a02:ed06::215 og 2a02:ed06:beef:beef::1                                       vpn.hackeriet.no (head)
  185.35.202.216                    2a02:ed06::216                                                                 konrad.hackeriet.no (kbeckmann)
  185.35.202.217                    2a02:ed06::217                                                                 pris.hackeriet.no (fnords)
  182.35.202.218                    2a02:ed06::218                                                                 sgo
  185.35.202.219                    2a02:ed06::119 2a02:ed06::4b6f:f144:35db:7605                                  saturn.hackeriet.no (bezaban)
  185.35.202.220                    2a02:ed06::202                                                                 gitlab.hackeriet.no (var: host001.hackeriet.no (capitol), 2a02:ed06::2312)
  185.35.202.221                    2a02:ed06::221                                                                 tor-node001.hackeriet.no
  185.35.202.222                    2a02:ed06::222                                                                 tor-node002.hackeriet.no
  185.35.202.223                    2a02:ed06::223                                                                 host002.hackeriet.no (capitol)
  185.35.202.224                    2a02:ed06::224                                                                 matrix.hackeriet.no (krav)
  185.35.202.225                    2a02:ed06::225                                                                 forum.hausmania.org
  185.35.202.226                    2a02:ed06::b1ac:b10c                                                           (rediger.)hausmania.org
  185.35.202.227                    2a02:ed06::227                                                                 nix.hackeriet.no (krav)
  185.35.202.228                                                                                                   wificontroller.hackeriet.no (hackeriet/lasse)
  185.35.202.229                                                                                                   loki.heplaphon.com (heplaphon)
  185.35.202.230 - 185.35.202.233                                                                                  DHCP-scope for installation
  185.35.202.234                    ?                                                                              hostname: blokk (owned by head)
  185.35.202.235                    ?                                                                              in use by head
  185.35.202.237                    2a02:ed06::237                                                                 fw.tla.wtf (kfh)
  185.35.202.238                    no ipv6                                                                        hausmania ext
  185.35.202.239                    no ipv6                                                                        customer V behind gi0/41 on pit-sw
  185.35.202.240/28 (.240-.254)                                                                                    VPN/NAT-scope (RESERVED)
                                    2a02:ed06::2039                                                                backup.hackeriet.no (capitol)
                                    2a02:ed06:8::1                                                                 k8s01.hackeriet.no (capitol)
```
### vlan150 | 10.0.150.0/24 | 2a02:ed06:150:/64 | int,kubernetes | pit-sw |

Unrouted internal network for Kubernetes. DHCP server on pit-sw.

### vlan200 | NAT64 IPv6 only | 2a02:ed06:212::/96 | nat64,hackeriet | routed at babel.hackeriet.no |

babel.hackeriet.no runs a NAT64 and DNS64 service. Clients on this vlan
needing IPv4 get NAT64 access, and IPv6 access is routed normally by
babel.

### vlan230 | 10.0.230.0/24 | 2a02:ed06:230:/64 | mgmt,hackeriet | pit-sw |

```
  10.0.120.10   -   hp pdu (needs to be renumbered)
```

vlan230 is the IPMI/BMC network.

## Configuration examples

For /etc/network/interfaces:

```
iface eth0 inet static
address 185.35.202.XXX
netmask 255.255.255.192
gateway 185.35.202.193
dns-nameserver 91.205.184.10 91.205.187.202 2001:4860:4860:0:0:0:0:8888

iface eth0 inet6 static
address 2a02:ed06::XXX
netmask 64
gateway 2a02:ed06::1
```

For /etc/sysctl.d/10-ipv6-privacy.conf

```

1.  Turn off IPv6 privacy extension in order to keep IP addresses for
    outgoing
2.  traffic static (see
    https://github.com/hackeriet/hackeriet.no/wiki/IP-plan)
    net.ipv6.conf.all.use\_tempaddr = 0
    net.ipv6.conf.default.use\_tempaddr = 0
```

Fiber connection dump:

```
Nett: 185.35.202.192/26
Linknett: 185.35.202.72/30 .73 Blix .74 Hackeriet
Linknett: 2a02:20c8:3460::/126 ::1 Blix ::2 Hackeriet
Nett: 2a02:ed06::/32
nameserver 91.205.184.10
nameserver 91.205.187.202
```

Enable LLDPd.
```
apt install lldpd
service start lldpd
```

## Linknett

2a02:ed06:1000::/48 - link networks, use ::1/126 and ::2/126.

```
  -          10.0.127.12/30   2A02:ED06:1000:1::1/64   link,hole-sw,star     -
  vlan2101   10.0.127.16/30   2a02:ed06:1000:2::1/64   link,hole-sw,pit-sw   -
```

