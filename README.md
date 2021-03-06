Infrastructure as Code Workshop
===============================

Workshop "Infrastructure as Code" anlässlich des [Interkantonalen Weiterbildungstags der Informatikfachkunde-Lehrpersonen](https://sites.google.com/view/weiterbildungstag-informatik/home).

* [Vorbereiten](Vorbereiten.md)
* [Folien](2021-05-12-IaCundLernMAAS.pdf)

### Eisenzeit (Imperativ) vs. die Cloud (Deklarativ)

In der **Eisenzeit** der IT waren Systeme direkt an physische Hardware gebunden. 
Das Bereitstellen und Warten der Infrastruktur war manuelle Arbeit, die die Menschen dazu zwang, zu klicken und zu tippen, um die Systeme am laufen zu halten. 
Da Änderungen viel Zeit und Geld erforderten, wurde in Änderungsmanagement und sorgfältige Prüfung, investiert
Dies machte Sinn, weil es teuer war, etwas falsch zu machen.

Im **Cloud-Zeitalter** der IT werden Systeme von der physischen Hardware entkoppelt.
Die routinemässige Bereitstellung und Wartung kann an Softwaresysteme delegiert werden, um den Menschen von Routinearbeiten zu befreien. 
Änderungen können in Minuten, wenn nicht Sekunden vorgenommen werden. 
Wir können diese Geschwindigkeit nutzen für eine höhere Zuverlässigkeit sowie schnellere Einführung von neuen Produkten. 

### Infrastruktur als Code

* Infrastruktur als Code ist ein Ansatz zur Automatisierung der Infrastruktur, der auf Praktiken aus der Softwareentwicklung basiert. 
* Dabei werden konsistente, wiederholbare Prozesse für die Bereitstellung und Änderung von Systemen und deren Konfiguration verwendet.
* Änderungen werden an Deklarationen (Code) vorgenommen und dann durch automatisierte Prozesse, auf Systeme übertragen.
* Infrastruktur als Code hat sich in den anspruchsvollsten Umgebungen bewährt. Für Unternehmen wie Amazon, Netflix, Google und Facebook sind IT-Systeme nicht nur geschäftskritisch. Sie sind das Geschäft!

### Ziele von Infrastruktur als Code

* Die IT-Infrastruktur unterstützt und ermöglicht Veränderungen, anstatt ein Hindernis oder eine Einschränkung zu sein.
* Änderungen am System sind Routine, ohne Drama oder Stress für Benutzer oder IT-Mitarbeiter.
* IT-Mitarbeiter verbringen ihre Zeit mit wertvollen Dingen, die ihre Fähigkeiten einbeziehen, und nicht mit sich wiederholenden Routineaufgaben.
* Benutzer können die benötigten Ressourcen definieren, bereitstellen und verwalten, ohne dass IT-Mitarbeiter dies für sie tun müssen.
* Teams können sich einfach und schnell von Fehlern erholen, anstatt davon auszugehen, dass Fehler vollständig verhindert werden können.
* Verbesserungen werden kontinuierlich vorgenommen und nicht durch teure und riskante „Urknall“ -Projekte.
* Lösungen für Probleme werden durch Implementierung, Test und Messung bewiesen, anstatt sie in Besprechungen und Dokumenten zu diskutieren.

## Übungen

**Cloud** 

* [Übung 1: VM mit Services in der Cloud anlegen](cloud-iac.md)
* [Übung 2: VM mit Services, mittels CLI, anlegen](cloud-iac-cli.md)
* [Übung 3: Cloud-init Hands-on](cloud-init-hands-on.md)

**LernMAAS**

* [Übung 4: Ausbildungumgebung in der Cloud anlegen](lernmaas-iac.md)
* [Übung 5: Ausbildungsumgebung in der Cloud, mittels CLI, anlegen](lernmaas-iac-cli.md)

## Links

### Weiterbildungen

* [Selbststudium Modul 300](https://github.com/mc-b/m300)
* [Von der Virtualisierung über Cloud und Container bis Serverless («VIRTAR»)](https://www.digicomp.ch/weiterbildung/development-trainings/software-engineering-trainings/it-architektur/softwarearchitektur/design-organisation/kurs-von-der-virtualisierung-ueber-cloud-und-container-bis-serverless)
* [Docker und Kubernetes – Übersicht und Einsatz ](https://www.digicomp.ch/trends/docker-trainings/docker-und-kubernetes-uebersicht-und-einsatz)
* [DevOps Engineering Practices & Tools (CDI)](https://www.digicomp.ch/weiterbildung/development-trainings/software-engineering-trainings/software-engineering-basics/devops-in-der-software-entwicklung/kurs-devops-engineering-practices-tools)
* [Dipl. Techniker/in HF Informatik, Modul CNT (Cloud Native Technologien)](https://tbz.ch/weiterbildung-tbz/it-services-engineer-hf/)
* [CAS Cloud and Platform Manager](https://www.hslu.ch/de-ch/informatik/weiterbildung/networking-and-innovative-technologies/cas-cloud/)

### Bücher

* [Infrastructure as Code. Managing Servers in the Cloud. Kief Morris](https://infrastructure-as-code.com/book/)
* [Cloud Native Infrastructure. Patterns for Scalable Infrastructure and Applications in a Dynamic Environment. Justin Garrison and Kris Nova](https://learning.oreilly.com/library/view/cloud-native-infrastructure/9781491984291/)

### Produkte und Projekte

* [LernMAAS](https://github.com/mc-b/lernmaas)
* [MAAS](https://maas.io)
* [Cloud-init](https://cloudinit.readthedocs.io/en/latest/)
* [Wireguard](https://www.wireguard.com/)

- - - 

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/ch/"><img alt="Creative Commons Lizenzvertrag" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/3.0/ch/88x31.png" /></a><br />Dieses Werk ist lizenziert unter einer <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/ch/">Creative Commons Namensnennung - Nicht-kommerziell - Weitergabe unter gleichen Bedingungen 3.0 Schweiz Lizenz</a>.

- - - 

* Autor: Marcel Bernet 
* Mail: ![](x_gitressourcen/images/mailto.png)
