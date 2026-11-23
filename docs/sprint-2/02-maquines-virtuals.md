# 02 · Màquines virtuals

Les cinc VMs s'han creat en VirtualBox 7.2.16 al PC de Ferran amb discos VDI dinàmics. La instal·lació i la transferència al PC comú es registraran segons el treball de cada membre.

| VM | Funció | Sistema previst | RAM | vCPU | Disc | Estat |
|---|---|---|---:|---:|---:|---|
| SRV-COM | Encaminament i Kea | Ubuntu Server 24.04.5 LTS | 1 GiB | 1 | 15 GiB | Instal·lant (reintent; vegeu 07) |
| SRV-LAN | Servidor intern | Windows Server 2025 Standard Evaluation (experiència d'escriptori) | 3 GiB | 2 | 50 GiB | Instal·lant |
| PC-ADM | Client d'administració | Windows 11 25H2 | 4 GiB | 2 | 64 GiB | ISO muntada, EFI i TPM 2.0 |
| PT-TEC01 | Client tècnic | Linux Mint 22.3 Cinnamon | 2 GiB | 2 | 25 GiB | ISO muntada |
| WEB-01 | Servidor de la DMZ | Ubuntu Server 24.04.5 LTS | 1 GiB | 1 | 15 GiB | ISO muntada |

S'han verificat set MAC virtuals diferents. Cal capturar una sessió iniciada en cada SO amb `hostname` i `whoami`. SRV-LAN es prepara amb IP fixa. L'Active Directory correspon al Sprint 3.

![Consola de SRV-COM durant l'arrancada des de la ISO](../../img/sprint-2/srv-com-instal·lador.png)

*Arrancada del suport d'instal·lació de SRV-COM.*

## Actualització 23/11/2026

La ISO de Windows Server 2025 està a `/home/batoi/winserv25.iso` i muntada a SRV-LAN. La màquina està creada amb 3 GiB RAM, 2 vCPU i disc virtual de 50 GiB, connectada a `wififix-lan`. La VM s'ha agrupat a `/WiFiFix Sprint 2`. S'ha intentat iniciar l'instal·lador, però després de «Loading files…» la consola ha quedat negra. Per tant, Windows Server encara no està instal·lat ni s'ha validat l'inici de sessió.

![Captura de SRV-LAN durant el problema d'arrencada](../../img/sprint-2/srv-lan-pantalla-negra.png)

*Pantalla negra observada després de carregar els fitxers d'instal·lació.*

### Instal·lació de SRV-LAN (23/11/2026)

La pantalla negra posterior a «Loading files…» no era un error de configuració: la ISO té 8 GB i l'instal·lador tardava a mostrar l'assistent. La VM manté BIOS, arrencada DVD → disc, controladora SATA i xarxa interna `wififix-lan`. Decisions de l'assistent: idioma i teclat Español, edició **Standard Evaluation (experiència d'escriptori)** (admet gestió gràfica i serveix per al Sprint 3), disc de 50 GB buit amb particions automàtiques. No s'instal·la Active Directory en aquest sprint.

![Selecció de l'edició a SRV-LAN](../../img/sprint-2/srv-lan-edicio-escriptori.png)

*Edició escollida a l'assistent de SRV-LAN.*

![Resum previ a la instal·lació de SRV-LAN](../../img/sprint-2/srv-lan-assistent-llest-per-instalar.png)

*Resum de l'assistent abans de copiar fitxers; l'inici de sessió encara no està validat.*

### Instal·lació de SRV-COM (23/11/2026)

La ISO d'Ubuntu Server 24.04.5 no estava muntada i s'ha muntat des de `Descargas`. L'instal·lador detecta les tres interfícies (`enp0s3` NAT amb DHCP, `enp0s8` i `enp0s9` en xarxes internes) i es fa servir el disc de 15 GB amb LVM (`/` 10 GB, `/boot` 1,75 GB). Les IP fixes es configuren després de la instal·lació.

![Interfícies de SRV-COM a l'instal·lador](../../img/sprint-2/srv-com-interficies-instalador.png)

*Les tres interfícies de SRV-COM vistes per l'instal·lador.*

![Particions de SRV-COM](../../img/sprint-2/srv-com-particions-instalador.png)

*Esquema de particions proposat per a SRV-COM.*
