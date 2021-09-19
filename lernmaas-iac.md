Übung 4: Ausbildungsumgebung in der Cloud anlegen
------------------------------------------------

Verwendet das nachfolgende Cloud-init Script um eine Umgebung für das Modul 122 anzulegen.

Geht dabei gleich vor wie bei [Übung 1](cloud-iac.md).


    #cloud-config
    hostname: m122-02
    manage_etc_hosts: true
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
      - git 
      - curl 
      - wget
      - jq
      - markdown
      - nmap
      - traceroute
    runcmd:
      - git clone https://github.com/mc-b/lernmaas /opt/lernmaas
      - sudo su - ubuntu -c "cd /opt/lernmaas && bash -x services/cloud-init.sh"

**Überprüft das Ergebnis, durch Anwählen der IP-Adresse Eurer VM im Browser.**

Mittels User `ubuntu` und Password `password` könnt Ihr Euch via `ssh` in die VM einloggen.

**Links**

* [IT Ausbildungsmodule](https://github.com/tbz-it)
* [Konfigurationsdatei mit Grössenangaben VM](https://github.com/mc-b/lernmaas/blob/master/config.yaml)
* [Offizielle Cloud-init Beispiele](https://cloudinit.readthedocs.io/en/latest/topics/examples.html)
* [lernMAAS und Cloud-init in der Public Cloud](https://github.com/mc-b/lernmaas/tree/master/doc/Cloud)