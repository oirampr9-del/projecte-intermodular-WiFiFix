# Bloc 2 · 04 - Adreçament IP i noms

Seguim el [disseny de xarxa](03-disseny-xarxa.md). Les adreces són les previstes per a la implantació.

| Zona | Xarxa | Màscara | Hosts vàlids | Difusió |
|---|---|---|---|---|
| LAN | 192.168.36.0/24 | 255.255.255.0 | 192.168.36.1–254 | 192.168.36.255 |
| DMZ | 172.16.36.0/24 | 255.255.255.0 | 172.16.36.1–254 | 172.16.36.255 |
| WAN | Segons l'operador. En laboratori, NAT VirtualBox 10.0.2.0/24 | Segons WAN | DHCP de l'operador o VirtualBox | Segons WAN |

| Equip o interfície | Xarxa | Adreça prevista | Prefix | Passarel·la |
|---|---|---|---|---|
| SRV-COM (WAN) | WAN | DHCP. En NAT VirtualBox, 10.0.2.15 habitualment | Segons WAN (/24 en laboratori) | Segons WAN (10.0.2.2 en laboratori) |
| SRV-COM (LAN) | LAN | 192.168.36.1 fixa | /24 | — |
| SRV-COM (DMZ) | DMZ | 172.16.36.1 fixa | /24 | — |
| SRV-LAN | LAN | 192.168.36.10 fixa | /24 | 192.168.36.1 |
| NAS-01 | LAN | 192.168.36.20 fixa | /24 | 192.168.36.1 |
| IMP-01 | LAN | 192.168.36.30 fixa | /24 | 192.168.36.1 |
| AP-01 | LAN | 192.168.36.41 fixa | /24 | 192.168.36.1 |
| AP-02 | LAN | 192.168.36.42 fixa | /24 | 192.168.36.1 |
| PC-SIS | LAN | 192.168.36.50 fixa | /24 | 192.168.36.1 |
| PC-GER i PC-ADM | LAN | DHCP, 192.168.36.100–149 | /24 | 192.168.36.1 |
| PT-TEC01 a PT-TEC03 | LAN | DHCP, 192.168.36.100–149 | /24 | 192.168.36.1 |
| SW-LAN | LAN | Sense IP de gestió (switch no gestionat) | — | — |
| WEB-01 | DMZ | 172.16.36.10 fixa | /24 | 172.16.36.1 |

SRV-LAN assignaria IP només a la LAN i anunciaria el DNS intern 192.168.36.10 i la passarel·la 192.168.36.1. El rang de 50 adreces deixa marge per als portàtils amb més d'una interfície. WEB-01 utilitzaria un resolutor extern autoritzat. La ruta per defecte de SRV-COM correspon a la WAN.

## Comprovació

Les IP fixes de LAN (.1, .10, .20, .30, .41, .42 i .50) són úniques i estan fora del rang DHCP. Les de DMZ (.1 i .10) són úniques dins de 172.16.36.0/24. Les tres xarxes de laboratori són diferents. En producció cal verificar que l'operador no lliure una subxarxa que se solape amb LAN o DMZ.

La DMZ té interfície i cable propis. El tallafoc permet publicar HTTPS cap a WEB-01 i denega les connexions noves iniciades des de DMZ cap a LAN. Així la web pública queda separada dels comptes i documents. Durant les proves verificarem l'assignació DHCP, les passarel·les, la resolució DNS i el bloqueig DMZ → LAN.

Font per als rangs privats: [RFC 1918](https://www.rfc-editor.org/rfc/rfc1918.html).
