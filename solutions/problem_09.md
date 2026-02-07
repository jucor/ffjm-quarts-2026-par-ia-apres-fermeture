# Probleme 9 : LES DATES D'ANNIE VERSAIRE (coefficient 9)

## Enonce

Annie a coche douze dates sur son calendrier 2025 :
1er janvier, 2 fevrier, 3 mars, 5 avril, 7 mai, ...
Ces dates sont formees, dans l'ordre, du nombre 1 suivi des nombres premiers et des mois consecutifs.
Quelle date sera cochee au mois de decembre ?

## Raisonnement

La suite des dates cochees par Annie est construite selon la regle suivante :

- Le jour du mois est donne par le nombre **1** suivi des **nombres premiers consecutifs** : 2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, ...
- Le mois avance d'un cran a chaque fois, de janvier a decembre.

On rappelle qu'un nombre premier est un entier admettant exactement deux diviseurs positifs (1 et lui-meme). En particulier, **1 n'est pas un nombre premier**.

### Construction mois par mois

| Mois       | Rang | Jour | Explication                        |
|------------|------|------|------------------------------------|
| Janvier    | --   | 1    | Le nombre 1 (point de depart, 1 n'est pas premier) |
| Fevrier    | 1er  | 2    | 1er nombre premier                 |
| Mars       | 2e   | 3    | 2e nombre premier                  |
| Avril      | 3e   | 5    | 3e nombre premier                  |
| Mai        | 4e   | 7    | 4e nombre premier                  |
| Juin       | 5e   | 11   | 5e nombre premier                  |
| Juillet    | 6e   | 13   | 6e nombre premier                  |
| Aout       | 7e   | 17   | 7e nombre premier                  |
| Septembre  | 8e   | 19   | 8e nombre premier                  |
| Octobre    | 9e   | 23   | 9e nombre premier                  |
| Novembre   | 10e  | 29   | 10e nombre premier                 |
| Decembre   | 11e  | 31   | 11e nombre premier                 |

### Verification

Le 11e nombre premier est bien **31**. En effet, la liste des nombres premiers dans l'ordre est :

> 2, 3, 5, 7, 11, 13, 17, 19, 23, 29, **31**, ...

Il reste a verifier que la date du **31 decembre** existe dans le calendrier 2025. Le mois de decembre compte toujours 31 jours, donc cette date est bien valide.

### Coherence avec l'enonce

Les cinq premieres dates donnees dans l'enonce correspondent exactement a notre construction :
- 1er janvier (jour = 1)
- 2 fevrier (jour = 2, premier nombre premier)
- 3 mars (jour = 3, deuxieme nombre premier)
- 5 avril (jour = 5, troisieme nombre premier)
- 7 mai (jour = 7, quatrieme nombre premier)

La regle se poursuit de maniere univoque jusqu'a decembre.

## Nombre de solutions

**1** (reponse unique)

## Reponse

La date cochee au mois de decembre est le **31 decembre**.
