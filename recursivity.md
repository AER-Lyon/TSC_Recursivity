
# La récursivité

## Description

Jusqu'à présent, la plupart des fonctions que vous avez créées sont des fonctions **itératives**, c'est à dire que chaque instruction est à la suite de la précédente. Lorsque vous vouliez répéter une action, vous utilisiez une boucle *for* ou *while*.

Dans ce cours, nous introduisons un nouveau concept : **la récursivité**. \
La récursivité est un principe fondamental en programmation, et existe dans tous les languages; elle permet de simplifier le code et d'en réduire la taille lorsque bien utilisée.

Mais qu'est ce que la récursivité ? \
La récursivité, c'est **appeler une fonction à l'intérieur d'elle-même**.

Vous vous demandez surement à quoi cela peut-il bien servir. Rassurez-vous, vous n'êtes ni les premiers, ni les derniers à se poser cette question. \
À l'issue de ce cours, vous aurez compris la récursivité et l'aurez utilisés dans plusieurs exemples.

Afin de bien vous faire comprendre comment utiliser la récursivité et ses cas d'application, chaque exercice est divisé en deux parties, correspondant à une manière de coder différente :
- Une première fois de manière **itérative**, c'est à dire en utilisant des boucles
- Une deuxième fois de manière **récursive**, en appelant cette fois-ci la fonction à l'intérieur d'elle-même.

Une correction des execices aura lieu au fur et à mesure du cours.

## Exemple

### Itératif

Dans ce premier exercice, nous allons réaliser une fonction prenant en paramètre un nombre positif, et affichant la liste des nombres partant de ce nombre jusqu'à 0.

```
compte_a_rebourg(4);

4
3
2
1
0
```

Pour réaliser cette fonction de manière itérative, nous allons utiliser une boucle while qui, à chaque tour de boucle, affiche la variable et la décrémente.

```c
void compte_a_rebourg(int nb)
{
    while (nb >= 0) {
        printf("%d\n", nb);
        nb--;
    }
}
```

### Récursif

Pour réaliser cette fonction de manière récursive, nous allons encore afficher la variable, mais au lieu d'utiliser une boucle en la décrémentant, nous allons appeler la fonction *compte_a_rebourg* en lui passant en argument la variable décrémentée.

De cette façon, la fonction va afficher le nombre passé en paramètre, puis appeler une autre instance de la fonction en lui passant en paramètre la variable moins 1.
Cette nouvelle instance de la fonction va à son tour afficher cette nouvelle valeur et ainsi de suite.

Ce cycle va continuer jusqu'à ce que *compte_a_rebourg* soit appelée avec une valeur négative. \
Cette fonction va alors s'arrêter avec le *return*, revenant à la fonction qui l'a appelée, qui va à son tour retourner et revenir à la fonction précédente et ce, jusqu'à revenir à la fonction initiale.

```
compte_a_rebourg(4);
|-> compte_a_rebourg(3);
    |-> compte_a_rebourg(2);
        |-> compte_a_rebourg(1);
            |-> compte_a_rebourg(0);
                |-> compte_a_rebourg(-1);
```

Voici le code de la fonction récursive.

```c
void compte_a_rebourg(int nb)
{
    if (nb < 0)
        return;

    printf("%d\n", nb);

    compte_a_rebourg(nb - 1);
    return;
}
```

## Exercices

### 1. my_putstr

Réalisez la fonction une fonction prenant en paramètre un char * et affichant chacun de ses caractères. La fonction aura le prototype suivant :

```c
void my_putstr(char *str);
```
```
my_pustr("Salut");

> Salut
```

#### A. Itératif

Réalisez la fonction de manière itérative, c'est à dire comme vous l'avez fait durant la piscine.

#### B. Récursif

Cette fois-ci, créez la même fonction mais de manière récursive. \
Si vous êtes bloqués et n'arrivez pas à avancer, faites appel aux AER présents dans la salle.

### 2. Fibonacci

La suite de fibonacci est une suite inventée par le mathématicien Fibonacci, dans laquelle chaque nombre est égal à la somme des deux précédents.

```
1 1 2 3 5 8 13 21 34 55 etc...
```
```
explication :
1 + 1 = 2
1 + 2 = 3
2 + 3 = 5
3 + 5 = 8
etc ...
```

Créez une fonction prenant en paramètre un nombre et et affichant le n-ème élément de la suite de fibonacci.

```c
void fibonacci(int a);
```
```
fibonacci(6);
> 13

fibonacci(9);
> 55
```

#### A. Itératif

Si vous avez du mal à implémenter cette fonction de manière itérative, rassurez-vous, c'est un cas concret où l'utilisation du récursif est plus facile que l'utilisation de l'itératif. \
Vous êtes libre de passer directement à la partie récursive, ou bien de prouver que vous êtes quelqu'un qui aime se faire du mal et réaliser la fonction en itératif.

#### B. Récursif

Pour implémenter la fonction en récursif, réfléchissez comme à l'exercice 1. \
"Comment pourrais-je remplacer la boucle par un appel de fonction à soi-même ?"

Si vous êtes bloqué, n'hésitez pas à faire appel aux AER présents dans la salle. Ils seront plus que ravis de faire votre travail à votre place (non).

### 3. Somme d'un tableau

Réalisez une fonction calculant la somme des élements d'un tableau d'int et la **retournant**.

```
[1, 0, 35, 26, 4]

> 66
```

#### A. Itératif

```c
int array_sum(int *array, int length);
```

Normalement, vous n'aurez pas besoin d'aide sur cette fonction.
Mais bon, si vous avez besoin d'aide, même rappel, les AER sont là.

#### B. Récursif

Le prototype de la fonction n'est volontairement pas indiqué, à vous de réfléchir à comment faire votre fonction en choisissant votre stratégie et en expérimentant.


> **Tip**: Il est possible que la fonction récursive ait besoin d'un ou de plusieurs paramètres différents et/ou en plus de la fonction itérative.

### 4. my_putnbr

Votre objectif est maintenant de réaliser une fonction affichant un nombre passé en paramètre.

```c
void my_putnbr(int nb);
```

```
my_putnbr(10)

10
```

Étant donné que cette fonction est **extrèmement** plus facile à réaliser de manière récursive, il n'y a pas de partie itérative à cet exercice. Vous êtes cependant libre de le faire en bonus à la fin du cours si vous êtes un crack.

### A. Récursive

Récapitulons :

- Vous devez afficher les chiffres de gauche à droite
- Vous ne pouvez afficher que les chiffres, donc les nombres compris entre 0 et 9

Ce qui veut dire que pour pouvoir faire cette fonction, vous allez devoir tout d'abord vérifier si le nombre donné en paramètre est compris entre 0 et 9, et si c'est le cas, l'afficher puis retourner.

Ensuite, si le nombre est supérieur à 9, vous devrez isoler ses chiffres. Comment faire cela ? \
Il existe l'opérateur % (modulo), qui permet donner le reste d'une équation.
En appliquant modulo 10 à notre nombre, on obtient le reste de sa division par 10.

Autrement dit :
```
4096 % 10 = 6

car 4096 divisé par 10 est égal à 409, reste 6.
On obtient donc son dernier chiffre.
```

Nous connaissons donc maintenant le chiffre des unités. Mais comment le supprimer du nombre initial \
Si vous avez été attentif, la réponse est déjà donnée dans l'encadré juste au-dessus.

Une fois que vous avez :
- le dernier chiffre (6)
- le reste du nombre (409)

il ne vous reste plus qu'à répéter cette opération (sans boucle, avec la récursivité) en affichant à chaque fois le dernier chiffre **après** avoir effectué la récursivité (pour que les chiffres soient affichés de gauche à droite).