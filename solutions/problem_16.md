# Probleme 16 : Michel astique sa voiture (coefficient 16)

## Enonce

En astiquant sa voiture dans son garage, Michel decouvre une planche avec huit clous places comme sur le dessin et un elastique tendu entre ces clous tel que :
- l'elastique touche chaque clou une unique fois,
- l'elastique ne se croise pas lui-meme.

**Question :** De combien de facons differentes l'elastique peut-il ainsi etre tendu ?

Par exemple, avec quatre clous places comme dans l'enonce, il n'y a que trois possibilites.

---

## Solution

### Modelisation du probleme

L'elastique forme une **boucle fermee** (polygone) qui passe par chacun des 8 clous exactement une fois et ne se croise pas. On cherche donc le nombre de **polygones simples** (non auto-intersectants) dont les sommets sont exactement les 8 clous donnes.

Deux configurations sont identiques si elles relient les memes paires de clous consecutifs, independamment du sens de parcours ou du point de depart sur la boucle.

### Extraction des positions des clous

A partir de l'image fournie (question16.png), les positions des 8 clous ont ete extraites par analyse d'image (detection des centroïdes des points noirs). En utilisant les coordonnees en pixels :

| Clou | Position (x, y) | Description |
|------|-----------------|-------------|
| P0   | (463, 82)       | Haut, centre-droit |
| P1   | (136, 188)      | Haut gauche |
| P2   | (262, 320)      | Milieu, gauche du centre |
| P3   | (372, 360)      | Centre |
| P4   | (665, 361)      | Droite |
| P5   | (262, 401)      | Milieu, sous P2 |
| P6   | (136, 532)      | Bas gauche |
| P7   | (463, 638)      | Bas centre |

### Analyse geometrique

- **Enveloppe convexe :** 5 des 8 points sont sur l'enveloppe convexe (P0, P1, P4, P6, P7).
- **Points interieurs :** 3 points sont a l'interieur de l'enveloppe convexe (P2, P3, P5).

Le fait que 3 points soient interieurs genere un grand nombre de polygones simples possibles, car il y a beaucoup de facons de "tisser" le chemin a travers les points interieurs sans croisement.

### Verification de l'exemple a 4 clous

Avec 4 clous dont l'un est a l'interieur du triangle forme par les trois autres, il existe exactement **(4-1)!/2 = 3** cycles hamiltoniens, et les 3 sont des polygones simples. Ceci confirme le resultat de l'enonce (3 possibilites).

### Methode de denombrement

Pour 8 points, le nombre total de cycles hamiltoniens distincts (a rotation et reflexion pres) est :

**(8-1)!/2 = 5040/2 = 2520**

Pour chaque cycle, on verifie si le polygone correspondant est simple en testant l'absence d'intersection entre toute paire d'aretes non adjacentes. Le test d'intersection de deux segments utilise le critere d'orientation (produit vectoriel / signe du determinant).

**Algorithme :**
1. Fixer le clou P0 comme point de depart.
2. Enumerer toutes les permutations des 7 autres clous.
3. Pour eviter le double comptage (sens horaire et anti-horaire), ne compter que les cycles ou le deuxieme clou a un indice inferieur au dernier.
4. Pour chaque cycle candidat, verifier que le polygone est simple (aucune paire d'aretes non adjacentes ne se croise).

### Verification de robustesse

Le resultat a ete verifie de plusieurs facons :
- **Coordonnees entieres** (multiplication par 10) : meme resultat.
- **Perturbations aleatoires** des coordonnees (+-5 pixels, 5 essais) : meme resultat a chaque fois.
- **Analyse des cas limites** : aucune paire de segments n'est proche d'une intersection marginale ; toutes les decisions de croisement sont bien separees.

---

## Reponse

**71**

L'elastique peut etre tendu de **71** facons differentes.
