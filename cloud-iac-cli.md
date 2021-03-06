Übung 2: VM mit Services, mittels CLI, anlegen
----------------------------------------------

Erstellt mit NotePad, vi, nano etc. eine Datei mit Namen cloud-init.cfg.

Als Inhalt verwendet Ihr ein Cloud-init Beispiel aus [Übung 1](cloud-iac.md).

Mittels dieser Datei und dem jeweiligen Cloud CLI, erstellen wir eine neu VM.

### Azure Cloud

Anmelden an der Azure Cloud 

    az login
 
Anschliessend müssen folgende Aktionen ausgeführt werden:
* Erstellen einer Ressource Gruppe, wo unsere VMs abgelegt werden:    
* Erstellen der VM 
* Freigeben des Ports 80, damit wir via Browser auf die VM bzw. die Installierten Services zugreifen können.

<pre>
az group create --name mygroup --location southcentralus
az vm create --resource-group mygroup --name myvm --image UbuntuLTS --size Standard_D2_v4 --location southcentralus --custom-data cloud-init.cfg    
az vm open-port --port 80 --resource-group mygroup --name myvm
</pre>    
    
**Überprüft das Ergebnis, durch Anwählen der IP-Adresse Eurer VM im Browser.**

Um die VM zu löschen, genügt es, die Resource Gruppe zu löschen.    

    az group delete --name mygroup --yes    
    
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
aws ec2 create-security-group --group-name mygroup --description "Standard Ports"
aws ec2 authorize-security-group-ingress --group-name mygroup --protocol tcp --port 22 --cidr 0.0.0.0/0
aws ec2 authorize-security-group-ingress --group-name mygroup --protocol tcp --port 80 --cidr 0.0.0.0/0   
    
aws ec2 run-instances --image-id ami-0767046d1677be5a0 --security-group-ids mygroup --instance-type t2.micro --count 1 --user-data file://cloud-init.cfg
</pre>

Anschliessend können wir uns die laufenden VMs anzeigen

    aws ec2 describe-instances --output table    
    
**Überprüft das Ergebnis, durch Anwählen der IP-Adresse Eurer VM im Browser.**
        
### Links

* [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/)
* [AWS CLI](https://aws.amazon.com/de/cli/)
* [Offizielle Cloud-init Beispiele](https://cloudinit.readthedocs.io/en/latest/topics/examples.html)
* [lernMAAS und Cloud-init in der Public Cloud](https://github.com/mc-b/lernmaas/tree/master/doc/Cloud)
