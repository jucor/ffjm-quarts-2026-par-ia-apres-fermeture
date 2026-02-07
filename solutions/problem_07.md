# Probleme 7 : A LA CHASSE AUX OEUFS (coefficient 7)

## Enonce

Claude possede 4 poules et il ramasse les oeufs chaque soir.

- La premiere pond un oeuf tous les jours.
- La deuxieme pond un oeuf tous les deux jours.
- La troisieme pond un oeuf tous les 3 jours.
- La quatrieme pond un oeuf tous les 4 jours.

Claude a pu ramasser 4 oeufs pondus le jour meme le 1er octobre.
Quel jour pourra-t-il de nouveau ramasser 4 oeufs ?

## Raisonnement

### Donnees du probleme

Le 1er octobre, les 4 poules pondent toutes un oeuf. A partir de cette date, chaque poule continue de pondre selon son propre cycle :

| Poule | Frequence de ponte          |
|-------|-----------------------------|
| 1     | tous les jours (cycle de 1) |
| 2     | tous les 2 jours (cycle de 2) |
| 3     | tous les 3 jours (cycle de 3) |
| 4     | tous les 4 jours (cycle de 4) |

### Jours de ponte de chaque poule

Si l'on note le 1er octobre comme le jour 0, chaque poule pond aux jours suivants :

- **Poule 1** : jours 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, **12**, ... (tous les jours)
- **Poule 2** : jours 0, 2, 4, 6, 8, 10, **12**, 14, ... (les jours pairs)
- **Poule 3** : jours 0, 3, 6, 9, **12**, 15, ... (les multiples de 3)
- **Poule 4** : jours 0, 4, 8, **12**, 16, ... (les multiples de 4)

### Recherche du prochain jour commun

On cherche le plus petit nombre de jours **strictement positif** ou les 4 poules pondent simultanement. Cela revient a trouver le plus petit commun multiple (PPCM) des quatre cycles.

Calculons le PPCM de 1, 2, 3 et 4 :

- PPCM(1, 2) = 2
- PPCM(2, 3) = 6
- PPCM(6, 4) = 12

Donc : **PPCM(1, 2, 3, 4) = 12**

### Verification

Le jour 12 apres le 1er octobre :

- Poule 1 : 12 est un multiple de 1 -> elle pond.
- Poule 2 : 12 est un multiple de 2 -> elle pond.
- Poule 3 : 12 est un multiple de 3 -> elle pond.
- Poule 4 : 12 est un multiple de 4 -> elle pond.

Les 4 poules pondent bien toutes le meme jour. Aucun jour entre le 1er et le 13 octobre ne reunit les 4 poules (on peut le verifier dans le tableau ci-dessus : aucun autre jour entre 1 et 11 n'est a la fois multiple de 2, de 3 et de 4).

### Calcul de la date

Le 1er octobre + 12 jours = **13 octobre**.

## Reponse

> **Claude pourra de nouveau ramasser 4 oeufs le 13 octobre.**
