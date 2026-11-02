# Bloc 2 · 02 - Alternatives i viabilitat

## Necessitats de partida

WiFiFix té sis treballadors, tres ordinadors fixos i tres portàtils. Necessita comptes individuals, fitxers compartits, còpies recuperables, Internet i una web pública separada. Partim de [01-necessitats.md](01-necessitats.md). Esta proposta es deixa en revisió per al grup; no pressuposa una reunió que encara no s'ha fet.

## 1. Servidor local o servei allotjat

| Aspecte | A · Servidor local i NAS | B · Servei de documents al núvol |
|---|---|---|
| Solució | Servidor de fitxers i comptes, NAS de còpies i còpia fora del local | Sis comptes en un servei empresarial allotjat |
| Avantatges | Control de permisos i dades; fitxers locals disponibles encara que falle Internet | Accés des de fora i ampliació per usuaris; menys maquinari local |
| Limitacions | Inversió, manteniment, electricitat i risc d'avaria al local | Quota recurrent, dependència del proveïdor i d'Internet per a les funcions en línia |
| Requisits | Servidor, NAS, SAI, xarxa, espai ventilat i responsable de sistemes | Internet estable, sis comptes, permisos i política de còpies i exportació |
| Cost aproximat | Reserva pròpia de 2.000–3.000 € per servidor, NAS amb discos i SAI | Hipòtesi de 8–12 €/usuari/mes: 48–72 €/mes per sis persones; 576–864 €/any |

Són estimacions de planificació sense IVA, no ofertes ni tarifes comercials verificades. No inclouen clients, xarxa, web, Internet, mà d'obra ni totes les còpies externes. L'opció local tampoc inclou electricitat, manteniment o renovació. En el pressupost complet es compararan inversió i recurrents sobre el mateix període.

Samba permet compartir fitxers entre Ubuntu i clients Windows [1]. Microsoft 365 Empresa Básico és una referència funcional de correu, emmagatzematge i aplicacions web/mòbils [2]; no substituïx tots els serveis d'un servidor, el tallafoc ni la DMZ. No s'ha confirmat la seua tarifa comercial: els 8–12 € són una hipòtesi nostra, no el seu preu.

## 2. Xarxa cablejada o mixta

| Aspecte | C · Cable als sis llocs | D · Cable i Wi-Fi |
|---|---|---|
| Avantatges | Connexions fixes i menys dependència de la cobertura de ràdio | Cable en equips fixos i mobilitat dels portàtils |
| Limitacions | Els portàtils necessiten presa i cable; menys mobilitat | Cal revisar cobertura, canals i seguretat dels AP |
| Requisits | Router/tallafoc, switch, preses, cablejat i adaptadors si cal | Base cablejada i dos AP previstos connectats al switch |
| Cost aproximat | Reserva de 500–800 € per router/tallafoc, switch i cablejat bàsic | Base anterior + 200–400 € per dos AP i alimentació compatible |

Estes reserves pròpies exclouen instal·lació i IVA. Cal concretar preses, metres de cable, PoE o injectors i possibles obres. Cisco explica la connexió sense fils dels portàtils i la combinació amb xarxes cablejades [3]. Dos AP són una previsió del Bloc 1; no es garantix cobertura sense estudiar el local.

## 3. Proposta recomanada

Proposem **A + D: servidor local amb còpies i xarxa mixta**. Manté servidor, NAS, SAI i dos AP del Bloc 1. Equips fixos, servidor, NAS, impressora i AP anirien per cable; els tres portàtils podrien usar Wi-Fi o cable.

La tria es basa en el control dels fitxers, la disponibilitat d'un responsable de sistemes i la mobilitat dels tècnics. No demostra per si mateixa rendibilitat. Si l'espai, el pressupost o el manteniment resulten insuficients, reconsiderarem el núvol.

El disseny següent inclourà LAN, servidor de comunicacions i DMZ. La web pública estarà separada dels documents interns. Cal decidir quins serveis seran físics o virtuals i pressupostar-los. El servidor de comunicacions requerirà interfícies o VLAN adequades i regles de tallafoc; no es pressuposa que qualsevol router domèstic servisca.

## 4. Aspecte innovador aplicable

Proposem monitoratge centralitzat amb avisos de caigudes i errors de còpia, junt amb un registre de mesures Wi-Fi abans i després de cada intervenció. És una millora del procés de WiFiFix, no una invenció tecnològica: ajudaria a detectar incidències i justificar el resultat al client. Cal revisar alertes i evitar falsos positius.

Les instantànies i la replicació són una opció per conservar versions i copiar dades; TrueNAS documenta estes funcions [4]. Només es proposaran si el NAS triat les admet. Les instantànies en el mateix equip no substituïxen una còpia fora del local.

## 5. Estudi de viabilitat preliminar

| Factor | Valoració i condició pendent |
|---|---|
| Espai | Suposem tres llocs fixos i zona tècnica. Cal verificar plànol, ventilació, preses, alimentació i rack; no s'han mesurat |
| Coneixements | Tenim pràctica acadèmica amb màquines virtuals, xarxes i serveis. Cal validar permisos, LAN/DMZ i restauració en laboratori |
| Equips | Sis clients coincidixen amb la plantilla. Cal dimensionar servidor i serveis públics i verificar ports, discos, alimentació dels AP i SAI |
| Economia | Reserva parcial de 2.700–4.200 €: servidor/NAS/SAI 2.000–3.000 + xarxa 500–800 + AP 200–400. Falten clients, perifèrics, serveis DMZ/comunicacions si necessiten equips addicionals, llicències, mà d'obra, IVA i recurrents |
| Manteniment | Sistemes revisarà actualitzacions, alertes i còpies; un altre tècnic ha de poder seguir instruccions documentades |
| Recuperació | Proposem còpia diària i prova mensual. Objectius inicials: perdre com a màxim un dia de documents i recuperar el servei en una jornada. S'han de validar amb proves |

La previsió de facturació de 300.000 €/any no equival a tresoreria disponible. La viabilitat econòmica queda condicionada al pressupost complet i als costos ordinaris. Concloem que la proposta és **tècnicament plausible, amb validacions pendents**. Encara no s'ha instal·lat ni provat la infraestructura.

## Fonts consultades

Consulta: 2 de novembre de 2026. Les fonts sostenen les funcions tècniques; les reserves econòmiques són estimacions pròpies.

1. [Ubuntu Server: Samba com a servidor de fitxers](https://ubuntu.com/server/docs/how-to/samba/file-server/).
2. [Microsoft 365 Empresa Básico](https://www.microsoft.com/es-es/microsoft-365/business/microsoft-365-business-basic): referència funcional; tarifa exacta pendent de verificar.
3. [Cisco: xarxes cablejades i sense fils](https://www.cisco.com/site/us/en/learn/topics/small-business/wireless-network.html).
4. [TrueNAS: tasques de replicació](https://www.truenas.com/docs/scale/26/dataprotection/replication/).
5. [Enunciat de l'activitat](https://aules.edu.gva.es/fp/mod/assign/view.php?id=11792927) i [necessitats](01-necessitats.md).
