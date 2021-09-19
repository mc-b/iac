Übung 3: Cloud-init Hands-on
----------------------------

Cloud-init übernimmt die Initialisierung einer Cloud-Instanz. Es wird von allen grossen öffentlichen Cloud Anbietern, Bereitstellungssystemen für private Cloud
Infrastrukturen und Bare Metal Installationen unterstützt.

Mit Cloud-init lassen u.a. folgende Einstellungen vornehmen:
* Festlegen eines Standardgebietsschemas
* Hostname einstellen
* ssh-private Schlüssel generieren
* ssh-Schlüssel zu den .ssh/authorized_keys des Benutzers hinzufügen, damit er sich anmelden kann

Das Verhalten von cloud-init kann über, das Feld `User data` (oder `Custom data`) konfiguriert werden. `User data` wird vom Benutzer zum Startzeitpunkt an cloud-init an den Cloud-Anbieter übergeben, normalerweise als Parameter in der CLI, Vorlage oder im Cloud-Portal, die zum Starten einer Instanz verwendet werden.

Beginnt das Feld `User data` mit `#cloud-config` erkennt die Cloud Umgebung, dass es sich um Cloud-init-Anweisungen handelt.

Die wichtigsten Einträge sind:
* **users**: Dient zum Erstellen und konfigurieren von Usern.
* **packages**: Beschreibt, in einem Array, welche Linux Packages installiert werden sollen.
* **runcmd**: Beschreibt, in einem Array, welche Shell (sh) Befehle ausgeführt werden sollen.
* **write_files**: dient zum Erstellen von (Konfigurations-)Dateien.

Ein einfaches Beispiel für Cloud-init ist:

    #cloud-config
    users:
      - name: ubuntu
        sudo: ALL=(ALL) NOPASSWD:ALL
        groups: users, admin
        home: /home/ubuntu
        shell: /bin/bash
        lock_passwd: false
        plain_text_passwd: 'password'        
    # login ssh and console with password
    ssh_pwauth: true
    disable_root: false    
    packages:
      - unzip
    runcmd:
      - echo "Hello from Cloud-init"
    write_files:
     - content: |
        Cloud-init write_files
       path: /etc/issue
       permissions: '0644'   

Nach der Installation der VM und durchlaufen von Cloud-init kann mittels 

    sudo cloud-init status

überprüft werden, ob Cloud-init ordnungsgemäss durchgelaufen ist.

Bei Fehlern (`error`) sind die Logdateien, zu studieren

* **/var/log/cloud-init.log** – Protokolldatei der ausgeführten Ergebnisses von cloud-init
* **/var/log/cloud-init-output.log** - Ausgabe von cloud-init bzw. deren Befehle

Die verwendete Konfiguration, welche aus `User data` erzeugt wurde, kann im Verzeichnis

* **/var/lib/cloud/instance** - z.B. Datei `user-data.txt` oder `scripts/runcmd` angeschaut werden.

#### Links

* [Cloud-init Dokumentation](https://cloudinit.readthedocs.io/en/latest/)
* [Ubuntu und Cloud-init](https://help.ubuntu.com/community/CloudInit)
* [AWS und Cloud-init](http://techflare.blog/beginner-tutorial-cloud-init-in-aws/)
* [Azure und Cloud-init](https://docs.microsoft.com/en-us/azure/virtual-machines/custom-data)
* [Google und Cloud-init](https://cloud.google.com/container-optimized-os/docs/how-to/create-configure-instance#using_cloud-init_with_the_cloud_config_format)

***
### Weitere Informationen

**Linux**
* [Linux](https://github.com/mc-b/M300/blob/master/80-Ergaenzungen/linux/01-Linux.md)
* [Bash](https://github.com/mc-b/M300/blob/master/80-Ergaenzungen/linux/10-Bash.md)
* [Advanced Packaging Tool (APT)](https://github.com/mc-b/M300/blob/master/80-Ergaenzungen/linux/20-APTTool.md)
* [Public-Private-Key-Verschlüsselung](https://www.inside-it.ch/de/post/was-ist-eigentlich-20201102) und [ssh](https://wiki.ubuntuusers.de/SSH/)
* [cURL](https://github.com/mc-b/M300/blob/master/80-Ergaenzungen/linux/30-cURL.md)

**Software Konfiguration**
* [Einleitung](https://github.com/mc-b/M300/blob/master/80-Ergaenzungen/swkonfiguration/01-Einleitung.md)
* [Tools](https://github.com/mc-b/M300/blob/master/80-Ergaenzungen/swkonfiguration/02-Tools.md)
    
**Service Konfiguration**
* [Einleitung](https://github.com/mc-b/M300/blob/master/80-Ergaenzungen/srvkonfiguration/01-Einleitung.md)
* [systemd](https://github.com/mc-b/M300/blob/master/80-Ergaenzungen/srvkonfiguration/02-systemd.md)
