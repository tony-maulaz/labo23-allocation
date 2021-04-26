# labo23 Allocation dynamique de mémoire

## Objectifs pédagogiques
- Mettre en oeuvre l’allocation dynamique de mémoire.
- Créer un ensemble de fonctions pour un type de données.

## Descriptif
On considère le type de données suivant :

```C
typedef struct
{
  int taille;
  int nbrMesure;
  double* tableau;
} Mesures;
```

Ce type de données permet de mémoriser des valeurs mesurées dans un tableau alloué dynamiquement, pointé par le champ `tableau`. 

`taille` 
: Mémorise le nombre de valeurs disponibles dans le tableau alloué dynamiquement.

`nbrMesure`
: Le nombre de mesure dans le tableau.

On vous demande d’écrire les fonctions suivantes :

### Initialiser
```C
// Saisie de la taille du tableau et allocation de mémoire.
void init(Mesures* mesures);
```
Cette fonction doit
- Demander à l'utilisateur de saisir la taille du tableau de mesure
- Allouer le tableau
- Si un tableau est déjà alloué, il faut informer l'utilisateur que cela n'est pas possible.

### Reset
```C
// Mise à zéro des des valeurs dans le tableau de mesures
void reset(Mesures* mesures);
```

### Ajouter
```C
// Ajout d'une mesure dans le tableau
void ajout(Mesures* mesures);
```
Cette fonction permet d'ajouter une mesure dans le tableau.
- Dans le message de saisie, on affiche le nombre de place disponible dans le tableau.
- Affiche un message en demandant à l'utilisateur d'entrer une mesure (un `double`)
- Ajout de la saisie dans le tableau.


### Libérer
```C
// Libération de la mémoire si allouée, ne rien faire si non allouée
// Doit pouvoir être appelée plusieurs fois de suite sans problème
void liberer(Mesures* mesures);
```

### Afficher
```C
// Pas d'erreur même si aucune mesure allouée
void afficher(Mesures* mesures);
```
Cette fonction affiche la liste des mesures
```console
Les mesures
1 : 2.365
2 : 25.7
3 : 78.369
...
```

### Moyenne
```C
double moyenne(Mesures* mesures);
```
Cette fonction affiche le nombre de mesure ainsi que la moyenne des valeurs qui sont dans le tableau


## Menu
Écrire un programme principal avec un `menu` permettant de
- saisir
- libérer
- ajouter
- afficher
- moyenne
- quitter

## Saisie
- La taille du tableau est limitée entre `0` et `100`
- La saisie des mesures est en `double`
- Si une mauvaise saisie est faite, il faut demander à l'utilisateur de recommencer.

## Fonctions
- Découper le programme en petites fonctions
- Développer une fonction pour faire la saisie d'un nombre. Cette fonction doit prendre comme paramètre le message à afficher.
- Vous ne devez pas copier du code

## IMPORTANT
- On ne peut allouer qu'un seul bloc.
- Si l'allocation se passe mal, on doit informer l'utilisateur et non quitter le programme.
- La seule manière de quitter le programme est par le menu.
- Prévoir les tests nécessaires pour que les fonctions se comportent correctement dans les différents cas possibles. 
  Par exemple, la fonction `afficher` ne doit pas planter, même si l’utilisateur n’a pas encore procédé à la saisie.
- Faites en sorte que quelle que soit la séquence d’opérations effectuée par l’utilisateur, on ne perde jamais un bloc de mémoire alloué dynamiquement. 
- La mémoire dynamique allouée doit également être libérée avant de quitter le programme.

## Partie 2

### Git
Avant toute grosse modification n'oubliez pas de faire un `commit` afin de pouvoir revenir en arrière facilement.

### Structure Mesure

Modifier la structure `Mesures` pour avoir un tableau de structure `Point` à la place d'un tableau de `double`.

```C
typedef struct
{
  int num;
  double valeur;
} Point;
```

Le champ `valeur` correspond à l'ancienne variable `double` qui contient la valeur de mesure.

Le champ `num` est le numéro de la mesure. A chaque fois qu'une nouvelle mesure est faite, on incrémente cette valeur. La première mesure a comme numéro le `1`.

```C
typedef struct
{
  int taille;
  int nbrMesure;
  Point* tableau;
} Mesures;
```

### Modification de la fonction afficher

Cette fonction affiche la liste des mesures.

Sur chaque ligne il faut afficher le `numéro` de la mesure ainsi que la valeur. Le numéro doit venir de la structure.
 
```console
Les mesures
1 : 2.365
2 : 25.7
3 : 78.369
...
```


### Ajouter les fonctionnalités suivantes :

#### Modifier
```C
// Modifie la taille du tableau
void modifier(Mesures* mesures);
```
Cette fonction permet de demander à l'utilisateur de saisir une nouvelle capacité pour le tableau.

- Si la nouvelle capacité du tableau est plus petite que le nombre de mesure en cours, il faut afficher une erreur et ne pas modifier la taille.

La fonction affiche un message informatif du genre :
```console
La capacité a bien été modifiée, il y a maintenant 12 places dans le tableau.
```

#### Supprimer dernière
Supprime la dernière mesure dans le tableau, ce qui va permette d'avoir une place en plus pour stocker une mesure.

```C
// Supprime la dernière mesure du tableau
void supprimer_fin(Mesures* mesures);
```

La fonction affiche un message informatif du genre :
```console
La mesure #8 a été supprimée, il reste 5 places dans le tableau.
```

#### Supprimer première
Supprime la première mesure dans le tableau, ce qui va permette d'avoir une place en plus pour stocker une mesure.

```C
// Supprime la première mesure dans le tableau
void supprimer_debut(Mesures* mesures);
```

La fonction affiche un message informatif du genre :
```console
La première mesure a été supprimée, il reste 9 places dans le tableau.
```
