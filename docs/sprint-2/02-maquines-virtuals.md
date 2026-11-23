# 02 · Màquines virtuals

Les cinc VMs s'han creat en VirtualBox 7.2.16 al PC de Ferran amb discos VDI dinàmics. La instal·lació i la transferència al PC comú es registraran segons el treball de cada membre.

| VM | Funció | Sistema previst | RAM | vCPU | Disc | Estat |
|---|---|---|---:|---:|---:|---|
| SRV-COM | Encaminament i Kea | Ubuntu Server 24.04.5 LTS | 1 GiB | 1 | 15 GiB | Instal·lador arrancat |
| SRV-LAN | Servidor intern | Windows Server 2025 | 3 GiB | 2 | 50 GiB | ISO pendent |
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
