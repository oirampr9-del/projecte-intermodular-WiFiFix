# Bloc 2 · 05 - Recursos materials i humans

Dimensionem la proposta per als sis treballadors del [Bloc 1](../04-maquinari-programari.md). Els identificadors de xarxa són els del [pla IP](04-adrecament-ip.md) i les quantitats tenen correspondència amb el [pressupost](06-pressupost.md).

## Maquinari i serveis

| Recurs | Quantitat | Funció, requisits i motiu |
|---|---:|---|
| Lenovo ThinkCentre M720s SFF reacondicionat, i5, 16 GB i SSD 512 GB | 3 | Llocs fixos de gerència, administració i sistemes. Ethernet Gigabit i memòria suficient per a ofimàtica i diagnòstic |
| Dell Latitude 5420 reacondicionat, i5, 16 GB i SSD 256 GB | 3 | Portàtils del servei tècnic. Wi-Fi, USB i autonomia comprovada abans de comprar |
| Lenovo ThinkCentre M720s SFF de la mateixa configuració | 3 | Un SRV-LAN per a comptes i fitxers, un SRV-COM per a encaminament i un WEB-01 per a una web estàtica de càrrega baixa. El SSD de SRV-LAN limita la capacitat útil i cal revisar-la quan cresquen els documents |
| Digitus DN-10130 Gigabit PCIe | 2 | Dues targetes de perfil baix en SRV-COM, més la boca integrada, per a WAN, LAN i DMZ. Cal verificar físicament les ranures lliures i el controlador Linux |
| Synology DS223j i Seagate IronWolf 4 TB | 1 NAS + 2 discos | Destí de còpies diàries, en mirall amb uns 4 TB bruts útils. Cal validar la compatibilitat del model de disc. El mirall dona tolerància a l'avaria d'un disc |
| WD Elements Portable 2 TB | 2 | Rotació setmanal de discos xifrats per a conservar sempre una còpia fora del local. Capacitat superior a la de les dades inicials del servidor. Cal comprovar la retenció real |
| TP-Link TL-SG116P | 1 | Switch no gestionat Gigabit de 16 ports amb PoE+. S'ocupen fins a 12 ports i en queden 4 lliures |
| TP-Link EAP225 interior | 2 | Wi-Fi corporativa en punts separats, alimentats amb PoE 802.3af des del switch. Cal comprovar cobertura i revisar canals al local |
| Rack Powergreen 19″ 6U amb safata i ventilació | 1 | Per al switch i la terminació de cablejat. Els servidors SFF, el NAS i el SAI poden quedar en una prestatgeria tècnica ventilada i amb accés restringit |
| APC BX950MI-GR, 950 VA / 520 W | 1 | Quatre eixides per a SRV-LAN, NAS, SRV-COM i switch amb els AP. Previsió de càrrega de 210 W (75 + 20 + 65 + 50 W). Cal mesurar-la i provar l'autonomia i l'apagada segura de servidor i NAS. WEB-01 i l'ONT queden fora d'esta reserva |
| Brother DCP-L2660DW | 1 | Impressió i escaneig d'administració per Ethernet. Cal comprovar el flux d'escaneig des dels clients |
| Monitor AOC 24B3HA2 i teclat/ratolí Logitech MK120 ES | 3 de cada | Pantalla Full HD i controls dels llocs fixos. Confirmarem que els cables de vídeo coincidixen amb les eixides dels equips |
| iFixit Essential Electronics Toolkit | 3 | Un joc per tècnic per a obrir ordinadors i fer reparacions bàsiques |
| Kit PcCom Essential de xarxa amb verificador | 1 | Comprovador compartit per a continuïtat i mapa de fils. Inclou ferramentes de terminació |
| Adaptador TP-Link UE300 i latiguillo Cat 6 | 3 kits | Prova cablejada amb cada portàtil i substitució ràpida de cable |
| Cable Cat 6, latiguillos i terminacions | 1 lot | Previsió de 100 m de cable, 20 latiguillos (inclosos els 3 de diagnòstic) i reserva per a preses, connectors i canaleta. Cal mesurar recorreguts |
| Samsung Galaxy A16 4G | 1 | Telèfon corporatiu d'administració per a cites i assistència |
| Fibra, línia mòbil, equip d'operador i domini .es | 1 contracte de fibra/mòbil i 1 domini | Internet i telèfon, ONT/router segons operador, IP pública i nom per a la web i el correu. Cal verificar cobertura, condicions professionals i publicació HTTPS |

## Programari i llicències

| Programari | Quantitat | Funció i requisits |
|---|---:|---|
| Ubuntu Server 24.04 LTS | 3 instal·lacions | Sistema dels tres servidors. OpenSSH per a gestió i UFW/netfilter en SRV-COM |
| Samba, DNS intern i Kea DHCP | 1 de cada | En SRV-LAN. Sis comptes individuals de Samba i grups amb permisos de carpetes. DNS intern i DHCP només per a la LAN |
| Nginx i Let's Encrypt | 1 web i 1 certificat | Web estàtica HTTPS en WEB-01. Validació per DNS o obertura temporal justificada del port 80 |
| Windows 11 Pro, Defender i navegador | 6 equips | Windows amb llicència inclosa si es confirma en comprar, actualitzacions, protecció local i xifrat dels portàtils |
| LibreOffice | 2 instal·lacions | Ofimàtica de gerència i administració |
| Holded Bàsic | 1 subscripció, 2 usuaris | Facturació i CRM per a administració i gerència, amb comptes diferenciats |
| Microsoft 365 Empresa Bàsic | 6 comptes | Correu corporatiu amb domini propi i MFA. Els documents compartits continuen en el servidor local |
| Assistència ràpida de Windows | 3 equips | Suport remot a clients Windows amb consentiment i sessió iniciada pel client |
| WiFi Analyzer (open-source), Wireshark, iperf3 i utilitats IP | 3 per a Wi-Fi i 4 per a la resta | Diagnòstic autoritzat. Cal verificar compatibilitat de l'adaptador amb les captures que es vulguen fer |
| restic i DSM | 1 servidor de còpies i 1 NAS | Repositori xifrat i versionat, còpia diària al NAS i rotació externa. Sistemes custodia les claus i verifica una restauració mensual |
| Zabbix | 1 instància local | Monitoratge intern de disponibilitat i avisos d'errors de còpia. La DMZ no inicia trànsit cap a la LAN |

## Equip d'implantació

| Membre | Responsabilitat prevista |
|---|---|
| Ferran Ferrer Seguí | Preparar connexions, adreçament i regles de SRV-COM, i comprovar DHCP, DNS i separació de la DMZ |
| Mario Perez Ruiz | Preparar l'inventari, verificar les compres i compatibilitats, i configurar serveis interns, comptes i còpies |
| Ferran i Mario | Revisió creuada, proves de restauració i web, documentació i traspàs al responsable de sistemes |

És el repartiment de l'equip acadèmic per a la futura implantació. La plantilla de l'empresa fictícia continua sent de sis treballadors.

## Fonts tècniques

- [Lenovo PSREF M720 SFF](https://psref.lenovo.com/syspool/Sys/PDF/ThinkCentre/ThinkCentre_M720_SFF/ThinkCentre_M720_SFF_Spec.html) i [Ubuntu Server: Samba](https://ubuntu.com/server/docs/how-to/samba/).
- [TP-Link EAP225](https://www.tp-link.com/es/business-networking/omada-wifi-ceiling-mount/eap225/) i [Synology DS223j](https://www.synology.com/es-es/products/DS223j).
- [Documentació de restic](https://restic.readthedocs.io/) i [tarifes Holded](https://www.holded.com/es/precios).
