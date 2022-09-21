# Activitat 00: Profunditzant en UNIX (Mòdul 1)

*Instructor*: [Jordi Mateo Fornés](http:jordimateofornes.com)

*Course*: [Grau en Tècniques d'Interacció Digital i de Computació](http://www.grauinteraccioicomputacio.udl.cat/ca/index.html)

*University*: University of Lleida - Campus Igualada - Escola Politècnica Superior

*Estudiants*: Paula Silland
              Joan Bonell
              Ricard Bosch

## Part teòrica

### Enunciat
Cerca la diferència entre Virtualització i Emulació. *Doneu exemples i casos d'ús on es puguin fer servir*.

### Resposta
La diferència es que amb la Virtualització pots tindre més rendiment que amb la Emulació i que la sensació sigui més fluida.

Exemples d'Emulació:
  - Els emuladors de consoles, com N64 o PS1.

Exemples de Virtualització:
  - VirtualBox i poder crear máquines virtuals.

tremplin-numerique.org

computerhoy.com

### Enunciat
Cerca les diferències entre les particions **GTP** i **MRB**. *Feu una taula comparativa*.

### Resposta


profesionalview.com

### Enunciat
Cerqueu informació sobre el procediment de **Fingerprint** del protocol SSH. Per a què serveix i quins problemes intenta solucionar.

### Resposta
xxxxx

## Part pràctica: Instal·lar un paquet 

### Enunciat
La majoria de les distribucions UNIX o Linux gaudeixen de repositoris estàndard que inclouen la majoria del programari que necessitareu per executar al vostre servidor o sistema d'escriptori basat en UNIX o Linux. Si falta algun paquet, és molt probable que trobeu un repositori que podeu afegir, de manera que la instal·lació es pugui gestionar amb el gestor de paquets integrat. Això s'ha de considerar una bona pràctica. Per què? Perquè és important per a la integritat de la plataforma assegurar-se que el gestor de paquets coneix el programari instal·lat. Quan aquest és el cas, els paquets es poden actualitzar fàcilment (per solucionar vulnerabilitats i similars). Un altre motiu per instal·lar des dels dipòsits és que les dependències es compleixen fàcilment. 

La vostra tasca és investigar el seu funcionament a NetBSD i indicar els passos per instal·lar el paquet, **vim** a *bsdlab*. 

### Resposta

```sh
xxxxx
```


## Part pràctica: Personalitzant la comanda ```ls``` 

### Enunciat

Una de les comandes més utilitzades quan treballem amb sistemes UNIX és ```ls```. Ara bé, la gran majoria de vegades acabarem fent servir els arguments ```ls -la```}.
Configureu el vostre sistema **bsdlab** amb una nova comanda ```la``` que permeti fer ```ls -la```.Veure exemple. Expliqueu els passos realitzats.

```sh
$ la
total 68
drwxr-xr-x  3 jordi  users   512 Sep  9 15:54 .
drwxr-xr-x  3 root   wheel   512 Sep  9 11:10 ..
-rw-r--r--  1 jordi  users  1772 Sep  6 02:31 .cshrc
-rw-r--r--  1 jordi  users   431 Sep  6 02:31 .login
-rw-r--r--  1 jordi  users   265 Sep  6 02:31 .logout
-rw-r--r--  1 jordi  users  1498 Sep  6 02:31 .profile
-rw-r--r--  1 jordi  users   166 Sep  6 02:31 .shrc
drwxr-xr-x  2 jordi  users   512 Sep  9 15:54 .ssh
-rw-r--r--  1 jordi  users     0 Sep  9 14:13 a.txt
-rw-r--r--  1 jordi  users     0 Sep  9 14:51 b.txt
-rw-r--r--  1 jordi  users  2048 Sep  9 14:52 f.tar
-rw-r--r--  1 jordi  users   125 Sep  9 14:52 f.tar.bz2
-rw-r--r--  1 jordi  users   106 Sep  9 14:52 f.tar.gz
-rwxr-xr-x  1 jordi  users  8744 Sep  9 15:26 hello
-rw-r--r--  1 jordi  users   150 Sep  9 15:26 hello.c
```

### Resposta
xxxxx

## Part pràctica: Problema de l'any 2038 

### Enunciat
Com us he explicat a classe els sistemes UNIX sofreixen d'un problema amb les dates causat: ```time_t``` emmagatzema el temps com un nombre enter signat de 32 bits. Per tant, únicament pot representar enters entre -(231) i 231 -1, per tant l'última hora que es pot codificar correctament és 231 - 1 segons després de l'època UNIX (03:14:07 UTC el 19 de gener de 2038). Intentar augmentar al segon següent (03:14:08) farà que l'enter es desbordi, establint el seu valor a -(231), que els sistemes interpretaran com a 231 segons abans de l'època (20:45:52 UTC el 13 de desembre de 1901).

La vostra tasca és obtenir una prova del delicte en el vostre sistema **bsdlad**. Heu de demostrar si aquest afer existeix o no en la vostra instal·lació actual. Heu d'indicar els passos a realitzar per demostrar-ho.

### Resposta
xxxxx

## Part pràctica: Shell 

### Enunciat

En aquest punt repassarem les comandes treballades a la sessió de laboratori 0. 

La vostra tasca és anotar totes les comandes ordenades que aneu utilitzant per resoldre cada ítem.

1. En el vostre directori *home*, heu de crear la següent estructura de *fitxers i directoris*: **week0/teoria/, week0/laboratori/, week0/handson, week0/notes.md, code/, activities/ README.md**
2. Feu servir l'eina *sftp* per pujar els documents vl00.pdf, lab00.pdf, ho00.pdf a la carpeta corresponent.
3. Editeu el fitxer notes.md amb el text **template.md**.
4. Mostreu les 3 primeres línies i les 2 ultimes per **stdout** del fitxer **template.md**.
5. Copieu el fitxer */etc/passwd* al vostre directori d'inici. La còpia ha d'incloure: *el nom, la data i l'hora de la darrera modificació*. (**man cp**). Anomeneu el fitxer com *cpasswd*.
6. Transformeu el fitxer en un fitxer ocult anomenat **.pass**.
7. Permeteu que **qualsevol usuari del sistema** pugui **llegir, escriure i executar** dins la carpeta *code*.
8. Comprimiu tot el contingut del vostre directori en un **backup.tar.gz2**}.
9. Descarregueu per *sftp* el fitxer *backup.tar.gz2* a la vostra màquina real.
10. Elimineu tots els fitxers del vostre home. Alerta (reviseu **man rm**) no volem eliminar els fitxers ocults com  **.ssh, .cshrc,.login,.logout...***}

template.md:
```md
# Week 00

## A

## B

## C
```

### Resposta
xxxxx