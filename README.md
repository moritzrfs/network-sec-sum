# Zusammenfassung Network Security 22

# Inhalt
- [Zusammenfassung Network Security 22](#zusammenfassung-network-security-22)
- [Inhalt](#inhalt)
- [Weitere Dokumente](#weitere-dokumente)
  - [ISO/OSI Modell](#isoosi-modell)
  - [VLAN](#vlan)
    - [VLAN Konventionen](#vlan-konventionen)
  - [LAN](#lan)
    - [Angriffsvektoren LAN](#angriffsvektoren-lan)
    - [Absicherung LAN](#absicherung-lan)
  - [WLAN](#wlan)
    - [Angriffsvektoren WLAN](#angriffsvektoren-wlan)
    - [Absicherung WLAN](#absicherung-wlan)
  - [WAN](#wan)
    - [Angriffsvektoren WAN](#angriffsvektoren-wan)
    - [Absicherung WAN](#absicherung-wan)
  - [Firewall](#firewall)
    - [Angriffsvektoren Firewall](#angriffsvektoren-firewall)
    - [Absicherung Firewall](#absicherung-firewall)
  - [IDS/IPS](#idsips)
    - [Angriffsvektoren IDS/IPS](#angriffsvektoren-idsips)
    - [Absicherung IDS/IPS](#absicherung-idsips)
  - [WEB/WAF](#webwaf)
    - [ByPass Techniken](#bypass-techniken)
    - [Angriffsvektoren WEB/WAF](#angriffsvektoren-webwaf)
    - [Absicherung WEB/WAF](#absicherung-webwaf)
  - [VPN](#vpn)
    - [Angriffsvektoren VPN](#angriffsvektoren-vpn)
    - [Absicherung VPN](#absicherung-vpn)
  - [PKI](#pki)
    - [Angriffsvektoren PKI](#angriffsvektoren-pki)
    - [Absicherung PKI](#absicherung-pki)
  - [SSL Inspection](#ssl-inspection)
    - [Problemstellung SSL Inspection](#problemstellung-ssl-inspection)
  - [Scanning](#scanning)
  - [Rechtliche Aspekte Scanning](#rechtliche-aspekte-scanning)
  - [SIEM](#siem)
    - [Zentraler Logserver](#zentraler-logserver)
    - [SIEM](#siem-1)
    - [SOC (Security Operations Center) Managed Service](#soc-security-operations-center-managed-service)
  - [Gesetze und Normen](#gesetze-und-normen)
  - [Hardening](#hardening)
    - [Switch Hardening](#switch-hardening)
  - [DDOS](#ddos)
    - [Absicherung DDOS](#absicherung-ddos)
  - [SDWAN](#sdwan)
    - [Vorteile modernes SDWAN](#vorteile-modernes-sdwan)
  - [Cloud Security](#cloud-security)
    - [Cloud Security Verantwortlichkeiten](#cloud-security-verantwortlichkeiten)
    - [Absicherung Cloud](#absicherung-cloud)
      - [Conditional Access](#conditional-access)
  - [OSINT](#osint)
    - [OSINT Schritte](#osint-schritte)
  - [E-Mail Security](#e-mail-security)
    - [Angriffsvektoren E-Mail](#angriffsvektoren-e-mail)
    - [Absicherung E-Mail](#absicherung-e-mail)
  - [IOT](#iot)
  - [Operational Technology (OT)](#operational-technology-ot)
    - [Fr??her vs Heute](#fr??her-vs-heute)
    - [Absicherung OT](#absicherung-ot)
    - [OT vs IT](#ot-vs-it)
  - [NAC](#nac)
    - [Zero Trust Ansatz](#zero-trust-ansatz)

# Weitere Dokumente
[Abk??rzungen](abbrevations.md)
[Beispiel Pr??fungsaufgaben](example-questions.md)
## ISO/OSI Modell

| Nr | Schicht | Protokoll | Einheiten | Ger??te |
|:--:|:-------:|:---------:|:---------:|:--------:|
| 7 | Anwendung | HTTP, FTP, SMTP, DNS | Daten | Gateway, Proxy, L4-7-Switch |
| 6 | Darstellung | AHTTP, FTP, SMTP, DNS | Daten | Gateway, Proxy, L4-7-Switch |
| 5 | Sitzung | HTTP, FTP, SMTP, DNS | Daten | Gateway, Proxy, L4-7-Switch |
| 4 | Transport | TCP, UDP | Segmente, Datagramme | Gateway, Proxy, L4-7-Switch |
| 3 | Vermittlung (Netzwerk) | IP, IPsec, IPX | Pakete | Router, L3 Switch |
| 2 | Sicherung (Verbindung) | IEEE802.3, 802.11 | Frames | Bridge, L2 Switch |
| 1 | Physikalisch | IEEE802.3, 802.11 | Bits | Kabel, Repeater |

## VLAN
Definition: Ein VLAN (Virtual Local Area Network) ist ein logisch abgegrenztes Netzwerk, das unabh??ngig vom physischen Netzwerk und den darin enthaltenen Ger??ten existiert. Es wird verwendet, um Netzwerkressourcen und -dienste zu gruppieren, die Kommunikation zu segmentieren und die Sicherheit zu erh??hen.

### VLAN Konventionen

- VLAN 100: ACL "headless" Nutzung f??r z.B. Fax Ger??te
- VLAN 200: CLs QoS Nutzung f??r z.B. VoIP
- VLAN 300: ACL Nutzung f??r z.B. Desktops
- VLAN 400: ACL Nutzung f??r Guest

## LAN 
Definition: Ein LAN (Local Area Network) ist ein Netzwerk, das innerhalb eines Geb??udes oder einer Gruppe von Geb??uden betrieben wird. LANs sind in der Regel auf eine bestimmte Organisation beschr??nkt und werden von einem einzigen Administrator verwaltet. LANs k??nnen ??ber ein physisches Kabel oder drahtlos ??ber Funktechnologien wie WLAN oder Bluetooth verbunden sein.

### Angriffsvektoren LAN
- Schwachstellen: z.B. in Switches, Router, Access Points
- ARP Spoofing: Technik, bei der ein Angreifer eine falsche ARP-Nachricht an ein Netzwerk sendet, um sich zwischen zwei Netzwerkger??ten zu schalten, um Netzwerkverkehr zu manipulieren oder abzufangen.
- Loops: z.B. durch falsche Konfiguration von Switches
- Veraltete Protokolle: z.B. Telnet, FTP, SNMPv1
- Backdoors: z.B. in Firmware

### Absicherung LAN
- VLANs (Unterteilung in verschiedene Netzwerke)
- Hardening (z.B. Switches, Router, Access Points)
- NAC Erweiterung (z.B. f??r WLAN)
- Broadcast Storms vermeiden (z.B. durch Portfast)
- Segmentierung mit ACLs

## WLAN

### Angriffsvektoren WLAN
- Wardriving: Technik, bei der ein Angreifer ein WLAN-Netzwerk scannen kann, um die SSID und die MAC-Adresse des Access Points zu ermitteln.
- WEP: veraltete Verschl??sselungsmethode, die leicht gebrochen werden kann.
- Fake/Rogue Access Points: Angreifer erstellen ein eigenes WLAN-Netzwerk, um die Verbindung eines Benutzers zu stehlen. (Evil Twin)
- Sniffing: Angreifer k??nnen den Datenverkehr eines WLAN-Netzwerks abfangen, um Passw??rter, Benutzernamen und andere sensible Daten zu stehlen.

### Absicherung WLAN
- SSID Hiding: SSID verstecken
- WPA3: neueste Verschl??sselungsmethode
- Rogue AP Detection: Erkennung von Fake/Rogue Access Points
- Abschaltung von WPS und UPnP: WPS und UPnP sind nicht sicher und sollten daher deaktiviert werden.

## WAN
Definition: Ein WAN (Wide Area Network) ist ein Netzwerk, das ??ber eine gr????ere geografische Region verteilt ist. WANs k??nnen ??ber ein physisches Kabel oder drahtlos ??ber Funktechnologien wie WLAN oder Bluetooth verbunden sein.

### Angriffsvektoren WAN
- SMB: Angreifer k??nnen ein SMB-Netzwerk scannen, um die IP-Adresse des Servers zu ermitteln.
- DDoS: Angreifer k??nnen eine DDoS-Attacke durchf??hren, indem sie eine gro??e Anzahl von Ger??ten mit einem Botnetzwerk infizieren.
- Offene Ports: Angreifer k??nnen die Ports eines Servers scannen, um die Dienste zu ermitteln, die auf dem Server ausgef??hrt werden.

### Absicherung WAN
- Router Hardening: z.B. Firewall, IPS, IDS
- Zonierung (z.B. DMZ)
- Managementzugriff auf Router und Switches beschr??nken
- DDOS Schutz (z.B. durch Anbieter)

## Firewall
Definition: Eine Firewall ist ein Sicherheitsmechanismus, der zwischen zwei Netzwerken platziert wird, um die Kommunikation zwischen diesen beiden Netzwerken zu kontrollieren. Firewalls k??nnen auf verschiedenen Ebenen eingesetzt werden, um die Kommunikation zwischen zwei Netzwerken zu kontrollieren. Sie k??nnen auf der Anwendungsebene, der Transportebene, der Vermittlungsebene oder der Sicherungsebene eingesetzt werden.

### Angriffsvektoren Firewall
- Schwachstellen in Firmware
- Regelwerk ??berf??llt
- Keine Change History
- Keine Review oder Audit
- Logische Fehler

### Absicherung Firewall
- Auditierung des Regelwerks
- ??berpr??fen z.B. mit NMAP
- Automatisierte Tests
- Updates und Patches

## IDS/IPS

### Angriffsvektoren IDS/IPS
- ??berlastung durch zu viele Events
- Bypass Techniken (z.B. durch Paket-Fragmentierung)

### Absicherung IDS/IPS
- Aktuelle Signaturdatenbank
- Zyklische automatisierte ??berpr??fung
- Verschl??sselte Kommunikation ber??ck??sichtigen

## WEB/WAF

Eine Web Application Firewall (WAF) ist ein Sicherheitsmechanismus, der dazu dient, Web-Anwendungen vor Angriffen zu sch??tzen. Es filtert und blockiert b??sartige Anfragen, die versuchen, auf Ihre Anwendung zuzugreifen und sie zu sch??digen. (z.B. SQL-Injection, Cross-Site Scripting, etc.)

### ByPass Techniken
- VPN
- URL-Filter oft nicht ausreichend
- DNS ??ber HTTPS
- Portable Apps

### Angriffsvektoren WEB/WAF
(wie beui IDS/IPS)

### Absicherung WEB/WAF
- Whitelistings
- Zus??tzlich zu Scans auch manuelle Tests durchf??hren
- Vergabe an Diensleister sinnvoll

## VPN
VPN (Virtual Private Network) ist ein Netzwerk, das es Nutzern erm??glicht, ??ber ein ??ffentliches Netzwerk wie das Internet eine sichere und private Verbindung herzustellen. Es bietet eine verschl??sselte Verbindung und erm??glicht es Nutzern, auf entfernte Netzwerke und Ressourcen zuzugreifen, als ob sie an dem lokalen Netzwerk angeschlossen w??ren.

### Angriffsvektoren VPN
- Alte Parameter
- Nicht ausreichende Schl??ssell??nge
- Fehlkonfiguration

### Absicherung VPN
- Auditierung der Konfiguration
- Keine Verwendung von alten Protokollen
- Schl??sselverwaltung

## PKI
Definition: Public Key Infrastructure (PKI) ist ein System, das dazu dient, digitale Zertifikate auszustellen, zu verwalten und zu ??berpr??fen

### Angriffsvektoren PKI
- Unsichere Schl??sselverwaltung
- Unsichere Serverkonfiguration
- Technologische Fehler im Allgemeinen

### Absicherung PKI
- Auditierung 1x pro Jahr
  
## SSL Inspection

SSL Inspection(auch HTTPS Inspection) ist eine Technik, bei dem ein Netzwerkger??te (z.B. Firewall) den verschl??sselten Datenverkehr eines Netzwerks analysiert und nach potenziellen Bedrohungen sucht (z.B. Malware, Phishing, etc. ohne die Verschl??sselung zu unterbrechen).

### Problemstellung SSL Inspection
1. Leistungseinbu??en durch zus??tzliche Verarbeitung des Datenverkehrs
2. Sicherheitsrisiko: wenn nicht korrekt konfiguriert, kann der Datenverkehr von Angreifern verwendet werden und R??ckschl??sse auf die Kommunikation der Nutzer gezogen werden.
3. Datenschutz: wenn z.B. der Inhalt privater Nutzung (z.B. E-Mails) analysiert wird, kann dies zu einem Versto?? gegen die DSGVO f??hren

## Scanning

- Zur??ckgreifen auf Dienstleister
- Automatisierung der Scans
- Integration in z.B. SIEM

## Rechtliche Aspekte Scanning
- EU: Dual Use Regelung (09/21)
- ?? 202a StGB Aussp??hen von Daten (Hackerparagraph)
- Tatbest??nde der virtuellen Sachbesch??digung (???? 303a-303b StGB)
- Pentests sind zul??ssig, wenn sie im Rahmen eines Sicherheitskonzeptes durchgef??hrt werden

## SIEM

SIEM steht f??r Security Information and Event Management. SIEM ist ein System, das dazu dient, die Sicherheit eines Netzwerks zu ??berwachen und zu verwalten. Muss compliance-konform sein (z.B. ISO 27001, etc.)

```mermaid
graph LR
A[Zentraler Logserver] --> B[SIEM]
B --> C[SOC]
```
### Zentraler Logserver
- Log Sicherung (z.B. auf externem Server)
- Zugriff auf Logs ohne System Zugriff auf die tats??chlichen Systeme
- Audit Anforderungen erf??llen
- Archivierung der Logs

### SIEM
- 24/7 ??berwachung
- Alarmierung bei Bedrohungen
- Regelgesteuerte Reaktionen
- Notfallplanung
- Know-how von Mitarbeitern

### SOC (Security Operations Center) Managed Service
- Entlastung der IT
- Spezialisten auf dem Gebiet
- Prozesse und Methoden
- Technologisches Know-how

## Gesetze und Normen
| Institution | Bezeichnung | Link |
| --- | --- | --- |
| ![](https://www.mailtastic.com/hubfs/ISO-27001%5B3%5D.svg) | ISO 27001 | https://www.iso.org/standard/54543.html |
| ![](https://www.itskritis.de/_uploads/563275b34c90f/its-kritis-logo.png) | KRITIS | https://www.itskritis.de/ |
| ![](https://upload.wikimedia.org/wikipedia/de/thumb/6/6c/Bundesanstalt_f%C3%BCr_Finanzdienstleistungsaufsicht_201x_logo.svg/1280px-Bundesanstalt_f%C3%BCr_Finanzdienstleistungsaufsicht_201x_logo.svg.png) | BAFIN | https://www.bafin.de/ |
| | TISAX | https://www.tisax.de/ |
| | DSGVO | https://www.datenschutzkonferenz.de/ |
| | IT Grundschutz | https://www.it-grundschutz.de/ |
| | PCI DSS | https://www.pcisecuritystandards.org/ |
| |HIPAA | https://www.hhs.gov/hipaa/for-professionals/security/laws-regulations/index.html |

## Hardening 
Hardening ist die Prozess der Absicherung von Systemen und Netzwerken

### Switch Hardening
- Aktualisierung der Switch Firmware
- Deaktivierung von unsicheren Protokollen und Diensten (z.B. SNMP, Telnet, etc.)
- Zugriff personalisieren (z.B. nur bestimmte IP-Adressen)
- Monitoring, Protokollierung, Alarmierung und Datensicherung

## DDOS
DDOS steht f??r Distributed Denial of Service. DDOS ist ein Angriff, bei dem ein Netzwerk mit einer gro??en Anzahl von Anfragen ??berlastet wird, sodass es nicht mehr erreichbar ist.

### Absicherung DDOS
- Angemessene Bandbreite
- Obfuskieren der IP-Adressen und interner Netzwerkstruktur
- Verlagern der Last auf externe Dienste

## SDWAN
SDWAN steht f??r Software Defined Wide Area Network. SDWAN ist ein Netzwerk, das aus mehreren Netzwerken besteht, die ??ber eine zentrale Verwaltungseinheit verwaltet werden.

![Modernes SDWAN](media/modern-sdwan.png)

### Vorteile modernes SDWAN
- Hohe Flexibilit??t (z.B. Verbindung zu mehreren Cloud Providern)
- Erh??hte Sicherheit (z.B. durch ??berwachung und Verschl??sselung)
- Kostenreduzierung (z.B. dadurch, dass keine eigene Netzwerk-Hardware angeschafft werden muss)
- Erh??hte Geschwindigkeit (z.B. durch die Nutzung von mehreren Internetverbindungen und oder Multi-Cloud)

## Cloud Security

### Cloud Security Verantwortlichkeiten
| Daten/Dienst/Anwendung | Verantwortung |
| --- | --- |
| Kunden Daten | Kunde |
| Plattformen, Apps | Kunde |
| Konfiguration von OS, Netzwerk, etc. | Kunde |
| Verschl??sselung | Kunde |
| Compute, Storage, Netzwerk | Cloud Provider |
| Cloud Infrastruktur | Cloud Provider |

### Absicherung Cloud
- Multi-Faktor-Authentifizierung
- Conditional Access: Zugriff nur von bestimmten Ger??ten und Standorten
- Dokumentation der Cloud Umgebung: z.B. mit Azure Blueprints
- Alarmierung bei Bedrohungen

#### Conditional Access

- MFA
- Benutzer- und Rollenbasierte Zugriffssteuerung
- Endger??teverwaltung: z.B. nur bestimmte Ger??te (MAC-Adressen) erlauben
- Geografische Einschr??nkung: z.B. Zugriff nur von bestimmten Standorten erlauben

## OSINT
OSINT (Open Source Intelligence) ist eine Art der Ermittlung, die auf offenen, nicht-klassifizierten Informationen beruht, die ??ber das Internet und andere Quellen zug??nglich sind. OSINT kann verwendet werden, um ein breites Spektrum an Themen zu erforschen, wobei der Fokus haupts??chlich auf Cyber-Sicherheit und Terrorismus liegt.

### OSINT Schritte
1. Identifizierung der Zielgruppe
2. Erstellen des Angriffsplans
3. Angriff Ausf??hrung
4. Angriff Erkennung und Abwehr

## E-Mail Security

### Angriffsvektoren E-Mail
- Phishing
- Spear Phishing
- Hafnium: Angriff auf Microsoft Exchange Server

### Absicherung E-Mail
- Nutzung von E-Mail Security L??sungen
- Sandboxen

## IOT
IOT steht f??r Internet of Things. IOT ist ein Netzwerk, das aus vielen Ger??ten besteht, die ??ber das Internet miteinander verbunden sind.

- Viele Ger??te im Einsatz
- H??ufig unmanaged


## Operational Technology (OT)

Operational Technology (OT) ist die Technologie, die die mechanischen und physischen Komponenten innerhalb eines Unternehmens, eines Produktionsprozesses oder einer Infrastruktur steuert, ??berwacht und optimiert. Dazu geh??ren Maschinen, Ger??te, Sensoren, Instrumente und andere Ger??te, die dazu beitragen, ein Netzwerk oder System zu errichten und zu verwalten.

### Fr??her vs Heute
- Fr??her: abgekoppelte Systeme
- Fr??her: Glasfaser und Kupferleitungen
- Fr??her: Betrieb auf speziellen Ger??ten
- Heute: Cloud, IoT, SDWAN, etc.
- Heute: Drahtlose Verbindungen
- Heute: universelle Ger??te

### Absicherung OT
- Asset Management
- Segmentierung
- Isolation von alten Systemen
- SIEM
### OT vs IT

| Kriterium | IT | OT |
| --- | --- | --- |
| Verf??gbarkeit | mittel, Verz??gerungen tolerierbar | sehr hoch, Verz??gerungen nicht tolerierbar |
| Echzeit | nein | ja |
| Lebendauer Komponenten | kurz | lang |
| Updates/Patches | h??ufig | selten |
| Sicherheitspr??fung/Audit | geplant und beauftragt | gelegentlich |
| Sicherheitsbewusstsein | hoch | niedrig aber steigend |


## NAC
NAC steht f??r Network Access Control. NAC ist eine Technologie, die es erm??glicht, die Sicherheit von Netzwerken zu verbessern, indem die Ger??te, die auf das Netzwerk zugreifen, ??berpr??ft werden.

### Zero Trust Ansatz
- Keine Vertrauen in die Netzwerkumgebung
- Verifizierung vor jedem Zugriff
- MFA
- Kontinuierliche ??berwachung
- Schutz vor internen Bedrohungen: z.B. durch die Nutzung von SIEM
- Verschl??sselung
- Schutz gegen externe Bedrohungen: z.B. durch die Nutzung von E-Mail Security L??sungen