# TP3 : On va router des trucs

## 0. Prérequis

## I. ARP

**🌞Générer des requêtes ARP**

    ping 10.3.1.11

    PING 10.3.1.11 (10.3.1.11) 56(84) bytes of data.
    64 bytes from 10.3.1.11: icmp_seq=1 ttl=64 time=1.14 ms
    64 bytes from 10.3.1.11: icmp_seq=2 ttl=64 time=1.11 ms

    ping 10.3.1.12

    PING 10.3.1.12 (10.3.1.12) 56(84) bytes of data.
    64 bytes from 10.3.1.12: icmp_seq=1 ttl=64 time=2.21 ms
    64 bytes from 10.3.1.12: icmp_seq=2 ttl=64 time=1.23 ms

    ip neigh show

    10.3.1.12 dev enp0s8 lladdr 08:00:27:20:8b:45 STALE
    10.3.1.1 dev enp0s8 lladdr 0a:00:27:00:00:17 REACHABLE

    ip neigh show

    10.3.1.11 dev enp0s3 lladdr 08:00:27:9d:f4:c7 STALE
    10.33.10.2 dev enp0s3 FAILED
    10.3.1.1 dev enp0s3 lladdr 0a:00:27:00:00:17 DELAY


    08:00:27:9d:f4:c7
    08:00:27:20:8b:45

## 2. Analyse de trames

**🌞Analyse de trames**

