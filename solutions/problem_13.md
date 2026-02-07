# Probleme 13 : JETONS A RETOURNER (coefficient 13)

## Enonce

Un plateau 3x3 comporte neuf jetons qui sont blancs d'un cote et noirs de l'autre.
Le but du jeu est que tous les jetons aient leur face noire visible.
Un coup autorise consiste a retourner d'un seul coup trois jetons alignes :
sur la meme ligne, sur la meme colonne, ou sur la meme diagonale.

**Grille d'Amel :**

```
N B N
B B N
B B B
```

**Grille de Sofia :**

```
N B N
B N B
B B B
```

(B = blanc, N = noir)

**Question :** Combien de coups au minimum faudra-t-il pour Amel et pour Sofia ?
Repondre 0 si c'est impossible.

---

## Analyse et modelisation

### Les 8 coups possibles

On numerote les positions (i,j) avec i = ligne, j = colonne, de 1 a 3.
Les 8 coups autorises sont :

| Coup | Positions retournees |
|------|---------------------|
| L1 (ligne 1) | (1,1), (1,2), (1,3) |
| L2 (ligne 2) | (2,1), (2,2), (2,3) |
| L3 (ligne 3) | (3,1), (3,2), (3,3) |
| C1 (colonne 1) | (1,1), (2,1), (3,1) |
| C2 (colonne 2) | (1,2), (2,2), (3,2) |
| C3 (colonne 3) | (1,3), (2,3), (3,3) |
| D1 (diagonale principale) | (1,1), (2,2), (3,3) |
| D2 (anti-diagonale) | (1,3), (2,2), (3,1) |

### Reduction du probleme

**Observation cle :** Chaque coup est une involution : l'effectuer deux fois revient a ne rien faire.
Par consequent, dans une solution optimale, chaque coup est utilise au plus une fois.
L'ordre des coups n'a pas d'importance (les retournements commutent).

On cherche donc un **sous-ensemble** des 8 coups tel que chaque jeton blanc soit
retourne un nombre impair de fois (pour devenir noir) et chaque jeton noir soit retourne
un nombre pair de fois (pour rester noir).

Ce probleme se formule naturellement comme un **systeme d'equations lineaires sur GF(2)**
(le corps a deux elements, 0 et 1), avec 9 equations (une par position) et 8 inconnues
(une par coup).

### Matrice du systeme

Soit x_L1, x_L2, x_L3, x_C1, x_C2, x_C3, x_D1, x_D2 dans {0, 1} les inconnues
(1 = on effectue le coup, 0 = on ne l'effectue pas).

Pour chaque position, on ecrit la contrainte :

| Position | Equation (somme mod 2 = cible) |
|----------|-------------------------------|
| (1,1) | x_L1 + x_C1 + x_D1 = t(1,1) |
| (1,2) | x_L1 + x_C2 = t(1,2) |
| (1,3) | x_L1 + x_C3 + x_D2 = t(1,3) |
| (2,1) | x_L2 + x_C1 = t(2,1) |
| (2,2) | x_L2 + x_C2 + x_D1 + x_D2 = t(2,2) |
| (2,3) | x_L2 + x_C3 = t(2,3) |
| (3,1) | x_L3 + x_C1 + x_D2 = t(3,1) |
| (3,2) | x_L3 + x_C2 = t(3,2) |
| (3,3) | x_L3 + x_C3 + x_D1 = t(3,3) |

ou t(i,j) = 1 si le jeton en (i,j) est blanc (a retourner), et t(i,j) = 0 s'il est noir.

### Invariant de parite fondamental

Considerons l'ensemble S des 6 positions situees **hors de l'anti-diagonale**, c'est-a-dire
toutes les positions sauf (1,3), (2,2) et (3,1) :

**S = {(1,1), (1,2), (2,1), (2,3), (3,2), (3,3)}**

Verifions que chaque coup retourne un nombre **pair** de positions dans S :

| Coup | Positions dans S retournees | Nombre |
|------|-----------------------------|--------|
| L1 | (1,1), (1,2) | 2 (pair) |
| L2 | (2,1), (2,3) | 2 (pair) |
| L3 | (3,2), (3,3) | 2 (pair) |
| C1 | (1,1), (2,1) | 2 (pair) |
| C2 | (1,2), (3,2) | 2 (pair) |
| C3 | (2,3), (3,3) | 2 (pair) |
| D1 | (1,1), (3,3) | 2 (pair) |
| D2 | (aucune) | 0 (pair) |

Puisque chaque coup retourne un nombre pair de jetons de S, **la parite du nombre de
jetons blancs dans S est un invariant** : aucune combinaison de coups ne peut la modifier.

Pour atteindre la configuration tout-noir, il faudrait 0 jeton blanc dans S (parite paire).
Donc, **si le nombre initial de jetons blancs dans S est impair, le probleme est impossible**.

---

## Resolution pour Amel

### Configuration de depart

```
N B N       (1,1)=N  (1,2)=B  (1,3)=N
B B N       (2,1)=B  (2,2)=B  (2,3)=N
B B B       (3,1)=B  (3,2)=B  (3,3)=B
```

Vecteur cible (1 = blanc a retourner) :
t = (0, 1, 0, 1, 1, 0, 1, 1, 1)

### Verification de l'invariant de parite

Positions dans S = {(1,1), (1,2), (2,1), (2,3), (3,2), (3,3)} :

| Position | Couleur |
|----------|---------|
| (1,1) | N |
| (1,2) | B |
| (2,1) | B |
| (2,3) | N |
| (3,2) | B |
| (3,3) | B |

Nombre de jetons blancs dans S : **4** (pair).

La cible est 0 (pair). La parite est compatible : **une solution pourrait exister**.

### Recherche de la solution optimale

**Peut-on resoudre en 0 coup ?** Non, il y a 6 jetons blancs a retourner.

**Peut-on resoudre en 1 coup ?** Chaque coup retourne exactement 3 positions.
Il faudrait que ces 3 positions soient exactement un sous-ensemble des 6 blancs,
et que retourner uniquement ces 3 suffise. Mais il resterait 3 blancs. Impossible.

**Peut-on resoudre en 2 coups ?** Deux coups retournent au plus 6 positions (et possiblement
moins si elles se chevauchent). L'enumeration exhaustive des C(8,2) = 28 paires confirme
qu'**aucune paire de coups ne resout le probleme**.

**Peut-on resoudre en 3 coups ?** L'enumeration exhaustive des C(8,3) = 56 triplets confirme
qu'**aucun triplet ne fonctionne non plus**.

**Solution en 4 coups :** L'enumeration trouve exactement **2 solutions en 4 coups** :

#### Solution 1 : L1, L3, C1, D2

**Coup 1 -- L1 (retourner la ligne 1) :** on retourne (1,1), (1,2), (1,3).

```
N B N              B N B
B B N   -- L1 -->  B B N
B B B              B B B
```

**Coup 2 -- L3 (retourner la ligne 3) :** on retourne (3,1), (3,2), (3,3).

```
B N B              B N B
B B N   -- L3 -->  B B N
B B B              N N N
```

**Coup 3 -- C1 (retourner la colonne 1) :** on retourne (1,1), (2,1), (3,1).

```
B N B              N N B
B B N   -- C1 -->  N B N
N N N              B N N
```

**Coup 4 -- D2 (retourner l'anti-diagonale) :** on retourne (1,3), (2,2), (3,1).

```
N N B              N N N
N B N   -- D2 -->  N N N
B N N              N N N
```

**Tous les jetons sont noirs !**

#### Solution 2 : L2, C2, C3, D2

**Coup 1 -- L2 (retourner la ligne 2) :** on retourne (2,1), (2,2), (2,3).

```
N B N              N B N
B B N   -- L2 -->  N N B
B B B              B B B
```

**Coup 2 -- C2 (retourner la colonne 2) :** on retourne (1,2), (2,2), (3,2).

```
N B N              N N N
N N B   -- C2 -->  N B B
B B B              B N B
```

**Coup 3 -- C3 (retourner la colonne 3) :** on retourne (1,3), (2,3), (3,3).

```
N N N              N N B
N B B   -- C3 -->  N B N
B N B              B N N
```

**Coup 4 -- D2 (retourner l'anti-diagonale) :** on retourne (1,3), (2,2), (3,1).

```
N N B              N N N
N B N   -- D2 -->  N N N
B N N              N N N
```

**Tous les jetons sont noirs !**

### Verification exhaustive

L'enumeration des 2^8 = 256 sous-ensembles de coups confirme :
- **0 solution** en 0, 1, 2 ou 3 coups
- **2 solutions** en 4 coups : {L1, L3, C1, D2} et {L2, C2, C3, D2}
- **0 solution** en 5, 6, 7 ou 8 coups

Le minimum est donc bien **4 coups**.

### Conclusion pour Amel

**Amel peut atteindre la configuration tout-noir en 4 coups minimum.**

**Reponse : 4**

---

## Resolution pour Sofia

### Configuration de depart

```
N B N       (1,1)=N  (1,2)=B  (1,3)=N
B N B       (2,1)=B  (2,2)=N  (2,3)=B
B B B       (3,1)=B  (3,2)=B  (3,3)=B
```

Vecteur cible (1 = blanc a retourner) :
t = (0, 1, 0, 1, 0, 1, 1, 1, 1)

### Verification de l'invariant de parite

Positions dans S = {(1,1), (1,2), (2,1), (2,3), (3,2), (3,3)} :

| Position | Couleur |
|----------|---------|
| (1,1) | N |
| (1,2) | B |
| (2,1) | B |
| (2,3) | B |
| (3,2) | B |
| (3,3) | B |

Nombre de jetons blancs dans S : **5** (impair).

La cible est 0 jetons blancs dans S (parite paire). Or la parite initiale est impaire.

**Puisque chaque coup retourne un nombre pair de positions dans S (comme demontre ci-dessus),
la parite du nombre de blancs dans S ne peut jamais changer. On part de 5 (impair) et on
devrait arriver a 0 (pair) : c'est impossible.**

### Preuve detaillee de l'invariant

Plus formellement, notons w(S) le nombre de jetons blancs dans l'ensemble
S = {(1,1), (1,2), (2,1), (2,3), (3,2), (3,3)}.

Apres n'importe quel coup, w(S) change de +/- k ou k est le nombre de positions de S
affectees par ce coup. Puisque k est toujours pair (voir tableau ci-dessus), w(S) mod 2
reste invariant.

- Etat initial : w(S) = 5, donc w(S) mod 2 = 1.
- Etat cible (tout noir) : w(S) = 0, donc w(S) mod 2 = 0.

Comme 1 != 0, aucune suite de coups ne peut transformer la grille de Sofia en tout-noir.

### Verification exhaustive

L'enumeration des 2^8 = 256 sous-ensembles de coups confirme qu'**aucun sous-ensemble
ne mene a la configuration tout-noir** pour la grille de Sofia.

### Conclusion pour Sofia

**Il est impossible pour Sofia d'atteindre la configuration tout-noir.**

**Reponse : 0**

---

## Reponse finale

| Joueuse | Minimum de coups | Explication |
|---------|-----------------|-------------|
| **Amel** | **4** | Deux solutions optimales : {L1, L3, C1, D2} ou {L2, C2, C3, D2} |
| **Sofia** | **0 (impossible)** | L'invariant de parite sur les 6 positions hors anti-diagonale est viole (5 blancs = impair, mais la cible exige une parite paire) |

**Reponse au probleme : Amel 4, Sofia 0.**
