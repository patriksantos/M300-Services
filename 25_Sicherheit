**M300 - 25_Sicherheit**
==========================

### Firewall

Eine Firewall ist ein Sicherungssystem, welches ein Rechnernetz oder einen einzelnen Computer vor unerwünschten Netzwerkzugriffen schützt und weiter gefasst auch ein Teilaspekt eines Sicherheitskonzepts ist.

    netstat -tulpen
Ausgabe der offenen Ports


    sudo apt-get install ufw
Installation


    sudo ufw status
    sudo ufw enable
    sudo ufw disable***
Start/Stop


    # Port 80 (HTTP) öffnen für alle
    vagrant ssh web
    sudo ufw allow 80/tcp
    exit

    # Port 22 (SSH) nur für den Host (wo die VM laufen) öffnen
    vagrant ssh web
    w
    sudo ufw allow from [Meine-IP] to any port 22
    exit

    # Port 3306 (MySQL) nur für den web Server öffnen
    vagrant ssh database
    sudo ufw allow from [IP der Web-VM] to any port 3306
    exit

Firewall Regeln


    sudo ufw status numbered
    sudo ufw delete 1

Löschen von Regeln


### Reverse-Proxy

    sudo apt-get install libapache2-mod-proxy-html
    sudo apt-get install libxml2-dev

Installation von benötigten modulen.


    sudo a2enmod proxy
    sudo a2enmod proxy_html
    sudo a2enmod proxy_http 

Module für Apache die aktiviert wereden müssen


    sudo service apache2 restart

Apache-Server Neustarten


    # Allgemeine Proxy Einstellungen
    ProxyRequests Off
    <Proxy *>
        Order deny,allow
        Allow from all
    </Proxy>

    # Weiterleitungen master
    ProxyPass /master http://master
    ProxyPassReverse /master http://master

Konfiguration vom Reverse Proxy

