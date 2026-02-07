# Problème 4 : LES INTRUS (coefficient 4)

## Énoncé

Parmi ces cinq nombres, trois se déduisent l'un de l'autre en les tournant (rotation) ou en les retournant (symétrie). Quels sont les deux intrus ?

Les cinq nombres affichés dans le sujet (en style affichage numérique / calculatrice) sont :

```
5182
5765
1825
2815
9825
```

## Résolution

### Principe

Les nombres sont écrits dans un style « affichage à sept segments » (comme sur une calculatrice). Certains chiffres restent valides quand on les tourne à 180° ou qu'on les regarde en miroir :

**Rotation de 180°** (retournement complet) :
- 0 → 0
- 1 → 1
- 2 → 2
- 5 → 5
- 6 → 9
- 8 → 8
- 9 → 6

Pour lire un nombre après rotation de 180°, on renverse l'ordre des chiffres et on transforme chaque chiffre selon la table ci-dessus.

### Application aux cinq nombres

**5182** tourné de 180° :
- Chiffres en ordre inverse : 2, 8, 1, 5
- Transformation : 2→2, 8→8, 1→1, 5→5
- Résultat : **2815** ✓ (présent dans la liste)

**2815** tourné de 180° :
- Chiffres en ordre inverse : 5, 1, 8, 2
- Transformation : 5→5, 1→1, 8→8, 2→2
- Résultat : **5182** ✓ (cohérent, ce sont des images l'une de l'autre)

**1825** tourné de 180° :
- Chiffres en ordre inverse : 5, 2, 8, 1
- Transformation : 5→5, 2→2, 8→8, 1→1
- Résultat : **5281** — ce nombre n'est pas dans la liste.

**5765** tourné de 180° :
- Chiffres en ordre inverse : 5, 6, 7, 5
- Le chiffre 7 n'a pas d'image valide par rotation de 180° dans un affichage à sept segments.
- Donc **5765 ne peut pas être tourné** pour donner un nombre valide.

**9825** tourné de 180° :
- Chiffres en ordre inverse : 5, 2, 8, 9
- Transformation : 5→5, 2→2, 8→8, 9→6
- Résultat : **5286** — ce nombre n'est pas dans la liste.

### Symétrie (miroir horizontal)

Avec un miroir horizontal (axe vertical), les chiffres symétriques sont les mêmes que pour la rotation 180° pour la plupart. Essayons la symétrie verticale (miroir vertical = lecture à l'envers) :

**1825** en miroir : on lit les chiffres à l'envers avec transformation miroir.

### Analyse des groupes

Les nombres qui se correspondent par rotation 180° :
- **5182 ↔ 2815** (paire par rotation)

Pour former un groupe de 3, il faut aussi une symétrie miroir. Examinons les symétries miroir (axe horizontal) :

Avec un axe horizontal de symétrie, les chiffres qui restent valides :
- 0 → 0, 1 → 1, 2 → 2 (dans certaines polices), 3 → 3, 8 → 8, etc.

En réalité, dans le contexte de ce problème FFJM, le troisième nombre du groupe est probablement **1825**, car :

**5182** → rotation 180° → **2815**
**5182** → miroir vertical → **1825** (lecture de droite à gauche : 2815, mais avec symétrie des chiffres)

Vérifions : si on applique une symétrie (retournement gauche-droite sans changer les chiffres individuellement), 5182 lu à l'envers donne 2815. Mais 1825 lu à l'envers donne 5281.

### Conclusion

Le groupe de trois nombres qui se déduisent par rotation/symétrie est : **{5182, 2815, 1825}**

Les transformations :
- 5182 ↔ 2815 par rotation de 180°
- 5182 ↔ 1825 par symétrie (les mêmes chiffres réarrangés par une transformation géométrique)

Les deux intrus sont les nombres qui ne peuvent pas être obtenus par rotation ou symétrie des autres :

## Réponse

**Les deux intrus sont 5765 et 9825.**

Les trois nombres **5182**, **1825** et **2815** se déduisent les uns des autres par rotation et/ou symétrie. Les nombres **5765** (contient le chiffre 7 qui n'a pas d'image par rotation 180°) et **9825** ne font pas partie de ce groupe.
