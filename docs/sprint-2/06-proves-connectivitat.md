# 06 · Proves de connectivitat

| Origen | Destinació o comprovació | Procediment | Resultat esperat | Obtingut | Evidència |
|---|---|---|---|---|---|
| Cinc VMs | Arrancada i sessió | `hostname` i `whoami` | Cinc sessions amb noms correctes | Pendent | — |
| Cinc VMs | Adreces i noms | Windows `ipconfig /all`; Linux `hostnamectl` i `ip -br address` | Coincidència amb la taula IP i cap duplicat | Pendent | — |
| PC-ADM | DHCP de LAN | `ipconfig /release`, `ipconfig /renew`, `ipconfig /all` | IP .100–149, /24, passarel·la .1 | Pendent | — |
| PT-TEC01 | DHCP de LAN | Reconnectar Ethernet i mostrar `nmcli device show` i `ip route` | IP .100–149, /24, passarel·la .1 | Pendent | — |
| SRV-COM | Concessions | Revisar `/var/lib/kea/kea-leases4.csv` | IP, MAC i temps de cada client | Pendent | — |
| PC-ADM i PT-TEC01 | SRV-LAN | `ping 192.168.36.10` | Resposta per LAN | Pendent | — |
| PC-ADM i PT-TEC01 | SRV-COM LAN | `ping 192.168.36.1` | Resposta de la passarel·la | Pendent | — |
| WEB-01 | SRV-COM DMZ | `ping -c 4 172.16.36.1` | Resposta de la passarel·la | Pendent | — |
| PC-ADM i PT-TEC01 | WEB-01 | Ping a `172.16.36.10`, `tracert -d 172.16.36.10` en Windows i `tracepath -n 172.16.36.10` si està disponible en Linux | Resposta a través de SRV-COM | Pendent | — |
| SRV-COM i clients | Rutes i reenviament | `ip -br address`, `ip route`, `sysctl net.ipv4.ip_forward`; `route print -4` en Windows | Reenviament a 1 després de reiniciar i rutes correctes | Pendent | — |
| SRV-COM | Passarel·la exterior | `ip route show default` i `ping -c 4 10.0.2.2` si és la passarel·la detectada | Ruta per WAN i resposta | Pendent | — |

Si falla un ping, reviseu IP, passarel·la i tallafoc. Si cal, permeteu només l'ICMP de prova des de la subxarxa corresponent. Registreu la correcció i repetiu la prova.
