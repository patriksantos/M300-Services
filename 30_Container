**M300 - 30_Container**
==========================

### Container

Entwickler können Software lokal bauen, die woanders genauso laufen wird – sei es ein Rack in der IT-Abteilung, der Laptop eines Anwenders oder ein Cluster in der Cloud.

Merkmale

- Container teilen sich Ressourcen mit dem Host-Betriebssystem
- Container können im Bruchteil einer Sekunde gestartet und gestoppt werden
- Anwendungen, die in Containern laufen, verursachen wenig bis gar keinen Overhead
- Container sind portierbar --> Fertig mit "Aber bei mir auf dem Rechner lief es doch!"
- Container sind leichtgewichtig, d.h. es können dutzende parallel betrieben werden.
- Container sind "Cloud-ready"!


### Docker

Docker nahm die bestehende Linux-Containertechnologie auf und verpackte und erweiterte sie in vielerlei Hinsicht – vor allem durch portable Images und eine benutzerfreundliche Schnittstelle –, um eine vollständige Lösung für das Erstellen und Verteilen von Containern zu schaffen.

Docker wird zuvor in der Vagrant File installiert und danach mit einer eigenen Docker File konfiguriert.


    docker run hello-world

Standard Test am Anfang ob es funktioniert.


    docker run -it ubuntu /bin/bash

Startet einen Container mit einer interaktiven Shell


    docker run -d ubuntu sleep 20

Startet einen Container, der im Hintergrund läuft


    docker run -d --rm ubuntu sleep 20

Startet einen Container im Hintergrund und löscht diesen nach Beendigung des Jobs


***Status abfragen:***

    docker ps

Aktive Container anzeigen.


    docker ps -a -q

Nur IDs ausgeben (-a = all // -q = quit)


***Images:***

    docker images

Lokale Images ausgeben (alternativ mit ls am Schluss)


***Löschen:***

    docker rm [name]

Entfernt einen oder mehrere Container. Gibt die Namen oder IDs erfolgreich gelöschter Container zurück.
(statt mit Namen (-f auch aktive) `docker ps -a -q` alle)


    docker rmi ubuntu

Docker Image löschen.


***Starten/Stoppen/Killen***

    docker start [id]

Docker Container neu starten, die Daten bleiben erhalten.

Alternativ mit docker stop (stoppen) ODER mit docker kill sofort stoppen.


***Dockerfile***

    docker build -t mysql .

das Image kann so gebuildet werden


    docker run --rm -d --name mysql mysql

Container starten.


    docker exec -it mysql bash

Funktionsfähigkeit überprüfen.


    ps -ef
    netstat -tulpen

Überprüfung im Container.


### Konzepte

***FROM***
Welches Base Image von hub.docker.com verwendet werden soll, z.B. ubuntu:16.04

***ADD***
Kopiert Dateien aus dem Build Context oder von URLs in das Image.

***CMD***
Führt die angegebene Anweisung aus, wenn der Container gestartet wurde. Ist auch ein ENTRYPOINT definiert, wird die Anweisung als Argument für ENTRYPOINT verwendet.

***COPY***
Wird verwendet, um Dateien aus dem Build Context in das Image zu kopieren. Es gibt die zwei Formen COPY src dest und COPY ["src", "dest"]. Das JSON-Array-Format ist notwendig, wenn die Pfade Leerzeichen enthalten.

***ENTRYPOINT***
Legt eine ausführbare Datei (und Standardargumente) fest, die beim Start des Containers laufen soll.
Jegliche CMD-Anweisungen oder an docker run nach dem Imagenamen übergebenen Argumente werden als Parameter an das Executable durchgereicht.
ENTRYPOINT-Anweisungen werden häufig genutzt, um "Start-Scripts" anzustossen, die Variablen und Services initialisieren, bevor andere übergebene Argumente ausgewertet werden.

***ENV***
Setzt Umgebungsvariablen im Image.

***EXPOSE***
Erklärt Docker, dass der Container einen Prozess enthält, der an dem oder den angegebenen Port(s) lauscht.

***HEALTHCHECK***
Die Docker Engine prüft regelmässig den Status der Anwendung im Container.
    HEALTHCHECK --interval=5m --timeout=3s \ CMD curl -f http://localhost/ || exit 1`

***MAINTAINER***
Setzt die "Autor-Metadaten" des Image auf den angegebenen Wert.

***RUN***
Führt die angegebene Anweisung im Container aus und bestätigt das Ergebnis.

***SHELL***
Die Anweisung SHELL erlaubt es seit Docker 1.12, die Shell für den folgenden RUN-Befehl zu setzten. So ist es möglich, dass nun auch direkt bash, zsh oder Powershell-Befehle in einem Dockerfile genutzt werden können.

***USER***
Setzt den Benutzer (über Name oder UID), der in folgenden RUN-, CMD- oder ENTRYPOINT-Anweisungen genutzt werden soll.

***VOLUME***
Deklariert die angegebene Datei oder das Verzeichnis als Volume. Besteht die Datei oder das Verzeichnis schon im Image, wird sie bzw. es in das Volume kopiert, wenn der Container gestartet wird.

***WORKDIR***
Setzt das Arbeitsverzeichnis für alle folgenden RUN-, CMD-, ENTRYPOINT-, ADD oder COPY-Anweisungen.


### Netzwerk Verbindung

    docker run --rm -d -p 3306:3306 mysql

MySQL Container permanent an Host Port 3306 weiterleiten.


    docker run --rm -d -P mysql

MySQL Container mit nächsten freien Port verbinden


    sudo apt-get install mysql-client

Installation des MySQL Clients auf dem Host.


    RUN sed -i -e"s/^bind-address\s*=\s*127.0.0.1/bind-address = 0.0.0.0/" /etc/mysql/my.cnf

Freigabe des Ports in der MySQL-Config im Container, z.B. via Dockerfile.


    CREATE USER 'root'@'%' IDENTIFIED BY 'admin';
    GRANT ALL PRIVILEGES ON *.* TO 'root'@'%';
    FLUSH PRIVILEGES;

SQL Freigabe, via MySQL Client im Container einrichten.


    mysql -u root -p admin -h 127.0.0.1

Sind alle Arbeiten durchgeführt, sollte mit folgenden Befehl vom Host auf den MySQL Server, im Docker Container, zugegriffen werden können.


