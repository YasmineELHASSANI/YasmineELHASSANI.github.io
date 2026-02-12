---
title: Projet jeu awalé
subtitle: Projet informatique - 1e année
description: Développement du jeu de l'awalé en langage C
layout: product
image: https://via.placeholder.com/640x480
---

<h1>Introduction</h1>

**Objectifs du projet**

Le but de ce projet est de réaliser en langage C le jeu de l’awalé. L’awalé est un jeu d’origine 
africain datant du VIIIème siècle. Le but est de s’emparer d’un maximum de graines. Le 
joueur qui a le plus de graines à la fin de la partie l’emporte. Pour ce faire nous avons 
travaillé de façon méthodique.
Pour mener a bien ce projet nous avons travaillé en équipe de trois.

<h1>Travail Réalisé</h1>

**Le programme**

Le programme est constitué de plusieurs modules qui permettent de le rendre plus lisible. Le programme permet de jouer au jeu d'Awalé en mode solo (contre l’ordinateur) ou contre un adversaire humain. Il gère les règles du jeu, l'affichage du plateau, et le tour des joueurs.

**Lancement du jeu**

Tout d'abord, nous affichons les règles du jeu et nous demandons à l'utilisateur le mode de jeu souhaité.
Ensuite, le jeu commence par initialiser le tableau afin d’avoir le plateau du jeu. Il s’agit d’un seul tableau répartit sur deux lignes afin de rendre les transferts de graines plus facile. Les graines sont matérialisées par des nombres. Initialement elles sont au nombre de 4 dans chaque case.

**Affichage du plateau**

Nous avons séparé le plateau en 2 parties. La ligne de jeu du joueur actif se situe toujours en bas pour simuler un plateau physique sur lequel notre partie du plateau est devant nous. Le joueur 2 possède les cases de a à f et le joueur 1 possède les cases de A à F.
Le but est que le joueur ait une expérience le plus proche possible d’un awalé classique (donc physique).
De a à f, nous avons les indices 0 à 5, de A à F se sont les indices 11 à 6.

**Saisie d'une case**

Nous avons deux fonctions de saisie. Ils permettent au joueur actif de choisir quels sont les graines qu’il souhaite jouer. 

*Remarques : Si la case sélectionnée ne contient aucune graine alors le programme renouvelle la demande à l’utilisateur. Si l’utilisateur tape un nombre ou une lettre qui n’est pas dans le tableau pour faire son choix alors l’ordinateur redemande à l’utilisateur de choisir.*

**Répartition des graines capturées**

Le décalage est l’action de répartir les graines une par une dans le sens anti-horaire. Le nombre de cases qui voient sa quantité de graines augmenter de 1 correspond au nombre de graines présent dans la case choisi. Par exemple sur la figure 4 ci-dessus (chapitre 2.1.3) le joueur choisi la case F qui contient 4 graines. Les 4 cases à « sa droite » reçoivent une graine chacune. Les cases a, b, c et d sont maintenant à 5 graines.
La procédure commence par demander la lettre de la case choisie par l’utilisateur via la fonction saisie. Nous avons fait une procédure decalage1 associé à la fonction saisie1 pour le joueur 1 et une procédure decalage2 associé à la fonction saisie2 pour le joueur 2.
Elle parcourt le tableau t pour trouver une correspondance avec la valeur saisie. Si une correspondance est trouvée, elle utilise la valeur correspondante dans le tableau y à partir de la position i + 6 pour déterminer jusqu’où le décalage doit s’effectuer.
Si la valeur trouvée (variable s) est non nulle, elle incrémente les valeurs dans le tableau y[] à partir de la position suivante (variable a). Si la variable a dépasse 11, elle recommence à incrémenter à partir de 0. La case sélectionnée à été vidée (y[i+6] = 0 pour le decalage1 et y[i]=0 pour decalage2).

**Incrémenttation des points**

Nous avons essayé de faire en sorte qu’après le décalage la procédure vérifie si la dernière case incrémentée est égale à 2 ou 3. Si c’est le cas alors la case est vidée et le joueur actif gagne 2 ou 3 points selon le nombre de graines présent dans cette case. Ensuite le programme doit vérifier de la même manière la case précédente et accorder le points ou non.
Nous ne sommes pas tout à fait parvenus à ce résultat. A la place le programme vérifie les valeurs de la ligne du joueur actif (6 cases). Si une case est égale à 2 ou 3 elle est vidée et les points capturés
sont ajoutés au compteur (score du joueur).
La procédure decalage2 fonctionne de la même manière pour le joueur 2.
Nous avons testé 2 méthodes pour la capture mais elles fonctionnent toutes les deux de la même façon. Méthode utilisée pour le joueur 2 (figure 8) et méthode utilisée pour le joueur 1 (figure 9).
La procédure Affiche_points affiche les points de deux joueurs, en utilisant des pointeurs pour 
accéder à ces valeurs. Elle affiche les résultats dans un format lisible dans la console, permettant 
ainsi de visualiser les scores des joueurs.


**Gagnant**

Les deux fonctions verifie_gagnant_multi et verifie_gagnant_solo ont pour objectif de déterminer le gagnant d'un jeu en comparant les points de deux joueurs (figure 11). Ces procédures doivent être appelée à la fin du jeu. La partie est terminé lorsque l’un des deux joueurs n’a plus de graines dans 
sa ligne (figure 12).

**Mode Solo**

L’ordinateur joue à la place du joueur 2, au lieu de saisir une case, il choisit une case aléatoire entre a et f (figure 13) et le jeu se déroule comme pour le mode multijoueur présenté précédemment (figure14). 

<h1>Les points forts</h1>

* Le code est bien structuré, avec des modules clairement définies pour chaque fonctionnalité. Cela rend le programme facile à lire et à comprendre.
* La fonction regle() présente clairement les règles du jeu, ce qui est essentiel pour les nouveaux joueurs.
* Le programme permet à l’utilisateur de choisir entre deux modes de jeu : en solo contre l'ordinateur ou en multijoueur.
* L’affichage du plateau se fait de manière claire, avec une représentation textuelle des cases et des graines. Cela aide les joueurs à suivre l'état du jeu.
* Le programme suit les points des joueurs, ce qui ajoute une dimension compétitive au jeu.
* Les fonctions de vérification des gagnants fournissent un retour sur le résultat du jeu.
* Le mode solo ajoute un élément d'imprévisibilité, rendant le jeu contre l'ordinateur plus intéressant.
* Le programme permet de rejouer après la fin d'une partie, ce qui est une bonne pratique dans les jeux pour encourager les utilisateurs à continuer à jouer.

<h1>Conclusion</h1>

En conclusion, ce projet de programmation du jeu d'awalé en langage C nous a permis d'explorer non seulement les aspects techniques de la conception de jeux, mais également de mieux comprendre les règles et les stratégies qui bordent ce jeu traditionnel. À travers cette expérience, nous avons renforcé nos compétences en algorithmique, en gestion de la mémoire et en manipulation des structures de données. Ce projet nous a également permis de travailler en équipe, favorisant la collaboration et l'échange d'idées, ce qui a été essentiel pour mener à bien le projet.

