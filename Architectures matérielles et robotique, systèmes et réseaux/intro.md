--
voir ed curran.net
----
BLOC 3
==
###  Architectures matérielles, robotique, systèmes et réseaux
 Raymond Namyst
---
## Introduction amphi
- Reprise du référentiel
- explication du contenu

## Ordre des sous thèmes : 
- Système, arhi, réseaux, robotique
---
Jour 1
==
Mathieu

- diapo 16 - la structure en oignon impose bloque la communication au seul niveau inférieur (en direction du kernel), ne bloque pas les communications montantes (à partir du kernel)
- le noyau est un logiciel qui s'exécute en mode privilégié, mais ça n'est pas un super utilisateur
- Les apples système, sont des appels au système d'exploitation (couche en oignon)
---
## Les interfaces graphiques et fichiers
- C'est un programme qui permet d'afficher l'infomation et qui masque les appels systèmes. C'est pratique pour les manipulations isolées.
- sous linux, les extensions de fichiers sont utiles uniquement pour les utilisateurs.
--- 
Jour 2
==
## architecture système
Site pour émuler un processeur : 
http://dept-info.labri.fr/ENSEIGNEMENT/archi/js-y86/index.html

Langage assembleur : 

- Met des valeurs 5 et 10 dans les registres
- Sauvegarde la valeur dans %edx
- Fait l'addition
  
### addition

    .pos 0
        irmovl 5,%eax
        irmovl 10,%ecx
        rrmovl %ecx,%edx
        addl %eax,%ecx
        halt

### Multiplication infinie

    .pos 0
        irmovl 7,%ebx
        irmovl 5,%eax
        rrmovl %eax,%ecx    

    boucle:    
        addl %ecx,%eax
        jmp boucle
        halt
    
---
### Multiplication  définie

L'objectif est de multiplier 7 à chaque tour de boucle (5 fois)
On met 7 dans le reg
On met 0 dans ecx
On met le cpteur de boulce dans eax
On mémorise 7 dasn ebx (pour l'additionner à chq tour de boucle)
Dans la boucle on fait l'addition et on décrémente eax
Le résultat de l'opération modifie le ZF qui permet de faire la boucle (car elle dépend du ZF)

    .pos 0
        irmovl 7,%ebx
        xorl %ecx,%ecx
        mrmovl N,%eax
        rrmovl %ebx,%ecx    
    boucle:    
        addl %ecx,%ebx
        isubl 1,%eax
        jne boucle
        halt
        
    .align 4
    N:  .long 5    

    
----
Réseau
==
Dans WireShark, dans la trame DNS s'il y a 2 ligne similaire => ipv4 et ipV6

arp : vérifie l'existance d'une IP sur le réseau
nslookup : vérifie l'adresse IP
netstat : vérifie les machines connectées sur le poste

## Le routage
pour vérifier si l'on est dans le même réseau (routeur), on fait un et entre les 2 adresses IP sur le netID. 

## biliothèque python pour le réseau
utilisation au cremi à l'aide de scappy3
