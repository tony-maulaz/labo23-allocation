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

Ce type de données permet de mémoriser des valeurs mesurées dans un tableau
alloué dynamiquement, pointé par le champ `tableau`. 

`taille` 
: Mémorise le nombre de valeurs disponibles dans le tableau alloué
dynamiquement.

`nbrMesure`
: Le nombre de mesure dans le tableau.

On vous demande d’écrire les fonctions suivantes :

#### Saisir
```C
// Saisie de la taille du tableau et allocation de mémoire.
void saisir(Mesures* mesures);
```
Cette fonction doit
- Demander à l'utilisateur de saisir la taille du tableau de mesure
- Allouer le tableau
- Si un tableau est déjà alloué, il faut informer l'utilisateur

#### Initialiser
```C
// Mise à zéro des champs de la structure
void initialiser(Mesures* mesures);
```

#### Ajout
```C
// Ajout d'une mesure dans le tableau
void ajout(Mesures* mesures);
```
Cette fonction permet d'ajouter une mesure dans le tableau.
- Dans le message de saisie, on affiche le nombre de place disponible dans le tableau.
- Affiche un message en demandant à l'utilisateur d'entrer une mesure (un `double`)
- Ajout de la saisie dans le tableau.


#### Liberer
```C
// Libération de la mémoire si allouée, ne rien faire si non allouée
// Doit pouvoir être appelée plusieurs fois de suite sans problème
void liberer(Mesures* mesures);
```

#### Afficher
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

#### Moyenne
```C
double moyenne(Mesures* mesures);
```
Cette fonction affiche le nombre de mesure ainsi que la moyenne des valeurs qui sont dans le tableau


## Menu
Ecrire un programme principal avec un `menu` permettant de
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

## IMPORTANT
- On ne peut allouer qu'un seul bloc.
- Si l'allocation se passe mal, on doit informer l'utilisateur et non quitter le programme.
- La seule manière de quitter le programme est par le menu.
- Prévoir les tests nécessaires pour que les fonctions se comportent correctement dans les différents cas possibles. 
  Par exemple, la fonction `afficher` ne doit pas planter, même si l’utilisateur n’a pas encore procédé à la saisie.
- Faites en sorte que quelle que soit la séquence d’opérations effectuée par l’utilisateur, on ne perde jamais un bloc de mémoire alloué dynamiquement. 
- La mémoire dynamique allouée doit également être libérée avant de quitter le programme.
