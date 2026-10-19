# 3. Identificació dels recursos TIC

> En aquesta fase només s'identifiquen els recursos. El disseny detallat de la infraestructura i el diagrama de xarxa es faran en el Bloc 2.

## 3.1 Ordinadors per departament

| Departament | Treballadors | Equips | Tipus |
|---|---|---|---|
| Direcció i Administració | 2 | 2 | Sobretaula |
| Comercial i Atenció al Client | 2 | 2 | Portàtils (mobilitat per a visites) |
| Suport Tècnic | 4 | 4 | Portàtils (treball en els clients) |
| Projectes i Xarxes | 3 | 3 | Estacions de treball potents (virtualització i proves) |
| Taller i Logística | 1 | 1 | Sobretaula |
| Taller (banc de proves) | — | 2 | Equips de proves i substitució |
| Sala de reunions | — | 1 | Mini PC connectat a una pantalla |
| **Total** | **12** | **15** | |

## 3.2 Servidors i funcions generals

| Servidor | Funció |
|---|---|
| Servidor de domini i fitxers | Controlador de domini (usuaris, polítiques), DNS, DHCP i carpetes compartides |
| Servidor de còpies de seguretat (NAS) | Còpies de seguretat internes i dels clients |
| Servidor de virtualització | Màquines virtuals per al gestor de tiquets, monitoratge, web interna i laboratori de proves |

## 3.3 Dispositius de xarxa

| Dispositiu | Quantitat | Funció |
|---|---|---|
| Router / firewall | 1 | Eixida a Internet, NAT, VPN i seguretat perimetral |
| Switch gestionable de 24 ports (PoE) | 2 | Connexió dels equips, servidors, punts d'accés i telèfons IP |
| Punts d'accés Wi-Fi | 3 | Cobertura de l'oficina, el taller i la sala de reunions, amb xarxa de convidats separada |
| Cablejat estructurat i armari de comunicacions (rack) | 1 | Organització i protecció de la xarxa |
| SAI | 2 | Protecció elèctrica de servidors i electrònica de xarxa |

## 3.4 Impressores i altres perifèrics

| Recurs | Quantitat | Funció |
|---|---|---|
| Impressora multifunció de xarxa | 1 | Impressió, còpia i escàner de l'oficina |
| Impressora d'etiquetes | 1 | Etiquetatge d'equips i material en el taller |
| Monitors addicionals | 8 | Doble pantalla en els llocs tècnics |
| Telèfons IP | 8 | Atenció telefònica i comunicació interna |
| Càmera i sistema d'audio per a videoconferència | 1 | Reunions amb clients |
| Discs externs i material de suport | Diversos | Transport de dades i eines dels tècnics |

## 3.5 Justificació dels recursos

- **Portàtils en Suport Tècnic i Comercial**: aquests llocs treballen sovint en les instal·lacions dels clients, per tant la mobilitat és imprescindible.
- **Estacions potents en Projectes i Xarxes**: han de poder executar màquines virtuals per a proves de configuracions abans de portar-les als clients.
- **Dos equips de proves en el taller**: permeten substituir temporalment un equip del client o reproduir una avaria.
- **Tres servidors**: separar fitxers, còpies i virtualització millora la seguretat i facilita la recuperació davant d'una fallada, sense complicar excessivament una empresa de 12 persones.
- **Dos switches PoE**: alimenten punts d'accés i telèfons IP sense font addicional, i el segon aporta capacitat i redundància.
- **Tres punts d'accés**: asseguren cobertura en tota l'oficina i el taller i permeten separar la xarxa de convidats i clients.
- **SAI**: evita pèrdues de dades i danys en servidors per talls de corrent.
- **Telèfons IP**: l'atenció telefònica és una part essencial del servei i les incidències solen arribar per aquesta via.
