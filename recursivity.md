
# La récursivité

## Description

Dans ce cours, nous introduisons un nouveau concept : **la récursivité**.

### La récursivité c'est quoi ?

La récursivité, c'est **appeler une fonction à l'intérieur d'elle-même**.

Jusqu'à présent, la plupart des fonctions que vous créiez étaient des fonctions **itératives**, c'est à dire que chaque instruction était à la suite de la précédente. Lorsque vous vouliez répéter une action, vous utilisiez une boucle *for* ou *while*.

### Ça sert à quoi ?

La récursivité permet de **simplifier le code** et de **résoudre des problèmes plus facilement** qu'en itératif dans certaines situations. \
Vous trouverez dans ce sujet des exercices graduellement plus difficiles.

Une correction des execices aura lieu au fur et à mesure du cours.

## Exemple

Voici un premier exemple pour illustrer ce concept avec la même fonction faite en itératif et en récursif.

Cette fonction affiche un compte à rebours partant du nombre passé en paramètre


```
compte_a_rebours(4);

4
3
2
1
0
```

### Itératif

Pour réaliser cette fonction de manière itérative, nous allons utiliser une boucle while qui, à chaque tour de boucle, affiche la variable et la décrémente.

```c
void compte_a_rebours(int nb)
{
    while (nb >= 0) {
        printf("%d\n", nb);
        nb--;
    }
}
```

### Récursif

Pour réaliser cette fonction de manière récursive, il faut remplacer la boucle while par un appel de fonction.

Ainsi, au lieu de décrémenter la variable dans le *while*, nous allons afficher la variable puis appeler un autre *compte_a_rebours* en lui passant **le numéro suivant** (la variable décrémentée).

Ils ne nous reste plus qu'à trouver un moyen d'arrêter ce cycle.
Nous allons donc mettre la **même condition d'arrêt** que le while, à savoir si la fonction reçoit un nombre négatif.

La fonction va alors retourner, ce qui va revenir à sa fonction "parente", qui va à son tour retourner, et ainsi de suite.

```
compte_a_rebours(4);
|-> compte_a_rebours(3);
    |-> compte_a_rebours(2);
        |-> compte_a_rebours(1);
            |-> compte_a_rebours(0);
                |-> compte_a_rebours(-1);
```

Voici le code de la fonction récursive.

```c
void compte_a_rebours(int nb)
{
    if (nb < 0)
        return;

    printf("%d\n", nb);

    compte_a_rebours(nb - 1);
    return;
}
```

## Exercices

### 1. my_putstr

Réalisez un putstr récursif, qui affiche le contenu de la chaîne passée en paramètre :

```c
void my_putstr(char *str);
```
```
my_pustr("Salut");

> Salut
```


Si vous êtes bloqués et n'arrivez pas à avancer, n'hésitez pas à faire appel aux AER présents dans la salle.

### 2. Factorielle

La factorielle d'un nombre n ( écrit **n!** ) est la multiplication de lui-même et des nombres précédents

```
5! = 5 x 4 x 3 x 2 x 1 = 120
3! = 3 x 2 x 1 = 6
1! = 1
```

Réalisez une fonction qui calcule la factorielle d'un nombre passé en paramètre.

```c
int facto(int nb);
```

### 3. Fibonacci

La suite de fibonacci est une suite mathématique dans laquelle chaque nombre est égal à la somme des deux précédents.

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

Pour implémenter la fonction en récursif, réfléchissez comme pour l'exemple et l'exercice précédent. \
"Comment pourrais-je remplacer une boucle par un appel de fonction"

### 4. Somme d'un tableau

Réalisez une fonction calculant la somme des élements d'un tableau d'int passé en paramètre et la retournant.

```
[1, 0, 35, 26, 4]

> 66
```

Le prototype de la fonction n'est volontairement pas précisé, à vous de réfléchir à comment faire votre fonction en choisissant votre stratégie et en expérimentant.

### 5. my_putnbr

Votre objectif est maintenant de réaliser une fonction affichant un nombre passé en paramètre.

```c
void my_putnbr(int nb);
```

```
my_putnbr(10)

> 10
```


### Aide
