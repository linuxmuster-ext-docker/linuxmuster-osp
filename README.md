# linuxmuster-osp

OpenSchulportfolio Docker App für linuxmuster. 

TESTVERSION - **NICHT PRODUKTIV VERWENDEN**

## Verwendung

Entweder du hast schon einen Dockerhost mit docker, docker-compose, dehydrated und nginx oder du erzeugst dir einen, z.B. mit create-docker-host: https://github.com/linuxmuster-ext-docker/create-docker-host

### Dienstenamen und Zertifikat

Zuerst musst du dir Dienstenamen ausdenken und SSL-Zertifikat besorgen. Also z.B. portfolio.meine-schule.tld

* Lege einen DNS Eintrag für deine Dockerapp, z.B. portfolio.meine-schule.tld, der auf die IP des Dockerhosts zeigt. Das darf auch ein CNAME sein.
* Trage diesen Host in die Datei ``/etc/dehydrated/domains.txt`` ein.
* Führe den Befehl ``dehydrated -c`` aus. Jetzt hast du die Zertifikate im Verzeichnis /var/lib/dehydrated/certs/<hostname>/ zur Verfügung, der Docker Host aktualisiert diese per Cronjpb.

### App herunterladen, konfigurieren und starten

* Klone dieses Repo auf deinen Dockerhost nach ``/srv/docker``
  * ``cd /srv/docker``
  * ``git clone https://github.com/linuxmuster-ext-docker/linuxmuster-osp``
* Wechsle in das App-Verzeichnis: ``cd linuxmuster-osp``
* Passe die Werte in der Datei ``osp.ini`` an.
* Erzeuge eine Konfiguration mit: ``./setup``
* Starte die App mit dem Befehl ``docker-compose up -d``

Jetzt solltest du dich an deinem Schulportfolio unter der Adresse https://osp.meine-schule.tld/ anmelden können, so wie du deinen Service-Host und deine Service-Domain gewählt und konfiguriert hast.
