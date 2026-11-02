# Bloc 2 · 01 - Necessitats TIC de WiFiFix

Partim de la plantilla revisada de sis persones: gerència i comercial (1), administració (1), servei tècnic (3) i sistemes i xarxes (1). Esta és una proposta per a l'empresa fictícia, pendent de validar amb un local concret.

| Departament | Necessitat | Usuaris afectats | Justificació |
|---|---|---:|---|
| Gerència i comercial | Internet, correu, pressupostos i CRM | 1 | Preparar ofertes i seguir els encàrrecs |
| Administració | Facturació, ofimàtica i impressió/escaneig en xarxa | 1 | Gestionar factures, cobraments i documentació |
| Servei tècnic | Tres portàtils, Wi-Fi i connexió Ethernet de prova | 3 | Treballar al local i en les instal·lacions dels clients |
| Servei tècnic | Diagnòstic de cablejat, cobertura i rendiment | 3 | Localitzar l'origen de les incidències i comprovar la reparació |
| Sistemes i xarxes | Administració del servidor, xarxa, permisos i monitoratge | 1 | Mantindre els serveis interns i detectar fallades |
| Tots | Sis comptes individuals i permisos per funció | 6 | Evitar comptes compartits i limitar l'accés als documents |
| Tots | Fitxers compartits i còpies recuperables | 6 | Centralitzar informació i recuperar-la en cas d'error o avaria |
| Tots | Internet i xarxa local estable | 6 | Accedir als serveis i compartir recursos |
| Gerència i Sistemes | Web corporativa pública separada dels fitxers interns | 2 responsables; públic extern | Mostrar serveis i contacte sense exposar la xarxa interna |
| Tots | Actualitzacions, protecció d'equips i accés remot controlat | 6 | Reduir incidències i protegir la informació |

## Prioritats i comprovacions previstes

1. Xarxa i Internet: els sis llocs han de poder connectar-se i resoldre noms.
2. Comptes i fitxers: cada persona accedix als recursos autoritzats; es comprova també una denegació d'accés.
3. Còpies: recuperar un fitxer de prova, amb una còpia addicional fora del local. RAID no substituïx les còpies.
4. Impressió: imprimir i escanejar des d'administració.
5. Web: accessible des de fora, amb separació de la LAN; el disseny del Bloc 2 inclourà una DMZ i un servidor de comunicacions, tal com demana l'enunciat.

## Fonts consultades

- [Enunciat PI-Q.2.1 en Aules](https://aules.edu.gva.es/fp/mod/assign/view.php?id=11792927): requisits i criteris del Bloc 2.
- [Empresa](../01-empresa.md): serveis, clients i càrrega prevista.
- [Organització](../02-organitzacio.md): sis persones i funcions.
- [Recursos TIC](../03-recursos-tic.md) i [inventari](../04-maquinari-programari.md): equips i ferramentes disponibles en la proposta.

No s'han fet entrevistes a una empresa real ni mesures en un local. Les necessitats es deduïxen de l'empresa fictícia i s'hauran de contrastar amb l'espai, el pressupost i les proves de la futura implantació.
