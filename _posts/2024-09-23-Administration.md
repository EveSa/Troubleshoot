---
layout: post
title: "Administration"
---
# Les Bases

Selon (« [The Linux System Administrator’s Guide](https://tldp.org/LDP/sag/html) » s. d.)

Un ordinateur, c’est comme une maison 🏠. Il nécessite donc une administration méticuleuse : son nettoyage, sa réparation quand nécessaire. Avec le Système d’Administration, on s’occupe de l’*Operating System* et pas de l’architecture de l’ordinateur en temps que tel.

Vous logez dans un immeuble meublé où la fonctionnalité des pièces à été déterminée.

> *"In the beginning, the file was without form, and void; and emptiness was upon the face of the bits. And the Fingers of the Author moved upon the face of the keyboard. And the Author said, Let there be words, and there were words.”*
> 

## Les fondations

L’assemblage de Linux (le kernel) et GNU (les programmes du système d’exploitation) 💥GNU/Linux

- **Kernel**
    
    Lien vers la structure physique de l’ordinateur, il alloue l’espace de chaque service et gère les échanges avec l’extérieur (le réseau)
    
    Ses parties les plus importantes sont : le *memory manager* et le *process manager*. C’est le *memory manager* qui s’occupe du swap et de l’assignation de partie de la mémoire à des process tandis que le *process manager* créé les process et implémente le multitasking. 
    
    Il correspond au monture de fenêtre, la peinture, les cloisons, les portes qui se mettent sur la structure en béton sans la modifier
    
    Le Coeur de la strucuture doit s’adapter à tous type de matériaux (Apple, Helwett-Packard, Intel, SnapDragon ?) et contient donc de multiple *Hardware device drivers*
    
- **System programs**
    
    Programmes permettant la bonne (sur)vie du système (ex : le programme *mount* )
    
    Installe ta cuisine, ta douche, tes toilettes, …
    
- Application programs
    
    ta salle de yoga, ta collection de jeux, tes plantes vertes et tes tableaux
    

La différence entre les programmes essentiels et les programmes non-essentielle est perméable. Elle dépend de la perception de chacun

Les programmes utilisent le kernel pour tourner en mode utilisateur

Une **distribution : a kernel + une OS**

## Organiser ses Appartements

On ne mange pas dans sa salle de bain : on observe les mêmes règles dans un PC

Chaque dossier à une fonction précise avec du mobilier spécifique pour un usage spécifique. Et on retrouve les mêmes pièces (dossiers) dans toutes les maisons (machines). Comme dans l’organisation des pièces dans les demeures occidentales : salon, chambre, cuisine, salle de bain, …

La structure des systèmes Linux est la suivante :

```bash
|_home
	|_ftp
	|_liw
	|_linus
|_boot    #bootstrap loader : commands needed during bootup e.g. LInux LOader and GRUB
|_bin     #binary : commands used during bootup and after for normal usage
|_sbin    #system binary : commands used only during bootup
|_proc    #virtual file system that povides informations about running processes
|_usr     # user
	|_bin   #binary files that cannot go to the /bin folder
	|_sbin  #system administration commands that are not needed on the root filesystem
	|_lib   #library that are linked with /usr/bin
	|_local # the place for locally installed softwares
|_boot    # bootstrap loader which run when the machine turns on
|_lib     #shared libraries needed by programs on the root filesystem
|_dev     #device files that helps user interface with the various device on the system
|					#tout ce qui a attrait aux disques durs, floppy disks, etc...
|_etc     #configuration file specific to the machine
	|_passwd
	|_shadow
	|_group
|_var    #fichiers changeant:pas partagé sur le réseau. Existe pour que /usr soit Read Only
	|_lib 
	|_log
	|_run  #informations vraies jusqu'au prochain boot
	|_spool#pour le reseau (imprimantes, mails, ...)
	|_tmp  #pour des fichiers temporaire à conserver plus longtemps que /tmp
```

Au premier niveau se trouve le “système de fichier racine”. Il est la base des systèmes de fichiers sur lequel d’autres systèmes peuvent être montés.

Le système /usr est le système qui contient toutes les commandes de base du système entier. Il ne doit JAMAIS être modifié manuellement

le système /home contient les fichiers personnel de l’utilisateur. (Un peu comme les différentes chambres dans une maison)

Il y a plusieurs type de *filesystems*  qui ne sont pas intercompatibles entre les systèmes d’explotations. On note minix et ext[1-3] pour linux et msods et ntfs pour windows.

Lors de la création de la maison (de la distribution sur la machine), on doit partitionner les disques, installer les systèmes de fichiers sur les différents disques ou partitions et monter (mount) tous les systèmes ensemble pour ne créer qu’une seule arborescence de fichier accessible par Linux sur toutes les partitions et disques.

## Mettre la machine en branle

> The information about how a hard disk has been partitioned is stored in its first sector (that is, the first sector of the first track on the first disk surface).  The first sector is the *master boot record* (MBR) of the disk; this is the sector that the BIOS reads in and starts when the machine is first booted.  The master boot record contains a small program that reads the partition table, checks which partition is active (that is, marked bootable), and reads the first sector of that partition, the partition's *boot sector* (the MBR is also a boot sector, but it has a special status and therefore a special name).  This boot sector contains another small program that reads the first part of the operating system stored on that partition (assuming it is bootable), and then starts it.
> 

## Gestion des droits des habitants

### What is root user ?

Root user = god mod

You NEVER want to run only as root. This could be very dangerous

Comme dans un immeuble :

- il y a des parties accessible à tous les habitants
- des parties qui nécessitent des clés spécifiques aux habitants (les appartements)

On distingue les locataires( les *users*) des propriétaires (les *superusers*).

Comme dans un immeuble, on peut :

- vendre un appartement (changer le “propriétaire” d’un fichier `chown`)
- Donner des clés pour :
    - visiter l’appartement ( `chmod +r`)
    - réaménager l’appartement (`chmod +w`)
    - faire des travaux dans l’appartement (`chmod +x`)
    - faire une collocation ou louer (`chmod +rwx`)

Vous pouvez donner des clés :

- à vous même (`chmod u+`)
- à votre famille (votre *user group*) (`chmod g+`)
- aux autres uniquement (`chmod o+`)
- ou à tout le monde (`chmod a+`)

⚠️Il faut éviter de vendre votre immeuble⚠️
⚠️     Vous risquez de terminer à la rue     ⚠️

On navigue dans un immeuble de façon classique:

- dans chaque pièces il y a différentes portes qui ont des petits noms avec écrit qui à le droit d’y faire quoi

→ pour avoir la liste des portes il suffit de taper `ls` (pour ‘liste’) et pour connaître les différents droits `ls -a`

## Mots-clés à expliciter

runlevels

getty : manager de login

daemon

logs

cron et crontabs

at et atd (pareil que cron mais une seule fois)

Filesystem

<aside>
❗ In Unix all processes must be in a single tree, so orphans must be adopted

</aside>

## GUI : Graphical User Interface

Window system ( X [Window Sytem], fvwm, icewm, blackbox, windowmaker) → tool upon which a GUI can be implemented

GUI may be directly incorporated in the kernel but this is not the case in linux (which use user level programs)

# S’installer dans ses appartements

## Installer des paquets

Lorsque le paquet est disponible nativement dans la distribution linux

```bash
apt install paquet
```

Sinon, il faut télécharger le fichier `.deb` (selon les distribution), équivalent des `.exe`en Windows

et faire la même manipulation. On peut télécharger les fichiers directement en ligne de commande avec la commade `wget`:

```bash
wget https://nom-de-domaine/nom-du-fichier.deb
apt install nom-du-fichier.deb
```

On peut ajouter l’option `-P dossier-d-extraction/` pour choisir où télécharger le fichier

→ le bash c’est bien

→ le python c’est mieux

## Créer des chambres d’expérimentations : Les environnements virtuels et les machines virtuelles

- **Quelle est la différence entre une machine virtuelle et un environnement virtuel ?**
    
    Une machine virtuelle est un type d’environnement virtuel sur lequel on a installé une OS complète ce qui permet de simuler une machine. Une machine virtuelle est un environnement virtuel lourd
    
- Les points positifs des Machines virtuelles
    1. Les machines virtuelles permettent de créer un environnement commun à toutes les personnes contribuant à un même projet pour éviter le problème du “*but it works on my computer*”. Cette utilisation des machines virtuelles est maintenant dépréciée avec la démocratisation des Dockers
    2. Les machines virtuelles permettent de contourner les restrictions imposée sur une machine tout en gardant un haut niveau de sécurité
    3. Les machines virtuelles permettent de cloisonner efficacement les environnements au même titre qu’un environnement et permet de travailler sur un grand nombre d’OS différent

### Environnements virtuels

Création avec virtualenv: 

```bash
apt install pip
pip install virtualenv
virtualenv ENV_NAME
source ./ENV_NAME/bin/activate
```

Création avec conda

```bash
apt install conda
conda create --name ENV_NAME -y python=VERSION
conda activate ENV_NAME
```

Il faut parfois initialiser conda avec la commande `conda init SHELL_NAME` pour faire fonctionner l’environnement

### Docker

## Les logiciel de gestion des paquets python

pip⚡conda

⚠️ Certains paquets ne sont compatibles qu’avec certaines version de python ⚠️

## Lancer des commandes en parallèle

```bash
for dir in $(find -type d -name *_fr); do $(ls $dir|wc -l)& done;
```

# 🏙️S’ouvrir au monde : Networking🏙️

[Linux Network Administrators Guide](http://www.tldp.org/LDP/nag2/index.html)

## Aller visiter d’autres maisons:

## Mots-clés

TCP/IP

SSH : Secure Shell

FTP : File Transfert Protocol

NFS : Network File System. Included directly into the linux kernel

### Les clés SSH

## Les Proxies

Quand on rencontre des problèmes de connexion sur un réseau publique ou professionnel, il est possible qu’un proxy ait été mis en place par le service IT.

### Savoir si on est derrière un proxy

```bash
echo "$http_proxy $https_proxy"
```

### Setter les proxies dans un code 🐍

```bash
import os
os.environ['HTTP_PROXY'] = proxy
os.environ['HTTPS_PROXY'] = proxy
```

### L’intérêt des proxies

???

## Les certificats de confiances

Il y a des agents qui donnent des certificats

Ensuite chaque logiciel a son portefeuille de certificat à *trust.* Sous python ,c’est certifi qui gère les certificats.

## Les requêtes

- `Get`
    
    demande une ressource au serveur
    
- `Post`
    
    Envoie des données au serveur
    
- `Put`
    
    Envoie un état au serveur
    

## Application Programming Interfaces (API)

## API Architecture Styles

- REST
- SOAP

### End Point

http://www.tldp.org/LDP/nag2/index.html

## Les ports

```bash
lsof -i:PORTNUMBER
```

Permet de connaître les process ouverts sur un port