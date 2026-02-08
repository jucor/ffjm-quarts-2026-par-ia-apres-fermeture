# Probleme 8 : LE TRAIN MEXICAIN (coefficient 8)

## Enonce

Dans le jeu "Le train mexicain", on utilise des pieces de dominos toutes differentes. Chaque demi-domino porte un nombre de points allant de 0 a 10.

Max utilise uniquement les dominos dont au moins un des deux cotes porte un nombre de points egal a 0, 2 ou 6. Il veut construire la plus longue suite possible de dominos, en suivant la regle du jeu de dominos : deux demi-dominos qui se touchent doivent porter le meme nombre de points.

**Quel est le plus grand nombre de dominos qu'il peut poser ?**

## Raisonnement

### Etape 1 : Lister tous les dominos disponibles

Max garde uniquement les dominos qui ont **au moins un cote egal a 0, 2 ou 6**. Listons-les tous.

**Dominos avec un 0 :**
(0|0), (0|1), (0|2), (0|3), (0|4), (0|5), (0|6), (0|7), (0|8), (0|9), (0|10) --> **11 dominos**

**Dominos avec un 2, pas encore comptes :**
(1|2), (2|2), (2|3), (2|4), (2|5), (2|6), (2|7), (2|8), (2|9), (2|10) --> **10 dominos**

**Dominos avec un 6, pas encore comptes :**
(1|6), (3|6), (4|6), (5|6), (6|6), (6|7), (6|8), (6|9), (6|10) --> **9 dominos**

**Total : 11 + 10 + 9 = 30 dominos.**

### Etape 2 : La regle des paires dans une chaine de dominos

Avant de chercher la plus longue chaine, il faut comprendre une regle importante.

Regardons un petit exemple de chaine :

```
[2|5] [5|0] [0|3]
```

Observons le nombre 5 : il apparait au milieu de la chaine, une fois a droite du premier domino et une fois a gauche du deuxieme. Il apparait donc **2 fois** (un nombre pair). C'est pareil pour le 0 qui apparait aussi 2 fois au milieu.

En revanche, le 2 (tout a gauche) et le 3 (tout a droite) n'apparaissent qu'**une seule fois** chacun.

Prenons un exemple plus long :

```
[1|0] [0|4] [4|2] [2|0] [0|6]
```

Ici, le 0 apparait **4 fois** au milieu (un nombre pair). Le 4 et le 2 apparaissent **2 fois** chacun (pair aussi). Seuls le 1 et le 6, aux deux bouts de la chaine, apparaissent **1 fois** (impair).

**La regle :** dans une chaine de dominos, chaque nombre qui se retrouve au milieu de la chaine doit apparaitre un nombre **pair** de fois sur les demi-dominos (il "entre" et il "sort", toujours par paires). Seuls les nombres places aux deux **extremites** (le tout premier et le tout dernier de la chaine) peuvent apparaitre un nombre **impair** de fois.

Comme une chaine n'a que **2 bouts**, on peut avoir au maximum **2 nombres** qui apparaissent un nombre impair de fois.

### Etape 3 : Compter les apparitions de chaque nombre

Comptons combien de fois chaque nombre apparait sur l'ensemble des demi-dominos de Max. Attention : un double comme (0|0) fait apparaitre le 0 **deux** fois.

**Les nombres 0, 2 et 6** (les "numeros centraux") :

- **Le 0** apparait sur : (0|0) deux fois, (0|1), (0|2), (0|3), (0|4), (0|5), (0|6), (0|7), (0|8), (0|9), (0|10).
  Total : 2 + 10 = **12 apparitions** (nombre pair).

- **Le 2** apparait sur : (2|2) deux fois, (0|2), (1|2), (2|3), (2|4), (2|5), (2|6), (2|7), (2|8), (2|9), (2|10).
  Total : 2 + 10 = **12 apparitions** (nombre pair).

- **Le 6** apparait sur : (6|6) deux fois, (0|6), (2|6), (1|6), (3|6), (4|6), (5|6), (6|7), (6|8), (6|9), (6|10).
  Total : 2 + 10 = **12 apparitions** (nombre pair).

**Les nombres 1, 3, 4, 5, 7, 8, 9, 10** (les "numeros satellites") :

Chacun de ces nombres apparait sur exactement **3 dominos** : un domino avec le 0, un avec le 2, et un avec le 6.

Par exemple, le nombre 4 apparait sur (0|4), (2|4) et (4|6), donc **3 apparitions** (nombre impair).

C'est pareil pour les 7 autres : 1, 3, 5, 7, 8, 9 et 10 apparaissent chacun exactement **3 fois** (nombre impair).

**Bilan :** les nombres 0, 2 et 6 apparaissent un nombre pair de fois (12), mais les **8 nombres** 1, 3, 4, 5, 7, 8, 9 et 10 apparaissent chacun un nombre **impair** de fois (3).

### Etape 4 : Pourquoi on ne peut pas utiliser les 30 dominos

D'apres la regle des paires (etape 2), dans une chaine de dominos, au maximum **2 nombres** peuvent avoir un nombre impair d'apparitions (ceux aux deux bouts).

Or, nous avons **8 nombres** avec un nombre impair d'apparitions. C'est beaucoup trop ! Il est donc **impossible** de placer les 30 dominos en une seule chaine.

Il faut retirer des dominos pour reduire le nombre de "nombres impairs" de 8 a 2.

### Etape 5 : Combien de dominos retirer au minimum ?

Nous devons corriger **6** des 8 nombres impairs (en garder 2 pour les extremites de la chaine). Corriger un nombre, c'est le faire passer d'un nombre impair d'apparitions (3) a un nombre pair (2), en retirant un domino qui le contient.

**Observation importante :** regardons la liste des 30 dominos. Chacun des 8 nombres satellites (1, 3, 4, 5, 7, 8, 9, 10) n'apparait **que sur des dominos qui ont 0, 2 ou 6 de l'autre cote**. Par exemple, il n'y a pas de domino (1|3) ou (4|7) dans la selection de Max, car aucun de ces dominos n'a un cote egal a 0, 2 ou 6.

Donc, chaque domino qu'on retire a :
- d'un cote, un numero satellite (1, 3, 4, 5, 7, 8, 9 ou 10),
- de l'autre cote, un numero central (0, 2 ou 6).

Quand on retire un tel domino :
- Le numero satellite perd 1 apparition : il passe de 3 a 2 (pair, c'est ce qu'on veut).
- Mais le numero central perd aussi 1 apparition : il passe de 12 a 11 (impair, ce n'est pas bon !).

Si on retire un **deuxieme** domino du meme numero central, celui-ci passe de 11 a 10 (pair a nouveau, c'est repare !).

**Conclusion :** il faut retirer les dominos **par paires** au niveau de chaque numero central. En retirant 2 dominos relies au 0, 2 dominos relies au 2, et 2 dominos relies au 6, on corrige 6 numeros satellites tout en gardant les 3 numeros centraux avec un nombre pair d'apparitions.

**Total de dominos retires : 2 + 2 + 2 = 6.**

On ne peut pas faire mieux : chaque domino retire ne corrige qu'un seul numero satellite, il faut en corriger 6, et la contrainte de retirer un nombre pair par numero central nous impose exactement 6 retraits (la repartition 2 + 2 + 2 est la seule facon de partager 6 en trois nombres pairs non nuls ; les repartitions comme 0 + 2 + 4 fonctionneraient aussi mais ne donnent pas un meilleur resultat).

### Etape 6 : La plus longue chaine a donc 24 dominos

$$30 - 6 = 24$$

### Etape 7 : Exemple de chaine de 24 dominos

Choisissons de retirer les 6 dominos suivants :

- Du cote du 0 : on retire **(0|7)** et **(0|9)** --> les nombres 7 et 9 passent a 2 apparitions (pair).
- Du cote du 2 : on retire **(2|5)** et **(2|8)** --> les nombres 5 et 8 passent a 2 apparitions (pair).
- Du cote du 6 : on retire **(4|6)** et **(6|10)** --> les nombres 4 et 10 passent a 2 apparitions (pair).

Les nombres 1 et 3 restent a 3 apparitions (impair) : ils seront aux deux bouts de la chaine.

Voici une chaine de **24 dominos** qui utilise tous les dominos restants, en allant du 1 au 3 :

```
[1|0] [0|0] [0|2] [2|2] [2|1] [1|6] [6|6] [6|3] [3|0]
[0|4] [4|2] [2|6] [6|5] [5|0] [0|8] [8|6] [6|7] [7|2]
[2|10] [10|0] [0|6] [6|9] [9|2] [2|3]
```

**Verification :**

- Les nombres qui se touchent entre deux dominos voisins correspondent bien :
  1-**0**, **0**-0, 0-**2**, **2**-2, 2-**1**, **1**-6, 6-**6**, **6**-3, 3-**0**, **0**-4, 4-**2**, **2**-6, 6-**5**, **5**-0, 0-**8**, **8**-6, 6-**7**, **7**-2, 2-**10**, **10**-0, 0-**6**, **6**-9, 9-**2**, **2**-3.
- Les 24 dominos sont tous differents.
- Chaque domino a bien au moins un cote egal a 0, 2 ou 6.

## Reponse

**Le plus grand nombre de dominos que Max peut poser est 24.**
