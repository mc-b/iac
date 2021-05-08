Übung 4: Ausbildungsumgebung in der Cloud, mittels CLI, anlegen
------------------------------------------------

Erstellt mit NotePad, vi, nano etc. eine Datei mit Namen cloud-init.cfg.

Als Inhalt verwendet Ihr ein Cloud-init Beispiel aus [Übung 3](lernmaas-iac.md).

Mittels dieser Datei und dem jeweiligen Cloud CLI, erstellen wir eine neu VM.

### Azure Cloud

Anmelden an der Azure Cloud 

    az login
 
Anschliessend müssen folgende Aktionen ausgeführt werden:
* Erstellen einer Ressource Gruppe, wo unsere VMs abgelegt werden:    
* Erstellen der VM 
* Freigeben des Ports 80, damit wir via Browser auf die VM bzw. die Installierten Services zugreifen können.

<pre>
az group create --name mylerngroup --location southcentralus
az vm create --resource-group mylerngroup --name m122-02 --image UbuntuLTS --size Standard_D2_v4 --location southcentralus --custom-data cloud-init.cfg    
az vm open-port --port 80 --resource-group mylerngroup --name m122-02
</pre>    
    
**Überprüft das Ergebnis, durch Anwählen der IP-Adresse Eurer VM im Browser.**

Um die VM zu löschen, genügt es, die Resource Gruppe zu löschen.    

    az group delete --name mylerngroup --yes    
    
### AWS Cloud

Einloggen in AWS Cloud

    aws configure
 
    AWS Access Key ID [****************WBM7]:
    AWS Secret Access Key [****************eKJA]:
    Default region name [eu-central-1]:
    Default output format [None]:
    
Anschliessend müssen folgende Aktionen ausgeführt werden:
* Security Group erstellen und Ports öffnen
* Erstellen der VM 

<pre>
aws ec2 create-security-group --group-name mylerngroup --description "Standard Ports"
aws ec2 authorize-security-group-ingress --group-name mylerngroup --protocol tcp --port 22 --cidr 0.0.0.0/0
aws ec2 authorize-security-group-ingress --group-name mylerngroup --protocol tcp --port 80 --cidr 0.0.0.0/0   
    
aws ec2 run-instances --image-id ami-0767046d1677be5a0 --security-group-ids mylerngroup --instance-type t2.micro --count 1 --user-data file://cloud-init.cfg
</pre>

Anschliessend können wir uns die laufenden VMs anzeigen

    aws ec2 describe-instances --output table    
    
**Überprüft das Ergebnis, durch Anwählen der IP-Adresse Eurer VM im Browser.**
        
### Links

* [IT Ausbildungsmodule](https://github.com/tbz-it)
* [Konfigurationsdatei mit Grössenangaben VM](https://github.com/mc-b/lernmaas/blob/master/config.yaml)
* [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/)
* [AWS CLI](https://aws.amazon.com/de/cli/)
* [Offizielle Cloud-init Beispiele](https://cloudinit.readthedocs.io/en/latest/topics/examples.html)
* [lernMAAS und Cloud-init in der Public Cloud](https://github.com/mc-b/lernmaas/tree/master/doc/Cloud)
        
