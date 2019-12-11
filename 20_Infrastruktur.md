**M300 - 20_Infrastruktur**
==========================

### Vagrant

Vagrant ist eine Ruby-Anwendung (open-source) zum Erstellen und Verwalten von virtuellen Maschinen (VMs).

Die Ruby-Anwendung dient als Wrapper (engl. Verpackung, Umschlag) zwischen Virtualisierungssoftware wie VirtualBox, VMware und Hyper-V und Software-Konfiguration-Management-Anwendungen bzw. Systemkonfigurationswerkzeugen wie Chef, Saltstack und Puppet.

Wichtig: Die Virtuellen Maschinen entsprechen lauffähigen Servern.


    vagrant init
Initialisiert im aktuellen Verzeichnis eine Vagrant-Umgebung und erstellt, falls nicht vorhanden, ein Vagrantfile


    vagrant up
Erzeugt und Konfiguriert eine neue Virtuelle Maschine, basierend auf dem Vagrantfile


    vagrant ssh
Baut eine SSH-Verbindung zur gewünschten VM auf


    vagrant status
Zeigt den aktuellen Status der VM an


    vagrant port
Zeigt die Weitergeleiteten Ports der VM an


    vagrant halt
Stoppt die laufende Virtuelle Maschine


    vagrant destroy
Stoppt die Virtuelle Maschine und zerstört sie. Am Schluss noch -f (forced) fürs direkte stoppen.


weitere Befehle während dem arbeiten mit Vagrant:

    vagrant box add [box-name]
Hinzufügen einer Box zur lokalen Registry


    vagrant box list
In der lokalen Registry vorhandene Boxen anzeigen


*Synchronisierter Ordner:*

Synchronisierte Ordner ermöglichen es der VM auf Verzeichnisse des Host-Systems zuzugreifen.

    Vagrant.configure(2) do |config|
        config.vm.synced_folder ".", "/var/www/html"  
    end

