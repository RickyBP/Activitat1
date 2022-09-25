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
La principal diferència consisteix en que la Virtualització ens permet crear més d'un sistema operatiu (virtual) dins d'un altre, per l'altre banda l'emulació permet que el sistema operatiu principal es comporti com un altre sistema. D'aquesta manera amb la Virtualització pots tindre més rendiment que amb l' Emulació i que la sensació sigui més fluida.

Exemples d'Emulació:
  - Els emuladors de consoles, com N64 o PS1.
  Per exemple si volem un joc de Nintendo DS, ens podem descarregar l'emulador pel nostre mòbil.

Exemples de Virtualització:
  - Programa VirtualBox.
  Un cas d'ús per exemple, es tenir un Mac i voler fer servir el sistema operatiu Linux, ho podrem fer amb la màquina virtual.

S'ha buscat informació a les següents pàgines:
  - tremplin-numerique.org
  - computerhoy.com
  - estudiometadatos.es
  - executrain.com.mx

### Enunciat
Cerca les diferències entre les particions **GTP** i **MRB**. *Feu una taula comparativa*.

### Resposta

MBR | Mida Max  de particions i disc dur: 2TB	  | 4 particions primaries	 | Sector de dades sense seguretat |Nom de la partició : emmagatzemat a la partició | Per a la majoria de SO |


GPT |	Mida Max de particions i disc dur: 256TB |	Il.limitades( fins a 128 particions primaries amb Windows) | Sector de dades amb sistema de comprovació CRC 32 i copia de seguretat GUID | Nom de la partició: identificador únic GUID més un nom de caràcters(36) | UEFI (fa que la BIOS pugui detectar els dispositius i les partcions | Només en SO de 64 bits |

S'ha buscat informació en les següents pàgines:
  - profesionalreview.com
  - islabit.com

### Enunciat
Cerqueu informació sobre el procediment de **Fingerprint** del protocol SSH. Per a què serveix i quins problemes intenta solucionar.

### Resposta

És una advertència i la seva funció principal és identificar de manera inequívoca un servidor(per evitar que ens connectem a un servidor SSH maliciós).

Problemes que intenta solucionar:

- Si el fingerprint del servidor SSH al que ens volem connectar està emmagatzemat en ~/.ssh/known_hosts, vol dir que no és la primera vegada que ens connectem al servidor, i en principi vol dir que és un servidor conegut i que ens podem connectar sense problemes.
- Si el fingerprint no apareix al ~/.ssh/known_hosts, apareix el missatge d'adevertencia i aquí hem de tindre cura i procedir de la manera següent:
  - Si no és el primer cop que ens connectem al servidor i ens apareix el missatge, hem d'avortar la connexió. Comprovarem que l'administrador no hagi creat un parell de claus. Si és així ens podem connectar sense dubtes. En canvi, si l'administrador no ha modificat les claus, podem estar rebent un atac 'man in the middle', i que el servidor on ens connectem sigui maliciós i ens vol robar les credencials i suplantar-nos la identitat.
  - Si apareix el missatge i és el primer cop que ens connectem, no ens hem d'amoïnar i tan sols hem de comprovar que el fingerprint de l'advertència correspongui amb el fingerprint del servidor SSH.
  
  S'ha buscat informació:
   - geekland.eu

## Part pràctica: Instal·lar un paquet 

### Enunciat
La majoria de les distribucions UNIX o Linux gaudeixen de repositoris estàndard que inclouen la majoria del programari que necessitareu per executar al vostre servidor o sistema d'escriptori basat en UNIX o Linux. Si falta algun paquet, és molt probable que trobeu un repositori que podeu afegir, de manera que la instal·lació es pugui gestionar amb el gestor de paquets integrat. Això s'ha de considerar una bona pràctica. Per què? Perquè és important per a la integritat de la plataforma assegurar-se que el gestor de paquets coneix el programari instal·lat. Quan aquest és el cas, els paquets es poden actualitzar fàcilment (per solucionar vulnerabilitats i similars). Un altre motiu per instal·lar des dels dipòsits és que les dependències es compleixen fàcilment. 

La vostra tasca és investigar el seu funcionament a NetBSD i indicar els passos per instal·lar el paquet, **vim** a *bsdlab*. 

### Resposta

Amb pkgsrc podem afegir, eliminar i gestionar fàcilment el programari del nostre sistema. Pkgsrc és bàsicament un conjunt de fitxers, agrupats per categories, que contenen informació per instal·lar el programari que hem seleccionat. 
Primer de tot hem buscat la manera d'instal·lar el repositori PKGSRC, que la mateixa pàgina de NetBSD trobes una guia. Per poder instal·lar-lo comprovarem que estem connectats al directori root i a continuació amb les següents comandes instalarem el PKGSRC:

'# PKG_PATH="http://cdn.NetBSD.org/pub/pkgsrc/packages/NetBSD/$(uname -p)/$(uname -r|cut -f '1 2' -d.)/All/"'

'# export PKG_PATH'

'# pkg_add pkgin'

A continuació introduïnt la comanda '# pkgin install zsh nginx-1.19.6 vim' intal·les VIM a NetBSD i amb la comanda '# pkgin upgrade' mantens el repositori de PKG actualitzat.


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
Es pot fer amb la següent comanda: alias la = " ls - la "

## Part pràctica: Problema de l'any 2038 

### Enunciat
Com us he explicat a classe els sistemes UNIX sofreixen d'un problema amb les dates causat: ```time_t``` emmagatzema el temps com un nombre enter signat de 32 bits. Per tant, únicament pot representar enters entre -(231) i 231 -1, per tant l'última hora que es pot codificar correctament és 231 - 1 segons després de l'època UNIX (03:14:07 UTC el 19 de gener de 2038). Intentar augmentar al segon següent (03:14:08) farà que l'enter es desbordi, establint el seu valor a -(231), que els sistemes interpretaran com a 231 segons abans de l'època (20:45:52 UTC el 13 de desembre de 1901).

La vostra tasca és obtenir una prova del delicte en el vostre sistema **bsdlad**. Heu de demostrar si aquest afer existeix o no en la vostra instal·lació actual. Heu d'indicar els passos a realitzar per demostrar-ho.

### Resposta
El problema diu que el (03:14:07 UTC el 19 de gener de 2038) és l'últim dia que pot comptar. Llavors si arriba aquesta data, seria (20:45:52 UTC el 13 de desembre de 1901).

A UNIX podem comprovar amb la comanda 'date -d "..." quin dia serà en el futur o quin dia va ser en el passat, per exemple si introduïm 'date -d "+5 days" Wed Sep 28 02:55:47 UTC 2022' ens diu quin dia serà d'aquí 5 dies.
Nosaltres hem comprovat si el nostre sistema passa del 19 de gener de 2038, comptant 16 anys, que serà tal dia com avui 23 de setembre.

localhost# date -d "16 years"
Thu Sep 23 02:59:07 UTC 2038

I com podem demostrar, aquest problema no existeix al nostre sistema.

Una altre forma de demostrar que aquest problema no existeix en el nostre sistema és la següent:
Creem un programa en C amb el següent codi:
#include<stdio.h>
#include<time.h>

int main(){
  time_t t;
  printf("El tamany de l'estructura de dades és de %ld bytes, que son %d bits", sizeof(t), sizeof(t)*8);
  return 0;
}

Amb aquest programa, ens mostraria per pantalla el següent:

"El tamany de l'estructura de dades és de 8 bytes, que són 64 bits".

Per tant, el problema de l'any 2038 no existeix en el nostre ordinador, ja que els ordinadors actuals tenen més bits.


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
1. per crear els directoris a *home* primer donem permis al Usuari per crear directoris amb la comanda 'chown -R *USUARI* /home'

A continuació amb la comanda 'ls -la' comprovem que l'usuari ja es el propietari del home i podrem afegir directoris.

Amb la comnda 'mkdir' creem els directoris 'week0/teoria/, week0/laboratori/, week0/handson, code/, activities/', dins del directori 'home/'.

I amb la comanda 'touch' creem els arxius 'notes.md' dins del directori 'week0' i l'arxiu 'README.md' al directori 'activities/'.

2. Després d'haber fet la configuració per poder connectar-nos al servidor local SFTP, ens movem per aquest amb les mateixes comandes que utilitzem al servidor remot de la màquina virtual, cd entrar a un directori, ls per veure que hi ha dins del directori, etc. però amb la diferència que hem d'afegir 'l' davant per poder diferenciar el local del remot. Exemple, per accedir a un directori escriure lcd, per veure que hi ha al directori lls, per veure en quin directori ens trobem lpwd...
Llavors fent servir les comandes per entrar als directoris locals on tenim els arxius, amb la comanda 'put localFile' copiem aquest arxiu al sistema remot.
Un cop tenim els arxius al sistema remot, amb la comanda 'mv file directori' movem l'arxiu 'file' al directori que hem escollit.

3. Creem els arxius notes.md (buit) i template.md (escribint el contingut amb VIM) utilitzant la comanda 'touch notes.md'.
Per moure el contingut de l'arxiu template.md a l'arxiu notes.md fem servir la comanda 'cp template.md notes.md'.

4. Per veure les 3 primeres línies de l'arxiu template.md utilitzem la comanda 'head' afegint -3 per veure només les 3 primeres línies:

"localhost$ head -3 template.md
*# Week 0

*## A"

I per veure les 2 últimes línies utilitzem la comanda 'tail' afegint un -2:

"localhost$ tail -2 template.md

*## C"

5. Fem servir la comanda cp inicialment.
Tenim per posar ara primerament cp -R passwd */home/joan

6. Farem servir la comanda chflags hidden /.pass i ja no es mostrarà el fitxer.

7. chmod a+rwx */code/ //La a el que fa és dir que tots els usuaris els hi dones el permís.

8. $ tar -cvf /home/backup.tar.gz2 /home/joan

9. Descarregueu per *sftp* el fitxer *backup.tar.gz2* a la vostra màquina real.

10.La comanda que hem d'evitar a tota costa és rm -rf.
La que farem servir serà rm -i *
Aquesta comanda el que farà serà eliminar tots els fitxers preguntant un per un si el volem eliminar. D'aquesta manera el programa evitarà que eliminem alguna cosa sense voler.
