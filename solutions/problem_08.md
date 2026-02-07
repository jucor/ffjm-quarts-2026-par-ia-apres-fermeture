# Probleme 8 : LE TRAIN MEXICAIN (coefficient 8)

## Enonce

Dans le jeu "Le train mexicain", on utilise des pieces de dominos toutes differentes. Chaque demi-domino porte un nombre de points allant de 0 a 10.

Max utilise uniquement les dominos dont au moins un des deux cotes porte un nombre de points egal a 0, 2 ou 6. Il veut construire la plus longue suite possible de dominos, en suivant la regle du jeu de dominos : deux demi-dominos qui se touchent doivent porter le meme nombre de points.

**Quel est le plus grand nombre de dominos qu'il peut poser ?**

## Raisonnement

### Etape 1 : Inventaire des dominos disponibles

Dans un jeu complet avec des valeurs de 0 a 10, chaque domino est une paire (a, b) avec a <= b. Max ne garde que les dominos dont **au moins un cote** vaut 0, 2 ou 6.

**Dominos contenant 0 :**
(0,0), (0,1), (0,2), (0,3), (0,4), (0,5), (0,6), (0,7), (0,8), (0,9), (0,10) --> **11 dominos**

**Dominos contenant 2 mais pas 0 :**
(1,2), (2,2), (2,3), (2,4), (2,5), (2,6), (2,7), (2,8), (2,9), (2,10) --> **10 dominos**

**Dominos contenant 6 mais ni 0 ni 2 :**
(1,6), (3,6), (4,6), (5,6), (6,6), (6,7), (6,8), (6,9), (6,10) --> **9 dominos**

**Verification par inclusion-exclusion :** si A_v designe l'ensemble des dominos portant la valeur v, alors |A_0| = |A_2| = |A_6| = 11, et les intersections deux a deux sont |A_0 inter A_2| = 1 (le domino (0,2)), |A_0 inter A_6| = 1 (le (0,6)), |A_2 inter A_6| = 1 (le (2,6)), et l'intersection triple est vide (un domino n'a que 2 faces). D'ou : 11 + 11 + 11 - 1 - 1 - 1 + 0 = **30 dominos au total**.

### Etape 2 : Modelisation par un graphe

On modelise le probleme en theorie des graphes :
- **Sommets** : les valeurs 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 (11 sommets).
- **Aretes** : chaque domino (a, b) est une arete entre les sommets a et b. Un double (a, a) est une boucle au sommet a.

Construire une suite de dominos en respectant la regle revient a trouver une **chaine** (trail) dans ce graphe, c'est-a-dire un parcours d'aretes sans repeter aucune arete. Maximiser le nombre de dominos poses equivaut a trouver la chaine la plus longue.

### Etape 3 : Calcul des degres des sommets

Le degre d'un sommet est le nombre de bouts d'aretes qui y sont rattaches. Une boucle (a, a) contribue 2 au degre de a.

| Sommet | Aretes incidentes | Degre | Parite |
|--------|-------------------|-------|--------|
| 0 | (0,0)[boucle], (0,1), (0,2), (0,3), (0,4), (0,5), (0,6), (0,7), (0,8), (0,9), (0,10) | 2 + 10 = 12 | pair |
| 1 | (0,1), (1,2), (1,6) | 3 | **impair** |
| 2 | (0,2), (1,2), (2,2)[boucle], (2,3), (2,4), (2,5), (2,6), (2,7), (2,8), (2,9), (2,10) | 2 + 10 = 12 | pair |
| 3 | (0,3), (2,3), (3,6) | 3 | **impair** |
| 4 | (0,4), (2,4), (4,6) | 3 | **impair** |
| 5 | (0,5), (2,5), (5,6) | 3 | **impair** |
| 6 | (0,6), (2,6), (1,6), (3,6), (4,6), (5,6), (6,6)[boucle], (6,7), (6,8), (6,9), (6,10) | 2 + 10 = 12 | pair |
| 7 | (0,7), (2,7), (6,7) | 3 | **impair** |
| 8 | (0,8), (2,8), (6,8) | 3 | **impair** |
| 9 | (0,9), (2,9), (6,9) | 3 | **impair** |
| 10 | (0,10), (2,10), (6,10) | 3 | **impair** |

**Verification :** somme des degres = 3 x 12 + 8 x 3 = 36 + 24 = 60 = 2 x 30. Correct (chaque arete contribue 2 a la somme).

**Sommets de degre impair : {1, 3, 4, 5, 7, 8, 9, 10} --> 8 sommets impairs.**

### Etape 4 : Condition pour une chaine eulerienne

Un theoreme classique de theorie des graphes (Euler) affirme que :
- Un graphe connexe admet un **chemin eulerien** (chaine utilisant toutes les aretes exactement une fois) si et seulement s'il possede **exactement 0 ou 2** sommets de degre impair.
- S'il y a 0 sommets impairs, on obtient un circuit (retour au depart) ; s'il y en a 2, on obtient un chemin ouvert entre ces deux sommets.

Notre graphe possede **8 sommets impairs**, donc on ne peut **pas** utiliser les 30 dominos en une seule chaine.

### Etape 5 : Nombre minimal d'aretes a retirer

Pour trouver la plus longue chaine, on cherche a retirer le **minimum d'aretes** du graphe pour obtenir un sous-graphe connexe ayant au plus 2 sommets de degre impair. La longueur de la chaine sera alors 30 moins le nombre d'aretes retirees.

**Observation structurelle cle :** chacun des 8 sommets impairs (1, 3, 4, 5, 7, 8, 9, 10) est relie exclusivement aux trois sommets pairs (0, 2, 6), qui forment les "hubs" du graphe. Il n'existe **aucune arete directe** entre deux sommets impairs.

Pour rendre un sommet impair pair, il faut retirer un nombre impair de ses aretes (1 ou 3). Le minimum est d'en retirer 1, laissant le sommet avec un degre de 2.

Cependant, retirer une arete entre un sommet impair v et un hub h :
- rend v pair (bien),
- mais change la parite de h (mal si h etait pair).

**Strategie optimale :** retirer les aretes **par paires** incidentes au meme hub. Si on retire deux aretes (h, v1) et (h, v2) du meme hub h, alors :
- v1 et v2 passent d'impairs a pairs (2 sommets corriges),
- h perd 2 en degre, donc sa parite ne change pas (reste pair).

Pour corriger 6 des 8 sommets impairs (en gardant 2 comme extremites du chemin), il faut **3 paires = 6 aretes retirees**, reparties equitablement entre les 3 hubs : 2 aretes retirees de chaque hub.

**On ne peut pas faire mieux que 6 aretes**, car :
- chaque arete retiree ne corrige qu'un seul sommet impair,
- il faut corriger 6 sommets,
- et la contrainte de parite sur les hubs impose de retirer un nombre pair d'aretes par hub.

### Etape 6 : Construction explicite

**Aretes retirees (6 dominos non utilises) :**

| Arete retiree | Hub concerne |
|---------------|-------------|
| (0, 3) | hub 0 |
| (0, 5) | hub 0 |
| (2, 4) | hub 2 |
| (2, 7) | hub 2 |
| (6, 8) | hub 6 |
| (6, 9) | hub 6 |

**Degres dans le sous-graphe restant (24 aretes) :**

| Sommet | Degre | Parite |
|--------|-------|--------|
| 0 | 10 | pair |
| 1 | 3 | **impair** (extremite) |
| 2 | 10 | pair |
| 3 | 2 | pair |
| 4 | 2 | pair |
| 5 | 2 | pair |
| 6 | 10 | pair |
| 7 | 2 | pair |
| 8 | 2 | pair |
| 9 | 2 | pair |
| 10 | 3 | **impair** (extremite) |

Le sous-graphe est connexe (chaque sommet reste relie a au moins 2 des hubs, et les hubs sont relies entre eux) et possede exactement 2 sommets impairs (1 et 10). Il admet donc un chemin eulerien de 1 a 10 utilisant les 24 aretes.

**Exemple de chaine de 24 dominos :**

```
(1|0) - (0|0) - (0|4) - (4|6) - (6|1) - (1|2) - (2|2) - (2|3) - (3|6) - (6|6) - (6|5) - (5|2) - (2|6) - (6|7) - (7|0) - (0|8) - (8|2) - (2|9) - (9|0) - (0|2) - (2|10) - (10|0) - (0|6) - (6|10)
```

Verification des raccordements : chaque paire de demi-dominos adjacents porte bien le meme nombre de points (1, 0, 0, 4, 6, 1, 2, 2, 3, 6, 6, 5, 2, 6, 7, 0, 8, 2, 9, 0, 2, 10, 0, 6, 10), et les 24 aretes du sous-graphe sont toutes utilisees exactement une fois.

## Reponse

$$\boxed{24}$$

**Le plus grand nombre de dominos que Max peut poser est 24.**
