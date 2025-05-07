# Indice

- [Information Gathering](#information-gathering)
- [Categorie principali](#categorie-principali)
  - [Reconnaissance passiva](#1-reconnaissance-passiva)
  - [Reconnaissance attiva](#2-reconnaissance-attiva)
- [Approfondimento](#reconnaissance-passiva-approfondimento)
  - [Ricerca web](#1-ricerca-web)
  - [Analisi dei registri di dominio](#2-analisi-dei-registri-di-dominio)
  - [Mappatura geografica](#3-mappatura-geografica)
  - [Database pubblici](#4-database-pubblici)

## Strumenti per la Reconnaissance Passiva

- [DNSDumpster.com](#dnsdumpstercom)
- [VirusTotal.com](#virustotalcom)
- [SecurityHeaders.com](#securityheaderscom)
- [NetCraft.com](#netcraftcom)
- [HOST (Comando Bash)](#host-comando-bash)
- [ROBOTS.TXT](#robotstxt)
- [SITEMAP.XML](#sitemapxml)
- [WHATWEB (Utility Linux)](#whatweb-utility-linux)
- [WHOIS (Utility Linux)](#whois-utility-linux)
- [DNSRecon](#dnsrecon)
- [Wafw00f (Utility Linux)](#wafw00f-utility-linux)
- [Sublist3r (Utility Linux)](#sublist3r-utility-linux)
- [Google Dorks](#google-dorks)
- [TheHarvester (Utility Linux)](#theharvester-utility-linux)
- [Leaked Password Databases](#leaked-password-databases)
- [DNS Zone Transfer](#dns-zone-transfer)
- [dnsrecon (Utility Linux)](#dnsrecon-utility-linux)
- [dig (Utility Linux)](#dig-utility-linux)
- [Hosts File](#hosts-file)

## Reconnaissance Attiva

- [Host Discovery con Nmap](#host-discovery-con-nmap)
- [Netdiscover (Utility Linux)](#netdiscover-utility-linux)
- [Port Scanning With Nmap](#port-scanning-with-nmap)
- [Strumenti per la Reconnaissance Attiva](#strumenti-per-la-reconnaissance-attiva)
- [Importare risultati di nmap su msfconsole](#importare-risultati-di-nmap-su-msfconsole)

# Information Gathering

L'information gathering rappresenta la prima fase fondamentale del processo di penetration testing e cybersecurity. Consiste nella raccolta sistematica di informazioni su un target (azienda o sistema) per identificare vulnerabilità e potenziali punti di accesso.

## Categorie principali

### 1. Reconnaissance passiva

Raccolta di informazioni senza interazione diretta con i sistemi target:

- Analisi di fonti pubblicamente disponibili (siti web, social media, registri domini)
- Scansione di rete per identificare servizi e sistemi attivi
- Estrazione di metadati da file e documenti

### 2. Reconnaissance attiva

Raccolta di informazioni attraverso interazione diretta con i sistemi target:

- Scansione di porte e servizi per identificare sistemi vulnerabili
- Enumerazione di utenti, gruppi e condivisioni di rete
- Analisi di errori e informazioni esposte dai sistemi

Per la certificazione eCPPT (eJPT), l'information gathering è un'area di valutazione critica. Dovrai dimostrare la tua capacità di raccogliere informazioni in modo efficace e legale, rispettando sempre normative e considerazioni etiche.

## Reconnaissance Passiva: Approfondimento

La reconnaissance passiva ti permette di costruire un profilo completo del target senza generare traffico sospetto o lasciare tracce. Ecco le tecniche principali:

### 1. Ricerca web

- **Analisi del sito web**: Comprendi struttura aziendale, servizi offerti e organizzazione interna
- **Social media**: Raccogli dettagli su dipendenti, attività aziendali e presenza online
- **Notizie e articoli**: Identifica storia aziendale, reputazione ed eventi significativi

### 2. Analisi dei registri di dominio

- **Informazioni di registrazione**: Identifica registrante, server DNS, date di registrazione/scadenza
- **Sottodomini**: Scopri indirizzi IP associati e relazioni tra domini

### 3. Mappatura geografica

- **Posizione fisica**: Utilizza servizi come Google Maps per localizzare sedi e uffici
- **Infrastrutture**: Identifica misure di sicurezza fisica (telecamere, recinzioni)

### 4. Database pubblici

- **Dati aziendali**: Consulta registri di brevetti, marchi e licenze
- **Informazioni sui dipendenti**: Cerca organigrammi e strutture organizzative

## Strumenti per la Reconnaissance Passiva

### DNSDumpster.com

DNSDumpster è uno strumento online utilizzato per la raccolta di informazioni relative ai domini e ai loro record DNS. Basta visitare il sito:

`https://dnsdumpster.com/`

### VirusTotal.com

VirusTotal può essere utilizzato anche come strumento per il passive DNS scanning. Questo approccio consente di raccogliere informazioni sui record DNS associati a un dominio senza effettuare query DNS attive.

`https://www.virustotal.com/gui/home/url`

### SecurityHeaders.com

SecurityHeaders.com è uno strumento online che consente di analizzare le intestazioni di sicurezza di un sito web. Quando inserisci l'URL di un sito, il servizio esamina le intestazioni HTTP inviate dal server e fornisce un report dettagliato su quali misure di sicurezza sono implementate.

`https://securityheaders.com/`

### NetCraft.com

Netcraft è un servizio che fornisce informazioni e statistiche su siti web e server. Il sito offre report dettagliati su vari aspetti di un sito web, come la tecnologia utilizzata, il sistema operativo del server, il provider di hosting, e altre informazioni utili per analizzare la presenza online di un sito. È spesso utilizzato da sviluppatori, professionisti del web e ricercatori per ottenere dati su come i siti sono costruiti e gestiti.

`https://sitereport.netcraft.com/`

### HOST (Comando Bash)

Strumento per eseguire ricerche DNS e ottenere informazioni su domini o indirizzi IP.

Funzionalità principali:

1. **Risoluzione di nomi di dominio**

   ```bash
   #/bin/bash

   host www.example.com
   ```

2. **Ricerca di record DNS**

   ```bash
   #/bin/bash

   host -t MX www.example.com
   ```

3. **Ricerca di informazioni su indirizzi IP**

   ```bash
   #/bin/bash

   host 8.8.8.8
   ```

### ROBOTS.TXT

File di testo che fornisce istruzioni ai crawler dei motori di ricerca su quali pagine o directory possono essere esplorate.

Esempio:

```text
User-agent: *
Disallow: /secret/
Disallow: /backup/
```

Dal punto di vista del penetration testing, questo file può rivelare informazioni preziose sulla struttura del sito e potenziali aree sensibili.

### SITEMAP.XML

File XML che elenca tutte le pagine di un sito web, utile per i motori di ricerca e per gli esperti di sicurezza.

Esempio:

```html
<?xml version="1.0" encoding="UTF-8"?>

<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://www.example.com/foo.html</loc>
    <lastmod>2022-06-04</lastmod>
  </url>
</urlset>
```

Per i penetration tester, fornisce una panoramica completa della struttura del sito, facilitando l'identificazione di aree potenzialmente vulnerabili.

### WHATWEB (Utility Linux)

Strumento di analisi che identifica le tecnologie utilizzate da un sito web.

Esempio:

```bash
#/bin/bash

whatweb https://www.example.com
```

Output:

```text
example.com [200 OK] Apache[2.4.41],
Country[RESERVED][ZZ],
HTML5, HTTPServer[Apache/2.4.41 (Ubuntu)],
IP[93.184.216.34],
JQuery, Script, Title[Example Domain]
```

### WHOIS (Utility Linux)

Strumento per ottenere informazioni sui registranti di domini e indirizzi IP.

Esempio:

```bash
#/bin/bash

whois example.com
```

Output:

```text
Domain Name: EXAMPLE.COM
Registry Domain ID: 1234567890_DOMAIN_COM-VRSN
Registrar WHOIS Server: whois.example-registrar.com
Registrar URL: http://www.example-registrar.com
Updated Date: 2023-01-01T00:00:00Z
Creation Date: 2000-01-01T00:00:00Z
Registrar Registration Expiration Date: 2024-01-01T00:00:00Z
Registrar: Example Registrar, Inc.
Registrar IANA ID: 123
Registrant Name: John Doe
Registrant Organization: Example Corp
Registrant Street: 123 Example St
Registrant City: Example City
Registrant State/Province: EX
Registrant Postal Code: 12345
Registrant Country: US
Registrant Phone: +1.5555555555
Registrant Email: johndoe@example.com
```

Nota: Molti domini utilizzano servizi di privacy per nascondere queste informazioni dalle query WHOIS pubbliche.

### DNSRecon

Strumento avanzato per la ricerca di informazioni DNS.

Esempio:

```bash
#/bin/bash

dnsrecon -d example.com
```

Output:

```text
[+] A Records
    - 192.0.2.1
    - 192.0.2.2

[+] MX Records
    - mail.example.com. (10)

[+] NS Records
    - ns1.example.com.
    - ns2.example.com.

[+] TXT Records
    - "v=spf1 include:_spf.google.com ~all"

[+] CNAME Records
    - www.example.com. -> example.com.
```

### Wafw00f (Utility Linux)

Strumento specializzato per identificare Web Application Firewalls (WAF).

Esempio:

```bash
#/bin/bash

wafw00f http://example.com
```

Output:

```text
Checking http://example.com for WAF...
WAF detected: Cloudflare
WAF version: 2023
Detection method: HTTP header analysis
```

### Sublist3r (Utility Linux)

Strumento per identificare sottodomini di un dominio principale.

Esempio:

```bash
#/bin/bash

sublist3r -d example.com
```

Output:

```text
    ___ _           _    _       _
   / __| |_  __ _ _| |__| |__ _| |_ ___
   \__ \ ' \/ _` | '_ \ / _` |  _/ -_)
   |___/_||_\__,_|_.__/_\__,_|\__\___|

    Sublist3r - v1.0.4

[+] Enumerating subdomains for example.com
[+] Found subdomain: www.example.com
[+] Found subdomain: mail.example.com
[+] Found subdomain: blog.example.com
[+] Found subdomain: api.example.com
[+] Found subdomain: dev.example.com
[+] Found subdomain: test.example.com

[+] Total subdomains found: 6
```

È possibile specificare i motori di ricerca con `-e`:

```bash
sublist3r -d example.com -e google,yahoo
```

Per ulteriori opzioni: `sublist3r --help` o visita il repository ufficiale: `https://github.com/aboul3la/Sublist3r`

### Google Dorks

Tecniche di ricerca avanzata su Google per scoprire informazioni sensibili.

| **Operatore**   | **Descrizione**                                                                                  |
| --------------- | ------------------------------------------------------------------------------------------------ |
| `site:`         | Cerca solo all'interno di un dominio specifico. Esempio: `site:example.com`                      |
| `filetype:`     | Cerca file di un tipo specifico. Esempio: `filetype:pdf`                                         |
| `inurl:`        | Cerca parole specifiche nell'URL. Esempio: `inurl:login`                                         |
| `intitle:`      | Cerca parole specifiche nel titolo della pagina. Esempio: `intitle:"admin"`                      |
| `allintext:`    | Cerca tutte le parole specificate nel testo della pagina. Esempio: `allintext:ricerca sicurezza` |
| `intext:`       | Cerca una parola specifica nel testo della pagina. Esempio: `intext:"password"`                  |
| `cache:`        | Mostra la versione memorizzata nella cache di una pagina. Esempio: `cache:example.com`           |
| `link:`         | Trova pagine che collegano a un URL specifico. Esempio: `link:example.com`                       |
| `related:`      | Trova siti web simili a un URL specifico. Esempio: `related:example.com`                         |
| `define:`       | Fornisce definizioni di una parola o frase. Esempio: `define:tecnologia`                         |
| `info:`         | Mostra informazioni su un URL specifico. Esempio: `info:example.com`                             |
| `OR`            | Cerca risultati che contengono uno dei termini specificati. Esempio: `apple OR orange`           |
| `-` (meno)      | Esclude una parola dai risultati. Esempio: `apple -fruit`                                        |
| `*` (asterisco) | Funziona come un jolly per sostituire una o più parole. Esempio: `best * 2023`                   |

Per una lista completa di tecniche avanzate: `https://www.exploit-db.com/google-hacking-database`

### TheHarvester (Utility Linux)

Strumento per raccogliere email, nomi utente, sottodomini e altre informazioni.

Esempio:

```bash
#/bin/bash

python theHarvester.py -d example.com -b google
```

Output:

```text
[*] Querying Google for example.com
[*] Found 5 emails:
    - info@example.com
    - support@example.com
    - admin@example.com
    - contact@example.com
    - sales@example.com

[*] Found 10 subdomains:
    - mail.example.com
    - www.example.com
    - blog.example.com
    - shop.example.com
    - api.example.com
    - dev.example.com
    - test.example.com
    - secure.example.com
    - support.example.com
    - forum.example.com

[*] Found 3 hosts:
    - 192.0.2.1
    - 192.0.2.2
    - 192.0.2.3
```

### Leaked Password Databases

Database di credenziali compromesse utilizzabili per verificare se informazioni sensibili sono state esposte.

Il servizio "Have I Been Pwned" (`https://haveibeenpwned.com/`) permette di verificare se un indirizzo email è stato coinvolto in violazioni di dati note.

### DNS Zone Transfer

Processo utilizzato per copiare dati di una zona DNS da un server primario a server secondari.

Tipi principali:

- **AXFR (Full Zone Transfer)**: Copia l'intera zona DNS
- **IXFR (Incremental Zone Transfer)**: Copia solo le modifiche recenti

Questo processo, se non adeguatamente protetto, può esporre informazioni sensibili sulla configurazione DNS di un dominio.

### dnsrecon (Utility Linux)

Strumento avanzato per la ricognizione DNS.

Esempio:

```bash
#/bin/bash

dnsrecon -d example.com
```

Output:

```text
DNS Recon v1.9.0

[+] Domain: example.com
[+] Type: A
[+] IP: 93.184.216.34

[+] Type: NS
[+] Nameserver: ns1.example.com
[+] Nameserver: ns2.example.com

[+] Type: MX
[+] Mail Exchange: mail.example.com
[+] Priority: 10

[+] Type: TXT
[+] TXT Record: "v=spf1 include:_spf.example.com ~all"

[+] Subdomains found:
    - www.example.com
    - api.example.com
    - blog.example.com

[+] Zone Transfer (AXFR) results:
    - Transfer failed: Not allowed

[+] Reverse DNS Lookup:
    - 93.184.216.34 -> example.com

[+] DNSSEC:
    - DNSSEC: No

[+] Additional Information:
    - SOA Record:
        - Primary NS: ns1.example.com
        - Email: hostmaster.example.com
        - Serial: 2023010101
        - Refresh: 7200
        - Retry: 3600
        - Expire: 1209600
        - Minimum TTL: 3600
```

### dig (Utility Linux)

Strumento potente per interrogare i server DNS.

Esempio:

```bash
#!/bin/bash

dig axfr @example.com 8.8.8.8
```

Output:

```
; <<>> DiG 9.10.6 <<>> example.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12345
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;example.com. IN A

;; ANSWER SECTION:
example.com. 3600 IN A 93.184.216.34

;; AUTHORITY SECTION:
example.com. 3600 IN NS ns1.example.com.

;; ADDITIONAL SECTION:
ns1.example.com. 3600 IN A 93.184.216.34

;; Query time: 50 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Mon Oct 02 12:00:00 UTC 2023
;; MSG SIZE rcvd: 100
```

### Hosts File

File di sistema che mappa nomi di dominio a indirizzi IP, potenzialmente sfruttabile per attacchi di phishing.

Esempio:

```
#/etc/hosts

127.0.0.1       localhost
192.168.1.10    server-locale
203.0.113.5     esempio.com
203.0.113.5     www.esempio.com
```

## Host Discovery con Nmap

Nmap (Network Mapper) è uno strumento essenziale per la scansione e l'analisi delle reti, fondamentale per l'ethical hacking.

Esempio di scansione di rete:

```bash
#!/bin/bash

nmap -sn 192.168.1.0/24
```

Output:

```
Starting Nmap 7.80 ( https://nmap.org ) at 2023-10-01 12:00 UTC
Nmap scan report for 192.168.1.1
Host is up (0.0010s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE
22/tcp open  ssh

Nmap scan report for 192.168.1.2
Host is up (0.0010s latency).
Not shown: 998 closed ports
PORT   STATE SERVICE
80/tcp open  http

Nmap scan report for 192.168.1.3
Host is up (0.0010s latency).
All 1000 scanned ports on 192.168.1.3 are closed
```

Per risparmiare tempo è possibile utilizzare un approccio tramite TCP SYN scan su porte specifiche:

```bash
#!/bin/bash

nmap -sn -PS21,22,25,80,445,3389,8080 -PU137,138 192.168.1.0/24
```

### Netdiscover (Utility Linux)

Strumento per la scoperta di host in rete locale tramite pacchetti ARP.

Esempio:

```bash
#!/bin/bash

netdiscover -i eth0 -r 192.168.1.0/24
```

Output:

```
Currently scanning: 192.168.1.0/24   |   Screen View: Unique Hosts
4 Captured ARP Req/Rep packets, from 4 hosts.   Total size: 240
________________________________________________________________________
   IP            At MAC Address     Count     Len  MAC Vendor / Hostname
---------------------------------------------------------------------------
192.168.1.1     00:1A:2B:3C:4D:5E      1      60  Cisco Systems, Inc
192.168.1.10    00:1A:2B:3C:4D:5F      1      60  Apple, Inc
192.168.1.20    00:1A:2B:3C:4D:60      1      60  Samsung Electronics
192.168.1.30    00:1A:2B:3C:4D:61      1      60  Hewlett Packard
```

## Port Scanning With Nmap

Esempio di scansione porte su un host specifico:

```bash
#!/bin/bash

nmap 192.168.8.1
```

Output:

```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-04-05 17:11 CEST
Nmap scan report for 192.168.8.1
Host is up (0.00077s latency).
Not shown: 994 closed tcp ports (reset)
PORT    STATE SERVICE
22/tcp  open  ssh
80/tcp  open  http

Nmap done: 1 IP address (1 host up) scanned in 38.74 seconds
```

Per accelerare la scansione, aggiungi `-Pn`:

```bash
#!/bin/bash

nmap -Pn 192.168.8.1
```

Per scansionare tutte le 65535 porte:

```bash
#!/bin/bash

nmap -Pn -p- 192.168.8.1
```

Comando avanzato con analisi dettagliata:

```bash
#!/bin/bash

nmap -Pn -p- -sCV --open 192.168.8.1 -vvv
```

Spiegazione dei parametri:

- `-Pn`: Salta la fase di ping e assume che l'host sia attivo
- `-p-`: Scansiona tutte le porte (1-65535)
- `-sCV`: Combina `-sC` (script di default) e `-sV` (rilevamento versioni)
- `--open`: Mostra solo le porte aperte
- `-vvv`: Massimo livello di dettaglio nell'output

Per scoprire tutte le opzioni disponibili, usa `nmap --help`.

## Strumenti per la Reconnaissance Attiva

La "reconnaissance attiva" in cybersecurity è una fase del processo di raccolta di informazioni su un obiettivo, che può essere un sistema, una rete o un'organizzazione. A differenza della ricognizione passiva, che si basa su informazioni già disponibili pubblicamente (come siti web, social media, ecc.), la ricognizione attiva implica l'interazione diretta con il target per raccogliere dati.

Qui di seguito mostro lo schema che seguiremo in fase di penetration testing:

| **1.Information Gathering**                                                                                                                            | **2.Enumeration**                                                                                               | **3.Exploitation (Initial Access)**                                                                                     | **4.Post Exploitation**                                                                                                                                                      | **5.Reporting**                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| <u>**Passive Information Gathering**</u><br>[+] OSINT                                                                                                  | <u>**Service & OS Enumeration**</u><br>[+] Service Enumeration<br>[+] User Enumeration<br>[+] Share Enumeration | <u>**Vulnerability Analisys and Threat Modeling**</u><br>[+] Vulnerability Analysis<br>[+] Vulnerability Identification | <u>**Post Exploitation**</u><br>[+] Local Enumeration<br>[+] Privilege Escalation<br>[+] Credential Access<br>[+] Persistence<br>[+] Defense Evasion<br>[+] Lateral Movement | <u>**Reporting**</u><br>[+] Report Writing<br>[+] Recommendations |
| <u>**Active Information Gathering**</u><br>[+] Network Mapping<br>[+] Host Discovery<br>[+] Port Scanning<br>[+] Service Detection<br>[+] OS Detection |                                                                                                                 | <u>**Exploitation**</u><br>[+] Developing/Modifying<br>[+] Exploits<br>[+] Service Exploitation                         |                                                                                                                                                                              |                                                                   |

### Importare risultati di nmap su msfconsole

Cominciamo col dire che i risultati di nmap possono essere esportati tramite il flag `-oX <nome-file>` in formato XML
dopodichè avviato il servizio di postgresql è possibile importare il file appena creato in un nuovo workspace in metasploit framework. Facciamo un esempio

```bash
#!/bin/bash

nmap -Pn -sT -oX nmap.xml 192.168.8.1
service postgresql start
msfconsole
```

```
.......7..77777,. .
.....777.,7777777:.        8O.    .OO88O.   ?OO.    .OO. 8OO8888 ~OO88OO8 . .
 . ,777,.?777777777.      ZO8O ....O, . O:  ?8OO...,O8O. 8O      ~O      OO.
...7777..7777..7777=     .O=.O7   .O,  .8.  ?8.8O.88.:O. 8O      ~O      .OO
 .?7777..7777..77777     OO  :O   .O8OOO.   ?8. ,OO. :O. 8OOOOOO ~O       $O
..7777+.?7777..77777    OOOOOOOO ..O,  88.. ?8.. .  .:O. 8O      ~O       OO.
 .?777..77777..77777   ,O,     O8 .O,.. OO  ?8.  .  .:O. 8O      ~O    ..8O.
 ..777..........I77,   8Z       O~.O,    OO ?8.      :O. 8OOOOOO ~OOOOO88
 ...777777777..777I.
 .  .77777777..77.
 ...  .~77777...


       =[ metasploit v4.10.1-dev [core:4.10.1.pre.dev api:1.0.0]]
+ -- --=[ 1372 exploits - 766 auxiliary - 221 post        ]
+ -- --=[ 340 payloads - 37 encoders - 8 nops             ]
+ -- --=[ Free Metasploit Pro trial: http://r-7.co/trymsp ]

msf > workspace -a nmap_session
msf > db_import nmap.xml
```

D'ora in poi possiamo utilizzare db_nmap per salvare i risultati automaticamente nel database di postgres.

Ora abbiamo i seguenti comandi che possiamo dare per leggere il database:

- `hosts` rivela tutti gli host trovati con nmap
- `services` rivela tutti i servizi trovati con nmap
- `vulns` rivela tutte le vulnerabilità trovate con nmap

## Generatore di dizionari personalizzati

`cupp` (Common User Passwords Profiler) è uno strumento utilizzato per generare dizionari di password personalizzati, utile in contesti di test di penetrazione e sicurezza informatica. Il comando cupp -i serve per avviare l'interfaccia interattiva di cupp, che ti guida nella creazione di un dizionario di password basato su informazioni specifiche che fornisci.
