# I.Exploration Local En Solo
## 1. Affichage d'informations sur la pile TCP/IP locale



**🌞 Affichez les infos des cartes réseau de votre PC**

    ipconfig /all
    
**Carte Wifi** 
    
    Realtek 8852CE WiFi 6E PCI-E NIC/40-1A-58-3B-37-EC/10.33.48.143

**Ethernet**

    Realtek Gaming GbE Family Controller/BC-0F-F3-5C-FA-C6/0

**🌞 Affichez votre gateway**

    10.33.51.254

**🌞 Déterminer la MAC de la passerelle**
    
    arp /a
    Interface : 10.33.48.143 --- 0x9
    Adresse Internet      Adresse physique      Type
    10.33.51.254          7c-5a-1c-cb-fd-a4     dynamique

## 2. Modifications des informations
### A. Modification d'adresse IP (part 1)

**🌞 Utilisez l'interface graphique de votre OS pour changer d'adresse IP**

**🌞 Il est possible que vous perdiez l'accès internet. Que ce soit le cas ou non, expliquez pourquoi c'est possible de perdre son accès internet en faisant cette opération.**

    J'ai perdu internet car je pense que quand j'ai changer d'adresse IP celle-ci était déja prise par une machine.

# II. Exploration locale en duo
## 3. Modification d'adresse IP

**🌞 Modifiez l'IP des deux machines pour qu'elles soient dans le même réseau**

    Adresse IP : 10.10.10.15

    Masque de sous-reseau : 255.255.255.0

**🌞 Vérifier à l'aide d'une commande que votre IP a bien été changée**

    commande : ipconfig 
    L'adresse a bien changé

**🌞 Vérifier que les deux machines se joignent**

    ping 10.10.10.15

 **🌞Déterminer l'adresse MAC de votre correspondant**

    commande : arp /a
    
    Interface : 10.10.10.15 --- 0xc
    Adresse Internet      Adresse physique      Type
    10.10.10.9            40-c2-ba-18-d4-2d     dynamique

    
## 4. Petit chat privé

**🌞 sur le PC client**

    nc.exe 10.10.10.09 8888


    sfqfqgsdgsdgsgsgggrregrsdfeqgsrh
    ptnrffrffdfdfdcd
    dc


**🌞 Visualiser la connexion en cours**

    netstat -a -n -b | Select-String "8888" -Context 0,1

    >   TCP    10.10.10.15:51674      10.10.10.9:8888           ESTABLISHED
    [nc.exe]

**🌞Pour aller un peu plus loin**

    .\nc.exe -l -p 8888 -s 10.10.10.15
    ;jbkhffjhfjfgfjjdds
    ee
    c bon ?
    ho REPOND

## 5. Firewall

**🌞 Activez et configurez votre firewall**

    ping 10.10.10.9

    Envoi d’une requête 'Ping'  10.10.10.9 avec 32 octets de données :
    Réponse de 10.10.10.9 : octets=32 temps=3 ms TTL=128
    Réponse de 10.10.10.9 : octets=32 temps=3 ms TTL=128
    Réponse de 10.10.10.9 : octets=32 temps=2 ms TTL=128
    Réponse de 10.10.10.9 : octets=32 temps=3 ms TTL=128
    Statistiques Ping pour 10.10.10.9:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
    Durée approximative des boucles en millisecondes :
    Minimum = 2ms, Maximum = 3ms, Moyenne = 2ms
**.**
    
    .\nc.exe -l -p 2025 -s 10.10.10.15
    l;l;l;l
    iugiug
    ok
    ok

## 6. Utilisation d'un des deux comme gateway

**🌞Tester l'accès internet**

    ping 1.1.1.1

    Envoi d’une requête 'Ping'  1.1.1.1 avec 32 octets de données :
    Réponse de 1.1.1.1 : octets=32 temps=11 ms TTL=57
    Réponse de 1.1.1.1 : octets=32 temps=12 ms TTL=57
    Réponse de 1.1.1.1 : octets=32 temps=11 ms TTL=57
    Réponse de 1.1.1.1 : octets=32 temps=13 ms TTL=57

    Statistiques Ping pour 1.1.1.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
    Durée approximative des boucles en millisecondes :
    Minimum = 11ms, Maximum = 13ms, Moyenne = 11ms
    
**🌞 Prouver que la connexion Internet passe bien par l'autre PC**

     tracert 10.10.10.9

    Détermination de l’itinéraire vers 10.10.10.9 avec un maximum de 30 sauts.

    1     4 ms     3 ms     5 ms  10.33.51.254
    2     3 ms     3 ms     2 ms  237.252.159.77.rev.sfr.net [77.159.252.237]
     3     6 ms     4 ms     5 ms  108.97.30.212.rev.sfr.net [212.30.97.108]
     4     4 ms     4 ms     4 ms  205.212.192.77.rev.sfr.net [77.192.212.205]
     5    24 ms    24 ms    23 ms  2.144.6.194.rev.sfr.net [194.6.144.2]
     6    21 ms    20 ms    21 ms  122.220.96.84.rev.sfr.net [84.96.220.122]
     7    22 ms    22 ms    21 ms  154.224.63.86.rev.sfr.net [86.63.224.154]
     8    26 ms    34 ms    25 ms  185.225.63.86.rev.sfr.net [86.63.225.185]
     9    27 ms    25 ms    28 ms  174.225.63.86.rev.sfr.net [86.63.225.174]
    10    27 ms    26 ms    26 ms  169.225.63.86.rev.sfr.net [86.63.225.169]





