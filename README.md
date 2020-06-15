# M300-LB2

## Inhaltsverzeichnis
- [M300 - LB2 Dokumentation Filip Stevanovic](#m300---lb2-dokumentation-filip-stevanovic)
  - [Inhaltsverzeichnis](#inhaltsverzeichnis)
- [K1](#k1)
  - [VirtualBox](#virtualbox)
  - [Vagrant](#vagrant)
  - [Visual Studio Code](#visual-studio-code)
  - [Git-Client](#git-client)
  - [SSH-Key](#ssh-key)
- [K2](#k2)
  - [GitHub Account](#github-account)
- [K3](#k3)
  - [Testen](#testen)
    - [Apache](#apache)
- [K4](#k4)
  - [Firewall](#firewall)
  - [Reverse-Proxy](#reverse-proxy)
  - [SSH](#ssh)
- [K5](#k5)
  - [Vergleich Vorwissen - Wissenszuwachs](#vergleich-vorwissen---wissenszuwachs)
  - [Reflexion](#reflexion)


K1
==========

> [⇧ *Nach oben*](#inhaltsverzeichnis)

## VirtualBox

*Vorbereitungen für die VM Erstellung*

1. Als erstes auf [dieser Webseite](https://www.virtualbox.org) VirtualBox heruntergeladen und danach GUI-basiert installiert. Keine Speziellen einstellungen vornehmen bei der GUI-basierten installation.
2. Danach Ubuntu Desktop 20.04 auf [dieser Webseite](https://www.ubuntu.com/#download) heruntergeladen. 

*VM erstellen mit Virtualbox*

1. VirtualBox starten
2. Mit einem klick auf `Neu` eine neue VM erstellen.
3. Als nächstes muss man folgende Attribute angeben:
   *  Name:           `m300_ubuntu`
   *  Typ:            `Linux`
   *  Version:        `Ubuntu (64-bit)`
   *  Speichergrösse: `2048 MB`
   *  Platte:         `[X] Festplatte erzeugen`
4. Nun auf `Erzeugen` klicken
5. Im nächsten Fenster, folgende Informationen eintragen:
   *  Dateipfad:                       standard
   *  Dateigrösse:                     `10.00 GB`
   *  Dateityp der Festplatte:         `VMDK (Virtual Maschine Disk)`
   *  Storage on physical hard disk:   `dynamisch alloziert`
6. Nun erneut auf `Erzeugen` klicken, dann im Hauptmenü die VM anwählen (blau markiert) und den Punkt `Ändern` aufrufen
7. Im Abschnitt `Massenspeicher` den SATA-Controller anwählen und auf das CD+Symbol klicken
8. Unter `Medium auswählen` das zuvor heruntergeladene Systemabbild (ISO-Datei) anwählen
9. Alle Änderungen speichern und die VM starten
10. Nun den Installationsanweisungen der OS-Installation folgen. 


*Folgende Befehle ausführen in der Bash der VM.*

1. Paketliste neu einlesen und Pakete aktualisieren:
   ```Shell 
   $  sudo apt-get update   #Paketlisten des Paketmanagement-Systems "APT" neu einlesen
   
   $  sudo apt-get update   #Installierte Pakete wenn möglich auf verbesserte Versionen aktualisieren

   $  sudo reboot           #System-Neustart durchführen
   ```
2. Software Controlcenter "Synaptic" installieren:
   ```Shell 
   $  sudo apt-get install synaptic
   ````
3. Nach erfolgreicher Installation in der Suche nach "Synaptic Package Manager" suchen und diesen starten
4. Innerhalb des Managers nach "apache" (Webserver-Programm) suchen und dieses (inkl. aller Abhängigkeiten) installieren
5. System-Neustart durchführen:
   ```Shell 
   $  sudo reboot
   ```
6. Prüfen ob der Standard-Content des Webservers unter "http://127.0.0.01:80" erreichbar ist.


## Vagrant
> [⇧ *Nach oben*](#inhaltsverzeichnis)

*Vagrant installation*

Zuerst habe ich Vagrant auf [dieser Webseite](https://www.vagrantup.com/ "vagrantup.com")   heruntergeladen und GUI-Basiert installiert.

*Mit Vagrant eine VM erstellt.*
1. Bash öffnen
2. In Ordner für die VM installation gehen:
    ```Shell
      $ cd C:\User\filip\Documents\Modul_300

    ``` 
3. Vagrantfile erzeugen, VM erstellen und starten:
    ```Shell
      $ vagrant box add http://10.1.66.11/vagrant/ubuntu/xenial64.box --name ubuntu/xenial64  #Vagrant-Box vom Netzwerkshare hinzufügen
      $ vagrant init ubuntu/xenial64        #Vagrantfile erzeugen
      $ vagrant up --provider virtualbox    #Virtuelle Maschine erstellen & starten
    ``` 
4. Die VM ist nun bereit und kann mit SSH-Zugriff bedient werden:
    ```Shell
      $ cd C:\Users\filip\Documents\Modul_300    #Zum Verzeichnis der VM wechseln
      $ vagrant ssh                       #SSH-Verbindung zur VM aufbauen
     ```

*VM erstellen mit Apache Webserver mit abgeändertem  Vagrantfile erstellt:*

1. Bash öffnen
2. In das M300-Verzeichnis wechseln:
    ```Shell
      $ cd C:\Users\filip\Documents\Modul_300
     ```
3. VM erstellen und starten:
    ```Shell
      $ vagrant up
    ``` 
4.Webbrowser prüfen, ob der Standard-Content des Webservers unter "http://127.0.0.01:8080" (localhost) erreichbar ist
5. Später habe ich im Ordner `$home\var\www\web` die Hauptseite `index.html` editieren und das Resultat überprüfen.
6. Abschliessend habe die VM  löschen:
    ```Shell
      $ vagrant destroy -f
    ```

## Visual Studio Code
> [⇧ *Nach oben*](#inhaltsverzeichnis)

*Visual Studio Code installieren und konfigurieren.*

1. Visual Studio Code auf [dieser](https://code.visualstudio.com/"visualstudio.com") Seite heruntergelden und GUI-basiert installieren.
2. Danach im Editor drei wichtige Extensions hinzugefügt:

* Markdown All in One (von Yu Zhang)
* Vagrant Extension (von Marco Stanzi)
* vscode-pdf Extension (von tomiko1207)

Dazu folgende Anweisungen befolgen: 

  1. Visual Studio Code öffnen
  2. Die Tastenkombination `CTRL` + `SHIFT` + `X` drücken und in der Suchleiste die erwähnten Extensions suchen.
  3. Auf `Install` klicken und anschliessend auf `Reload`, um die Extension in den Arbeitsbereich zu laden.

*Dokumentation lokal mit Visual Studio Code zu bearbeiten*

  1. Änderungen am Readme-File von meinem Repositorys vornehmen
  2. Datei speichern und in der linken Leiste das Symbol mit einer "1" aufrufen
  3. Unter dem Abschnitt *Changes* die betroffenen Files bezüglich ihres Changes "stagen"
  4. Nachricht hinterlegen und Haken setzen
  5. Bei den 3 Punkten (...) auf *Push* klicken
  6. Warten, bis Dateien vollständig gepusht wurden

## Git-Client
> [⇧ *Nach oben*](#inhaltsverzeichnis)


*Client installieren*
Client-Installation auf [dieser](https://git-scm.com/downloads) Seite heruntergeladen und GUI-basiert installieren.

*Den Client konfiguriert:*
1. Bash öffnen
2. Git konfigurieren mit Informationen des GitHub-Accounts:
    ```Shell
      $ git config --global user.name "<filip-tbz>"
      $ git config --global user.email "<filipstevanoviic@gmail.com>"
    ``` 

*Repository heruntergeladen, um lokal zu arbeiten.*

1. Bash öffnen
2. Ordner für Repository erstellen:
    ```Shell
      $ cd C:\Users\djord\Documents\Modul_300
      $ mkdir MeinLokalesRepository
     ```
3. Repository mit SSH klonen:
    ```Shell
      $ git clone git@github.com:djordje-tbz/LB02.git

      Cloning into 'lb2'...
    ``` 
4. Repository aktualisieren und Status anzeigen:
    ```Shell
      $ git pull

      Already up to date.
    ```

## SSH-Key 
> [⇧ *Nach oben*](#inhaltsverzeichnis)

*SSH-Key erstellen lokal*

1.  Folgenden Befehl mit der Account-E-Mail von GitHub in Bash einfügen:
    ```Shell
      $  ssh-keygen -t rsa -b 4096 -C "filipstevanoviic@gmail.ch"
    ```
2. Neuer SSH-Key wird erstellt:
    ```Shell
      Generating public/private rsa key pair.
    ```
3. Bei der Abfrage, unter welchem Namen der Schlüssel gespeichert werden soll, die Enter-Taste drücken (für Standard):
    ```Shell
      Enter a file in which to save the key (~/.ssh/id_rsa): [Press enter]
    ```
4.Passwort für den Key festgelegt:
    ```Shell
      Enter passphrase (empty for no passphrase): [Passwort]
      Enter same passphrase again: [Passwort wiederholen]
    ```
*SSH-Key dem Client hinzufügen*

1. Auf www.github.com im Benutzerkonto *Settings* aufrufen
2.  Unter den Menübereichen auf der linken Seite zum Abschnitt *SSH und GPG keys* wechseln
3.  Auf *New SSH key* klicken
4.  Im Formular unter *Title* die Bezeichnung MB SSH-Key vergeben
5.  Den Key von der Datei *C:\Users\User\.ssh\id_rsa.pub* einfügen und auf *Add SSH key* klicken

*SSH Zugriff auf VM*

SSH Zugriff auf VM:
```shell
vagrant ssh
```
K2
======


## Eigene Lernumgebung
> [⇧ *Nach oben*](#inhaltsverzeichnis)

*Github Account erstellt*
1. Auf [GitHub.com](https://github.com) gehen
2. Auf *Sign up* klicken
3. Username, E-mail und Passwort eingeben sowie Aufgabe zum verifizieren lösen
4. Auf *Create an Account* klicken

*Mark Down Extension Visual Studio Code hinzufügen*
1. Virtual Studio Code öffnen
2. *CTRL* + *SHIFT* + *X* drücken und nach Mark Down suchene. 
3. Auf *install* klicken.

K3
======


> [⇧ *Nach oben*](#inhaltsverzeichnis)
## Vagrant

*Vagrant Befehle*


| Befehl              | Funktion       |
| ------------------- | -------------- |
| `vagrant init`      | Dadurch wird das aktuelle Verzeichnis als Vagrant-Umgebung initialisiert|
| `vagrant up`        | Dieser Befehl startet den Gast-Rechner/Virtuelle Maschine.|
| `vagrant ssh`       | Dadurch wird SSH in einen laufenden Vagrant-Rechner eingespielt und man erhält Zugriff auf die Shell.|
| `vagrant status`    | Dadruch wird der aktuelle Status des Gastrechners angezeigt. |
| `vagrant shutdoown` | Dadurch wird der Gast-Rechner heruntergefahren. |
| `vagrant destroy`   | Dadurch werden alle Ressourcen, die erstellt wurden zum Gast-Rechner und der Gast-Rechner selbst gelöscht.|

*Testen*

Apache
- index.html file ändern und schauen ob die Änderung übernommen wurde.
- Im Webbrowser überprüfen.

K4
======

> [⇧ *Nach oben*](#inhaltsverzeichnis)
 
## Firewall

  *Automatisch Firewall Regeln erstellt, indem die Zeilen ins Vagrantfile eingefügt werden*

1. Vagrantfile öffnen
2. Folgende Zeilen einfügen:
    Shell
      sudo apt-get install ufw
      sudo ufw allow 80/tcp
      sudo ufw allow 22/tcp
      sudo ufw allow out 22/tcp 
      sudo ufw enable
     

## Reverse-Proxy
*Automatisch einen Reverse-Proxy installieren, indem die Zeilen ins Vagrantfile eingefügt werden*
1. Vagrantfile öffnen
2. Folgende Zeilen einfügen:
    Shell
    sudo apt-get -y install libapache2-mod-proxy-html
    sudo apt-get -y install libxml2-dev

    sudo a2enmod proxy
    sudo a2enmod proxy_html
    sudo a2enmod proxy_http
     

## Benutzer und Rechtevergabe

*Automatisch User mit Passwort erstellt, indem die Zeilen ins Vagrantfile eingefügt werden*

1. Vagrantfile öffnen
2. Folgende Zeilen einfügen:
    Shell
      sudo groupadd testadmin
      sudo useradd user1 -g testadmin -m -s /bin/bash 
      sudo useradd user2 -g testadmin -m -s /bin/bash 
      sudo chpasswd <<<user1:abc123	
      sudo chpasswd <<<user2:abc123
    
## SSH

*Automatisch ein SSH Zugang erstellt, indem die Zeilen ins Vagrantfile eingefügt werden*

1. Vagrantfile öffnen  
2. Folgende Zeilen einfügen:
    Shell
      sudo apt-get -y install openssh-server
    
K5
======

> [⇧ *Nach oben*](#inhaltsverzeichnis)
 

## Persöhnliche Lernentwicklung

*Bereits bekannt*

- Virtualisierungen mit Linux und Windows kannte ich schon zuvor da ich auch im Geschäft mit der Virtualisierung arbeite, aber natürlich nicht wie in der Schule, da wir im Betrieb viele Einschränkungen haben.
- Virtualbox kannte ich von vorherigen ÜK Modulen.

*Gelerent in diesem Modul*


 - Vagrante kannte ich nicht und ist für mich neu.
 - Auch mit Markdown bin ich zuvor nicht in Berührung gekommen.
 - Github ist auch neu für mich.

*Fazit*

Ich habe in diesem Modul sehr viel gelernt im Bezug auf die automatisierte Virtualisierung und wie man dies aufsetzen kann. In meinem nächstem Team kann ich dieses Wissen sicherlich brauchen, da wir in einer Cloud Testing anbieten und es wäre sicherlich intelligent Browser Testing auf einer VM zu machen, welche automatisiert aufgesetzt wurde von Vagrant.

## Reflexion
Zu Beginn hatte ich start Probleme, da ich das ganze nicht richtig verstanden habe. Zum Glück gab es die Anleitung von Herr Rohr und natürlich auch meine Mitschüler. Ich hatte leider bei mehreren Sachen Schwierigkeiten bei diesem Modul. Ich hatte probleme mit dem Responsitory, dieses kann irgendwie nicht lokal abgespeichert werde konnte und beim automatisiertem VM aufsetzen wusste ich nicht wie genau das Vagrantfile ändern, aber dies funktionierte dann nach langer google recherche. 







