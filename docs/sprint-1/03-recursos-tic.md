# 03 - Recursos informàtics

## Què necessitem

Perquè WiFiFix funcione necessitem ordinadors per als treballadors, una xarxa interna, un servidor i ferramentes per a les reparacions

Ací només expliquem què ens faria falta, els models i els preus ja els mirarem en el Bloc 2

## Ordinadors

| Departament | Quantitat | Tipus |
|---|---:|---|
| Gerència i comercial | 1 | Sobretaula |
| Administració | 1 | Sobretaula |
| Servei tècnic | 3 | Portàtils |
| Sistemes i xarxes | 1 | Sobretaula |
| **Total** | **6** | |

Hem triat portàtils per als tècnics perquè moltes vegades han d'anar a casa dels clients o a altres empreses

Els altres tres poden utilitzar ordinadors fixos a l'oficina

## Servidor i còpies de seguretat

**1 servidor principal** per guardar documents compartits, gestionar usuaris i permisos i tindre alguns serveis interns

**1 NAS** per guardar còpies de seguretat i recuperar fitxers si hi ha algun problema, també seria bona idea tindre una còpia fora del local

## Xarxa

| Dispositiu | Quantitat | Per a què serveix |
|---|---:|---|
| Router amb firewall | 1 | Internet i protecció de la xarxa |
| Switch | 1 | Connectar ordinadors, servidor i altres equips per cable |
| Punts d'accés Wi-Fi | 2 | Donar cobertura sense fils al local |
| Armari rack | 1 | Tindre els equips de xarxa ordenats |
| SAI | 1 | Evitar que el servidor s'apague de colp si falla la llum |

Els dos punts d'accés ens ajudarien a cobrir el local, encara que la quantitat final dependrà de la grandària i de les parets

## Impressores i ferramentes

- 1 impressora multifunció de xarxa per imprimir i escanejar
- 3 monitors per als ordinadors fixos
- 3 teclats i 3 ratolins
- 3 equips de ferramentes, un per cada tècnic
- 1 comprovador de cablejat per revisar les connexions Ethernet
- 1 telèfon corporatiu per atendre els clients

## Per què hem triat això

Els sis treballadors tindrien un ordinador cadascun i els tècnics podrien portar els portàtils a les instal·lacions

El servidor serviria per compartir fitxers i controlar els usuaris, el NAS per fer còpies i els equips de xarxa per connectar-ho tot

Pensem que és suficient per començar sense comprar material que no necessitem encara


## Diagnòstic específic de xarxes

| Ferramenta | Quantitat i destinataris | Ús previst |
|---|---|---|
| Comprovador de cablejat Ethernet | 1 compartit pel servei tècnic | Detectar fils oberts, curtcircuits i errors en l'ordre dels parells. És el mateix comprovador de l'inventari anterior |
| Adaptador USB-Ethernet i cable de xarxa de prova | 3 kits, un per portàtil tècnic | Connectar-se per cable i descartar problemes de Wi-Fi o del cable del client |
| Analitzador Wi-Fi | 3 instal·lacions en els portàtils tècnics | Revisar senyal, canals i interferències abans i després de col·locar els punts d'accés |
| Wireshark | 4 instal·lacions: tres tècnics i sistemes | Analitzar captures de trànsit quan siga necessari i amb autorització del client |
| iperf3 | 4 instal·lacions: tres tècnics i sistemes | Mesurar el rendiment entre dos equips autoritzats de la xarxa local |
| ping, traceroute/tracert, ip/ipconfig i nslookup | En els 4 equips tècnics | Comprovar connectivitat, ruta, configuració IP i resolució DNS |

Les aplicacions s'utilitzen en els equips ja comptats; no requerixen ordinadors addicionals. Compartim el comprovador perquè les visites es poden planificar. Si coincidixen diverses instal·lacions, revisarem si cal un segon aparell.

Un comprovador bàsic verifica la continuïtat i el mapa de fils, però no certifica una categoria de cablejat. Si un contracte exigix certificació, pressupostaríem el lloguer d'un certificador o el servei d'una empresa especialitzada.

En cada intervenció registraríem l'estat inicial, la prova realitzada, el canvi i el resultat final. No faríem captures ni exploracions de xarxes alienes sense autorització. Els models, compatibilitats i costos es concretaran en el Bloc 2.
