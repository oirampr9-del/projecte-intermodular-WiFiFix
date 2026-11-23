# 05 · DHCP de la LAN

Configuració prevista de Kea en SRV-COM. La concessió és d'una hora. Les IP fixes de la LAN (.1 i .10) queden fora del rang. En este sprint no s'anuncia DNS corporatiu. S'ha comprovat que el VirtualBox d'este amfitrió no té cap DHCP associat a `wififix-lan`.

Instal·leu `kea-dhcp4-server` quan funcione la WAN. Feu una còpia de `/etc/kea/kea-dhcp4.conf` i configureu-lo així:

```json
{
  "Dhcp4": {
    "interfaces-config": { "interfaces": ["lan0"] },
    "lease-database": {
      "type": "memfile",
      "persist": true,
      "name": "/var/lib/kea/kea-leases4.csv"
    },
    "valid-lifetime": 3600,
    "subnet4": [
      {
        "id": 1,
        "subnet": "192.168.36.0/24",
        "pools": [{"pool": "192.168.36.100 - 192.168.36.149"}],
        "option-data": [{"name": "routers", "data": "192.168.36.1"}]
      }
    ]
  }
}
```

Valideu amb `sudo kea-dhcp4 -t /etc/kea/kea-dhcp4.conf`. Habiliteu i reinicieu `kea-dhcp4-server` i reviseu `systemctl status kea-dhcp4-server`. Renoveu les concessions dels dos clients i compareu les IP i MAC amb el CSV de Kea, incloent-hi temps de validesa i expiració.

[Guia de Kea d'Ubuntu Server](https://ubuntu.com/server/docs/how-to/networking/install-isc-kea/)
