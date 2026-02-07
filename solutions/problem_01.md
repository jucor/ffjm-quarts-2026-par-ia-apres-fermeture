# Probleme 1 : LE DEFI DU CHOCOLATIER (coefficient 1)

## Enonce

Un chocolatier prepare une boite de chocolats pour ses clients. Il utilise une boite carree de 7 cm de cote, dans laquelle il souhaite ranger des chocolats carres de 2 cm de cote.
Tous les chocolats doivent etre places a plat, sans empilement, et doivent tenir entierement dans la boite.
Quel est le nombre maximal de chocolats qu'il peut ranger dans cette boite ?

## Resolution

### Approche par alignement sur une grille

La boite a un cote de 7 cm et chaque chocolat a un cote de 2 cm.

En disposant les chocolats alignes avec les bords de la boite :

- Nombre de chocolats par rangee : 7 / 2 = 3,5 donc **3 chocolats** par rangee (3 x 2 = 6 cm, il reste 1 cm)
- Nombre de rangees : 7 / 2 = 3,5 donc **3 rangees** (3 x 2 = 6 cm, il reste 1 cm)

Total avec cette disposition : 3 x 3 = **9 chocolats**, occupant un carre de 6 cm x 6 cm.

Il reste alors une bande de 1 cm de large sur le cote droit et une bande de 1 cm de large en haut (formant un "L"). Ces bandes sont trop etroites pour accueillir un chocolat supplementaire (un chocolat mesure au minimum 2 cm dans toute direction).

### Peut-on faire mieux en inclinant des chocolats ?

Un carre de 2 cm de cote, pivote de 45 degres, s'inscrit dans un carre de cote 2 x sqrt(2) ≈ 2,83 cm. On pourrait imaginer placer un chocolat incline dans l'espace restant.

Cependant, les bandes restantes ne mesurent que 1 cm de large, ce qui est insuffisant meme pour un chocolat incline (qui necessite au minimum 2 cm dans toute direction, quelle que soit son orientation).

### Peut-on reorganiser l'ensemble pour creer plus de place ?

Examinons s'il est possible de disposer 10 chocolats ou plus dans la boite, en utilisant un melange de chocolats alignes et de chocolats inclines.

Ce probleme correspond a un probleme classique d'empaquetage : placer des carres unitaires dans un carre de cote donne. En posant l'unite egale au cote du chocolat (2 cm), notre boite a un cote de 7/2 = 3,5 unites.

Or, il est mathematiquement demontre que pour empaqueter 10 carres unitaires dans un carre, le cote minimal necessaire est de 3 + 1/sqrt(2) ≈ 3,707 unites. Puisque 3,5 < 3,707, il est **impossible** de placer 10 chocolats dans la boite, quelle que soit la disposition choisie (avec ou sans rotation).

### Verification par l'aire

- Aire de la boite : 7 x 7 = 49 cm²
- Aire d'un chocolat : 2 x 2 = 4 cm²
- Nombre maximal theorique (borne superieure par l'aire) : 49 / 4 = 12,25 donc au plus 12 chocolats

Cette borne n'est pas atteinte en pratique. Elle nous indique seulement que la reponse est au plus 12, mais l'analyse geometrique ci-dessus montre que 10 est deja impossible.

### Configuration optimale

La disposition optimale est une grille de 3 x 3 chocolats alignes avec les bords de la boite :

```
+---------------------------------------+
|  +----+  +----+  +----+  |            |
|  |    |  |    |  |    |  |            |
|  +----+  +----+  +----+  |  1 cm      |
|  +----+  +----+  +----+  |            |
|  |    |  |    |  |    |  |            |
|  +----+  +----+  +----+  |            |
|  +----+  +----+  +----+  |            |
|  |    |  |    |  |    |  |            |
|  +----+  +----+  +----+  |            |
|           1 cm            |            |
+---------------------------------------+
       6 cm                    1 cm
                  7 cm
```

Les 9 chocolats occupent 6 cm x 6 cm. Les bandes restantes de 1 cm (a droite et en bas) sont trop etroites pour tout chocolat supplementaire.

## Reponse

**Le nombre maximal de chocolats que le chocolatier peut ranger dans la boite est 9**, disposes en 3 rangees de 3 chocolats alignes avec les bords de la boite.
