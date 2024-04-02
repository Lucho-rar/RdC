# Redes de Computadoras - 2024
## _Trabajo Práctico 1_

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

### Configuración de diagrama 

| PC | Interfaz de Red | IPv4 | IPv6 |
|----------|----------|----------|---------|
| h1   | eth 0   | 192.168.1.10/24 |  2001:aaaa:bbbb:1::10/64  |
| h2   | eth 0   | 192.168.2.10/24  |2001:aaaa:cccc:1::10/64  |
| h3    | eth 0   | 192.168.2.11/24  |2001:aaaa:cccc:1::11/64  |
| Router 1    | eth 0   | 192.168.1.11/24   |2001:aaaa:bbbb:1::11/64  |
|    | eth 1   | 192.168.2.12/24  |2001:aaaa:cccc:1::12/64  |

##### Config Router

```
Router1(config)#interface GigabitEthernet0/0/0
Router1(config-if)#ip address 192.168.2.12 255.255.255.0
Router1(config-if)#no shutdown 

Router1(config)#interface GigabitEthernet 0/0/1
Router1(config-if)#ip address 192.168.1.11 255.255.255.0
Router1(config-if)#no shutdown 
```
### Evaluar conectividad entre todos los hosts enviando 3 paquetes ICMPv4, usando ping para IPv4

##### From H1

````
C:\>ping -n 3 192.168.2.10

Pinging 192.168.2.10 with 32 bytes of data:

Reply from 192.168.2.10: bytes=32 time<1ms TTL=127
Reply from 192.168.2.10: bytes=32 time<1ms TTL=127
Reply from 192.168.2.10: bytes=32 time<1ms TTL=127

Ping statistics for 192.168.2.10:
    Packets: Sent = 3, Received = 3, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

C:\>ping -n 3 192.168.2.11

Pinging 192.168.2.11 with 32 bytes of data:

Reply from 192.168.2.11: bytes=32 time<1ms TTL=127
Reply from 192.168.2.11: bytes=32 time<1ms TTL=127
Reply from 192.168.2.11: bytes=32 time<1ms TTL=127

Ping statistics for 192.168.2.11:
    Packets: Sent = 3, Received = 3, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
````






##### From H2

```
C:\>ping -n 3 192.168.2.11

Pinging 192.168.2.11 with 32 bytes of data:

Reply from 192.168.2.11: bytes=32 time<1ms TTL=128
Reply from 192.168.2.11: bytes=32 time<1ms TTL=128
Reply from 192.168.2.11: bytes=32 time<1ms TTL=128

Ping statistics for 192.168.2.11:
    Packets: Sent = 3, Received = 3, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

C:\>ping -n 3 192.168.1.12

Pinging 192.168.1.12 with 32 bytes of data:

Reply from 192.168.1.12: bytes=32 time<1ms TTL=127
Reply from 192.168.1.12: bytes=32 time<1ms TTL=127
Reply from 192.168.1.12: bytes=32 time<1ms TTL=127

Ping statistics for 192.168.1.12:
    Packets: Sent = 3, Received = 3, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
```

##### From H3

```
C:\>ping -n 3 192.168.1.12

Pinging 192.168.1.12 with 32 bytes of data:

Reply from 192.168.1.12: bytes=32 time<1ms TTL=127
Reply from 192.168.1.12: bytes=32 time<1ms TTL=127
Reply from 192.168.1.12: bytes=32 time<1ms TTL=127

Ping statistics for 192.168.1.12:
    Packets: Sent = 3, Received = 3, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

C:\>ping -n 3 192.168.2.10

Pinging 192.168.2.10 with 32 bytes of data:

Reply from 192.168.2.10: bytes=32 time<1ms TTL=128
Reply from 192.168.2.10: bytes=32 time<1ms TTL=128
Reply from 192.168.2.10: bytes=32 time<1ms TTL=128

Ping statistics for 192.168.2.10:
    Packets: Sent = 3, Received = 3, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
```



### Evaluar conectividad entre todos los hosts enviando 3 paquetes ICMPv4, usando ping para IPv4

##### From H1
```
C:\>ping -n 3 2001:aaaa:cccc:1::10

Pinging 2001:aaaa:cccc:1::10 with 32 bytes of data:

Reply from 2001:AAAA:CCCC:1::10: bytes=32 time<1ms TTL=127
Reply from 2001:AAAA:CCCC:1::10: bytes=32 time<1ms TTL=127
Reply from 2001:AAAA:CCCC:1::10: bytes=32 time<1ms TTL=127

Ping statistics for 2001:AAAA:CCCC:1::10:
    Packets: Sent = 3, Received = 3, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

C:\>ping -n 3 2001:aaaa:cccc:1::11

Pinging 2001:aaaa:cccc:1::11 with 32 bytes of data:

Reply from 2001:AAAA:CCCC:1::11: bytes=32 time<1ms TTL=127
Reply from 2001:AAAA:CCCC:1::11: bytes=32 time<1ms TTL=127
Reply from 2001:AAAA:CCCC:1::11: bytes=32 time=17ms TTL=127

Ping statistics for 2001:AAAA:CCCC:1::11:
    Packets: Sent = 3, Received = 3, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 17ms, Average = 5ms
```

##### From H2
```
C:\>ping -n 3 2001:aaaa:bbbb:1::10

Pinging 2001:aaaa:bbbb:1::10 with 32 bytes of data:

Reply from 2001:AAAA:BBBB:1::10: bytes=32 time<1ms TTL=127
Reply from 2001:AAAA:BBBB:1::10: bytes=32 time<1ms TTL=127
Reply from 2001:AAAA:BBBB:1::10: bytes=32 time<1ms TTL=127

Ping statistics for 2001:AAAA:BBBB:1::10:
    Packets: Sent = 3, Received = 3, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

C:\>ping -n 3 2001:aaaa:cccc:1::11

Pinging 2001:aaaa:cccc:1::11 with 32 bytes of data:

Reply from 2001:AAAA:CCCC:1::11: bytes=32 time=14ms TTL=128
Reply from 2001:AAAA:CCCC:1::11: bytes=32 time<1ms TTL=128
Reply from 2001:AAAA:CCCC:1::11: bytes=32 time<1ms TTL=128

Ping statistics for 2001:AAAA:CCCC:1::11:
    Packets: Sent = 3, Received = 3, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 14ms, Average = 4ms

```





##### From H3
```
C:\>ping -n 3 2001:aaaa:bbbb:1::10

Pinging 2001:aaaa:bbbb:1::10 with 32 bytes of data:

Reply from 2001:AAAA:BBBB:1::10: bytes=32 time<1ms TTL=127
Reply from 2001:AAAA:BBBB:1::10: bytes=32 time<1ms TTL=127
Reply from 2001:AAAA:BBBB:1::10: bytes=32 time<1ms TTL=127

Ping statistics for 2001:AAAA:BBBB:1::10:
    Packets: Sent = 3, Received = 3, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

C:\>ping -n 3 2001:aaaa:cccc:1::10

Pinging 2001:aaaa:cccc:1::10 with 32 bytes of data:

Reply from 2001:AAAA:CCCC:1::10: bytes=32 time<1ms TTL=128
Reply from 2001:AAAA:CCCC:1::10: bytes=32 time<1ms TTL=128
Reply from 2001:AAAA:CCCC:1::10: bytes=32 time=1ms TTL=128

Ping statistics for 2001:AAAA:CCCC:1::10:
    Packets: Sent = 3, Received = 3, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 1ms, Average = 0ms
```

### ARP H1
```
C:\>arp -a
  Internet Address      Physical Address      Type
  192.168.1.11          0060.3e75.1c02        dynamic
```
### ARP H3
```
C:\>ARP -A
  Internet Address      Physical Address      Type
  192.168.2.10          0030.a34d.b6dc        dynamic
  192.168.2.12          0060.3e75.1c01        dynamic
```

### ARP Router
```
Router#show arp
Protocol  Address          Age (min)  Hardware Addr   Type   Interface
Internet  192.168.1.10            17  00D0.5878.0A00  ARPA   GigabitEthernet0/0/1
Internet  192.168.1.11            -   0060.3E75.1C02  ARPA   GigabitEthernet0/0/1
Internet  192.168.2.10            17  0030.A34D.B6DC  ARPA   GigabitEthernet0/0/0
Internet  192.168.2.11            11  00D0.BC0E.30B7  ARPA   GigabitEthernet0/0/0
Internet  192.168.2.12            -   0060.3E75.1C01  ARPA   GigabitEthernet0/0/0
```





