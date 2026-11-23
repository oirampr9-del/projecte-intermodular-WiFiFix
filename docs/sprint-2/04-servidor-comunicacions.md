# 04 · Servidor de comunicacions

Configuració prevista per a SRV-COM. Compareu les MAC de la taula de xarxa amb `ip -br link` i reviseu els YAML existents de Netplan abans d'aplicar el canvi. Deixeu una única definició per NIC i conserveu una còpia dels fitxers originals.

```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    wan0:
      match:
        macaddress: "08:00:27:06:b7:10"
      set-name: wan0
      dhcp4: true
    lan0:
      match:
        macaddress: "08:00:27:95:85:e5"
      set-name: lan0
      addresses: [192.168.36.1/24]
    dmz0:
      match:
        macaddress: "08:00:27:b6:1d:d1"
      set-name: dmz0
      addresses: [172.16.36.1/24]
```

Valideu amb `sudo netplan generate` i `sudo netplan try` des de la consola. En `/etc/sysctl.d/90-wififix-forward.conf`, afegiu `net.ipv4.ip_forward = 1` i carregueu la configuració amb `sudo sysctl --system`.

Comproveu `ip -br address`, `ip route` i `sysctl net.ipv4.ip_forward` abans i després de reiniciar. Des de SRV-COM, proveu la passarel·la exterior que apareix en `ip route show default`. Feu les proves LAN → DMZ des dels clients. En el pla actual es valida l'exterior des de SRV-COM i es reserva per a una fase posterior el NAT dels clients.

[Manual de Netplan per a Ubuntu 24.04](https://manpages.ubuntu.com/manpages/noble/man5/netplan.5.html)
