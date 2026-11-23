# Sprint 2 · 01 - Pla d'intervenció

> **Esborrany del 16 de novembre de 2026.** Aquest document és la planificació que fem abans d'implantar res. Les dades marcades com a **Pendent** encara s'han de confirmar i cap màquina virtual està creada encara.

## 1. Punt de partida

En la SA1 vam dissenyar la xarxa de WiFiFix amb una LAN, una DMZ i un servidor de comunicacions (SRV-COM) amb tres interfícies ([disseny de xarxa](../sprint-1/bloc-2/03-disseny-xarxa.md) i [adreçament IP](../sprint-1/bloc-2/04-adrecament-ip.md)). En aquest sprint muntem una versió mínima d'eixa infraestructura amb cinc màquines virtuals. Els sis treballadors es representen amb dos clients de prova; no fem una VM per cada treballador ni simulem el NAS, la impressora o els AP.

Conservem les xarxes de la SA1:

| Zona | Xarxa | Passarel·la | Equips en aquest sprint |
|---|---|---|---|
| LAN | 192.168.36.0/24 | 192.168.36.1 (SRV-COM) | SRV-LAN, PC-ADM, PT-TEC01 |
| DMZ | 172.16.36.0/24 | 172.16.36.1 (SRV-COM) | WEB-01 |
| Exterior | NAT de VirtualBox | La del NAT (es comprovarà) | SRV-COM |

### Canvis respecte a la SA1

L'enunciat del Sprint 2 fixa una estructura comuna per a tots els grups, i per això canviem algunes coses de la proposta original:

| Què deia la SA1 | Què fem en el Sprint 2 | Motiu |
|---|---|---|
| DHCP (Kea) i DNS al servidor intern SRV-LAN | DHCP (Kea) al servidor de comunicacions SRV-COM, només per a la LAN | L'enunciat demana el DHCP en el servidor Linux de comunicacions. Mantenim Kea, que és el servei que ja havíem triat |
| SRV-LAN amb Ubuntu Server i Samba | SRV-LAN amb Windows Server | L'estructura comuna demana un servidor intern Windows, preparat per a Active Directory en el Sprint 3 |
| Sis clients Windows 11 Pro | Un client Windows i un client Linux de prova | Es demana provar la xarxa i el DHCP amb els dos tipus de client |
| DHCP anuncia el DNS intern 192.168.36.10 | **Proposta:** en el Sprint 2 no s'anuncia DNS | El DNS corporatiu arriba en el Sprint 3 i l'enunciat només vol anunciar DNS si és accessible. **Pendent de confirmar amb el professor** |

La resta de decisions de la SA1 (subxarxes, IP fixes dels servidors, rang DHCP 192.168.36.100–149 i ruta per defecte de SRV-COM per la WAN) es mantenen. Quan acabe el sprint actualitzarem els documents de la SA1 que calga o deixarem una nota que remeta a aquest apartat.

## 2. Màquines previstes

| VM | Funció en el Sprint 2 | Sistema | Adaptadors de VirtualBox | IP |
|---|---|---|---|---|
| SRV-COM | Encaminament i DHCP de la LAN | Ubuntu Server 24.04 LTS | 1: NAT · 2: `wififix-lan` · 3: `wififix-dmz` | WAN per DHCP del NAT · 192.168.36.1/24 · 172.16.36.1/24 |
| SRV-LAN | Servidor intern, preparat per al Sprint 3 | Windows Server 2025 | `wififix-lan` | 192.168.36.10/24 fixa |
| PC-ADM | Client Windows (lloc d'administració) | Windows 11 | `wififix-lan` | DHCP |
| PT-TEC01 | Client Linux (portàtil tècnic) | Linux Mint 22.x | `wififix-lan` | DHCP |
| WEB-01 | Servidor de la DMZ, preparat per als serveis posteriors | Ubuntu Server 24.04 LTS | `wififix-dmz` | 172.16.36.10/24 fixa |

**Pendent:** confirmar amb el professor les versions exactes dels sistemes.

Cap client ni servidor intern té adaptador NAT propi. Així tot el trànsit cap a fora ha de passar per SRV-COM. En el Sprint 2 no configurem NAT (*masquerade*) per als clients, perquè l'enunciat no exigeix que isquen a Internet; si fera falta, ho comentaríem abans amb el professor.

## 3. Seqüència de tasques, dependències i temps

Tenim 5 setmanes i 10 hores lectives, unes 2 hores per setmana.

| Setmana | Tasca | Depén de | Temps previst | Responsable | Col·labora |
|---|---|---|---:|---|---|
| S1 | S2 · 00 Preparar amfitrió, ISO i accessos | — | 0,5 h | Ferran | Mario |
| S1 | S2 · 01 Pla d'intervenció i Trello | S2 · 00 | 1,5 h | Ferran i Mario | — |
| S2 | S2 · 02 Crear les VMs i instal·lar els sistemes | S2 · 00, S2 · 01 | 2 h | Ferran (SRV-COM, WEB-01) i Mario (SRV-LAN, PC-ADM, PT-TEC01) | — |
| S3 | S2 · 03 LAN, DMZ i adreçament | S2 · 02 | 1 h | Ferran | Mario |
| S3 | S2 · 04 Servidor de comunicacions i encaminament | S2 · 03 | 1 h | Ferran | Mario (revisió) |
| S4 | S2 · 05 Servei DHCP en SRV-COM | S2 · 04 | 2 h | Mario | Ferran (revisió) |
| S5 | S2 · 06 Proves de connectivitat | S2 · 05 | 1,5 h | Ferran i Mario (creuades) | — |
| S5 | S2 · 08 README i lliurament | Totes | 0,5 h | Ferran i Mario | — |
| Totes | S2 · 07 Seguiment i incidències | S2 · 01 | 10 min per sessió, inclosos en cada tasca | Ferran i Mario | — |

Les instal·lacions de Windows poden durar més d'una sessió. Per això, en la S2 cada membre instal·la les seues màquines en paral·lel al seu ordinador i després les reunim a l'amfitrió final (apartat 5). L'ordre no es pot canviar: sense les xarxes i les IP fixes no es pot configurar l'encaminament, i sense encaminament no té sentit provar el DHCP i la connectivitat.

## 4. Recursos necessaris

### Ordinadors de l'equip

| Ordinador | CPU | RAM | Disc lliure | VirtualBox | Ús |
|---|---|---|---|---|---|
| PC de Ferran (aula, Linux Mint 22.1) | 4 fils | 15 GB | 109 GB a `/home` (ocupat al 88 %) | 7.2.16 | Amfitrió final de les cinc VMs |
| PC de Mario (aula) | **Pendent** | **Pendent** (8,5 GB lliures) | 55 GB | **Pendent** | Instal·lacions en paral·lel i exportació en OVA |

### Recursos de cada VM

Ajustem els recursos als mínims de cada sistema i a la capacitat de l'amfitrió. Els discos són dinàmics, així que l'espai real ocupat és menor que la mida màxima.

| VM | RAM | vCPU | Disc (màxim) | Ocupació real aproximada |
|---|---:|---:|---:|---:|
| SRV-COM | 1 GB | 1 | 15 GB | 4–5 GB |
| SRV-LAN | 3 GB | 2 | 50 GB | 15–20 GB |
| PC-ADM | 4 GB | 2 | 64 GB | 20–25 GB |
| PT-TEC01 | 2 GB | 2 | 25 GB | 10–12 GB |
| WEB-01 | 1 GB | 1 | 15 GB | 4–5 GB |
| **Total** | **11 GB** | | | **~55–65 GB** |

Amb les cinc engegades queden uns 4 GB per al sistema amfitrió. Per a la majoria de proves no cal tindre-les totes enceses alhora.

### Imatges i programari

- ISO d'Ubuntu Server 24.04 LTS, Windows Server 2025, Windows 11 i Linux Mint 22.x, descarregades de les webs oficials o del lloc que indique el professor. Es guarden fora del repositori.
- VirtualBox 7.2, Kea DHCP (paquets d'Ubuntu), GitHub, Trello i un editor de diagrames.
- **Pendent:** confirmar si els Windows són versions d'avaluació i quan caduquen.

## 5. Distribució de les màquines i entorn comú

Les xarxes internes de VirtualBox només funcionen dins del mateix ordinador. Si dues VMs estan en ordinadors diferents, no es veuen encara que les xarxes tinguen el mateix nom. Per això **les cinc VMs funcionaran en un únic amfitrió**, el PC de Ferran, que és el que té més disc lliure.

1. Ferran crea SRV-COM i WEB-01 directament a l'amfitrió.
2. Mario instal·la SRV-LAN, PC-ADM i PT-TEC01 al seu PC, una cada vegada, perquè no hi caben totes alhora.
3. Mario exporta cada VM acabada en format OVA (Fitxer → Exportar servei virtualitzat) i la copia a l'amfitrió amb un disc USB o una carpeta compartida de l'aula.
4. Ferran importa l'OVA amb l'opció de **generar noves adreces MAC** per a tots els adaptadors i comprova que no n'hi ha cap de repetida.
5. Una vegada importada i comprovada, Mario pot esborrar la VM del seu PC per alliberar espai.

Les xarxes internes es diran `wififix-lan` i `wififix-dmz`. A l'amfitrió ja hi ha xarxes internes d'altres assignatures (per exemple `intnet`, `sox` o `blackmesa`); amb noms propis evitem barrejar-les.

## 6. Permisos i autoritzacions

| Què | A qui ho demanem | Estat |
|---|---|---|
| Versions de SO i hipervisor que podem utilitzar | Professor | **Pendent** |
| Llicències o versions d'avaluació de Windows | Professor | **Pendent** |
| Ús del PC de Ferran com a amfitrió durant les cinc setmanes i els sprints següents | Professor | **Pendent** |
| Repositori de GitHub privat amb accés del professorat | Mario (propietari del repositori) | **Pendent** |
| Accés del professorat al tauler de Trello | Mario (propietari del tauler) | **Pendent** |

## 7. Riscos i mesures preventives

| Activitat | Risc | Mesura preventiva | Mitjans de protecció o recuperació |
|---|---|---|---|
| Treball prolongat davant la pantalla | Fatiga visual i males postures | Pantalla a l'altura dels ulls, cadira ben regulada i pauses curtes cada hora | Normes de l'aula sobre l'ús dels llocs de treball |
| Connectar discs USB o manipular equips | Contacte elèctric o avaria per manipular amb l'equip encés | No obrir els equips, no tocar regletes ni cables amb l'equip encés i avisar el professor davant de qualsevol problema elèctric | Instal·lació elèctrica de l'aula i professor responsable |
| Instal·lacions i canvis de configuració | Pèrdua de dades o d'una VM que ja funcionava | Instantània abans de cada canvi important i còpia de la documentació en GitHub | Instantànies de VirtualBox, OVA exportades i historial de commits |
| Configuració de xarxa i DHCP | Afectar la xarxa de l'aula o altres equips | No utilitzar mai el mode pont amb el DHCP actiu: només NAT i xarxes internes. Comprovar que el DHCP escolta només la LAN | Xarxes internes aïllades de VirtualBox |
| Pujar fitxers al repositori | Publicar ISO, discos, contrasenyes o dades personals | Revisar cada commit abans de pujar-lo | Repositori privat i revisió creuada |

**Pendent:** relacionar cada mesura amb el punt concret de les normes de l'aula.

## 8. Imprevistos possibles i solucions previstes

| Imprevist | Com el detectarem | Solució prevista |
|---|---|---|
| Falta de RAM a l'amfitrió | L'amfitrió va molt lent o una VM no arranca per falta de memòria | Engegar només les VMs necessàries per a cada prova i baixar la RAM de SRV-LAN o PC-ADM dins dels mínims del sistema |
| Espai insuficient a l'amfitrió | Avís de VirtualBox o `df -h` per baix de 15 GB lliures | Esborrar instantànies antigues, guardar les OVA en un disc extern i, amb permís, eliminar VMs velles d'altres pràctiques |
| Una instal·lació no arranca | La VM es queda en negre o torna a l'instal·lador | Revisar l'ISO, el tipus de sistema i el firmware (EFI/TPM en Windows 11) i, si cal, tornar-la a crear des de zero |
| Interfícies de SRV-COM confoses | La IP de la LAN apareix a la interfície equivocada | Identificar cada interfície per la seua MAC abans d'escriure la configuració de netplan |
| Llicència d'avaluació de Windows caducada abans dels sprints següents | Avís d'activació del sistema | Comprovar la data de caducitat en instal·lar i consultar el professor |

## 9. Organització en Trello i seguiment

Utilitzem el [tauler de WiFiFix](https://trello.com/b/AtTTwzrK/projecte-intermodular-wififix). Hem afegit les llistes **Pendent**, **En procés** i **Finalitzat** per al Sprint 2. Les targetes del Sprint 1 queden a la llista **Sprint 1 - Fet**, així es conserva l'historial. Cada targeta (S2 · 00 a S2 · 08) té responsable, descripció, objectiu, dependències, criteris de finalització i una checklist.

**Al final de cada sessió**, els dos membres dediquem uns 10 minuts a:

1. Moure les targetes segons el seu estat i marcar els passos fets de la checklist.
2. Anotar en el [registre de seguiment](07-seguiment-incidencies.md) la feina prevista, la feina feta, el temps i els problemes.
3. Comparar l'avanç amb la taula de l'apartat 3 i decidir què fem en la sessió següent.
4. Fer un commit amb els canvis de la documentació.

**Si una desviació afecta el lliurament** (per exemple, una tasca que es retarda més d'una setmana o un canvi en l'abast), ho comunicarem al professor a classe o per Aules, i deixarem constància de la comunicació i de l'ajust acordat en el registre d'incidències.

## 10. Fonts

- Enunciat del Sprint 2, SA2 del Projecte Intermodular.
- [Manual de VirtualBox: xarxes internes i NAT](https://www.virtualbox.org/manual/topics/networkingdetails.html).
- [Ubuntu Server: configuració de xarxa amb netplan](https://documentation.ubuntu.com/server/explanation/networking/configuring-networks/).
- [Documentació de Kea DHCP](https://kea.readthedocs.io/).
