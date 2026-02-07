# Probleme 13 : JETONS A RETOURNER (coefficient 13)

## Enonce

Un plateau 3x3 comporte neuf jetons qui sont blancs d'un cote et noirs de l'autre.
Le but du jeu est que tous les jetons aient leur face noire visible.
Un coup autorise consiste a retourner d'un seul coup trois jetons alignes :
sur la meme ligne, sur la meme colonne, ou sur la meme diagonale.

**Grille d'Amel :**

```
B B N
N B B
B N N
```

**Grille de Sofia :**

```
N B N
B N B
N B N
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

### Invariant fondamental

La matrice A du systeme (9 lignes x 8 colonnes sur GF(2)) est de **rang 7**, ce qui
signifie que l'espace noyau a gauche est de dimension 2. Il existe donc des contraintes
de compatibilite sur le vecteur cible.

**Invariant 1 (positions hors diagonale principale) :**
Les six positions (1,2), (1,3), (2,1), (2,3), (3,1), (3,2) -- c'est-a-dire toutes
les positions **sauf la diagonale principale** (1,1), (2,2), (3,3) -- verifient la
propriete suivante : chacun des 8 coups retourne un nombre **pair** de ces six positions.

Par consequent, **la parite du nombre de jetons blancs parmi ces 6 positions est un
invariant** : aucune combinaison de coups ne peut la modifier.

Pour atteindre la configuration tout-noir, il faut 0 jeton blanc parmi ces 6 positions
(parite paire). Donc, **si le nombre de jetons blancs parmi ces 6 positions est impair
au depart, le probleme est impossible**.

**Invariant 2 (les 4 coins) :**
De meme, les quatre coins (1,1), (1,3), (3,1), (3,3) sont tels que chaque coup en
retourne un nombre pair. La parite du nombre de jetons blancs aux coins est donc
aussi un invariant.

---

## Resolution pour Amel

### Configuration de depart

```
B B N       (1,1)=B  (1,2)=B  (1,3)=N
N B B       (2,1)=N  (2,2)=B  (2,3)=B
B N N       (3,1)=B  (3,2)=N  (3,3)=N
```

Vecteur cible (1 = blanc a retourner) :
t = (1, 1, 0, 0, 1, 1, 1, 0, 0)

### Verification de l'invariant 1

Positions hors diagonale principale : (1,2), (1,3), (2,1), (2,3), (3,1), (3,2).

Couleurs correspondantes : B, N, N, B, B, N.

Nombre de jetons blancs parmi ces 6 positions : **3** (impair).

Or, pour la configuration tout-noir, il faudrait **0** jeton blanc (pair).

**La parite est impaire au depart et devrait etre paire a l'arrivee : c'est impossible !**

### Verification exhaustive

On peut confirmer en testant les 2^8 = 256 combinaisons possibles de coups :
**aucune ne mene a la configuration tout-noir**.

### Conclusion pour Amel

**Il est impossible pour Amel d'atteindre la configuration tout-noir.**

**Reponse : 0**

---

## Resolution pour Sofia

### Configuration de depart

```
N B N       (1,1)=N  (1,2)=B  (1,3)=N
B N B       (2,1)=B  (2,2)=N  (2,3)=B
N B N       (3,1)=N  (3,2)=B  (3,3)=N
```

Vecteur cible :
t = (0, 1, 0, 1, 0, 1, 0, 1, 0)

### Verification des invariants

**Invariant 1 :** Positions hors diagonale : (1,2)=B, (1,3)=N, (2,1)=B, (2,3)=B, (3,1)=N, (3,2)=B.
Nombre de blancs : **4** (pair). Compatible avec 0 (pair). OK.

**Invariant 2 :** Coins : (1,1)=N, (1,3)=N, (3,1)=N, (3,3)=N.
Nombre de blancs : **0** (pair). Compatible. OK.

Les invariants sont satisfaits, donc une solution pourrait exister.

### Recherche de la solution optimale

**Peut-on resoudre en 1 coup ?** Aucun des 8 coups ne retourne exactement les 4 positions
blanches (1,2), (2,1), (2,3), (3,2). Chaque coup ne retourne que 3 positions, et il
faudrait retourner exactement 4 positions (les 4 bords) sans toucher aux 5 autres.
C'est impossible en un seul coup.

**Solution en 2 coups : L2 puis C2.**

**Coup 1 -- L2 (retourner la ligne 2) :** on retourne (2,1), (2,2), (2,3).

```
N B N              N B N
B N B   -- L2 -->  N B N
N B N              N B N
```

- (2,1) : B -> N (bien)
- (2,2) : N -> B (temporairement blanc)
- (2,3) : B -> N (bien)

**Coup 2 -- C2 (retourner la colonne 2) :** on retourne (1,2), (2,2), (3,2).

```
N B N              N N N
N B N   -- C2 -->  N N N
N B N              N N N
```

- (1,2) : B -> N (bien)
- (2,2) : B -> N (corrige)
- (3,2) : B -> N (bien)

**Tous les jetons sont maintenant noirs !**

### Verification exhaustive

L'enumeration des 256 combinaisons confirme qu'il existe exactement **2 solutions** :

| Nombre de coups | Coups |
|-----------------|-------|
| 2 | L2, C2 |
| 4 | L1, L3, C1, C3 |

La solution en 2 coups est l'unique solution optimale.

On peut aussi verifier la seconde solution (L1, L3, C1, C3 -- retourner les lignes 1 et 3 et les colonnes 1 et 3) : elle fonctionne mais necessite 4 coups.

### Conclusion pour Sofia

**Sofia peut atteindre la configuration tout-noir en 2 coups minimum (L2 et C2).**

**Reponse : 2**

---

## Reponse finale

| Joueuse | Minimum de coups | Explication |
|---------|-----------------|-------------|
| **Amel** | **0 (impossible)** | L'invariant de parite des positions hors diagonale principale est viole (3 blancs = impair) |
| **Sofia** | **2** | Solution : retourner la ligne 2 (L2) puis la colonne 2 (C2) |

**Nombre de solutions pour l'ensemble du probleme : 1** (il n'y a qu'une seule paire de reponses : Amel = 0, Sofia = 2).

La reponse au probleme est : **Amel 0, Sofia 2**.
