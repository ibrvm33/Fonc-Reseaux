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

    
