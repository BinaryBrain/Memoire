# Remarques générales

Le rapport est plutôt bien rédigé, même s'il y a de trop nombreuses coquilles (qu'une relecture aurait permis de corriger...). Au niveau de la structure, il manque une véritable introduction et une conclusion. L'ordre des chapitres pourrait être un peu adapté.

Au niveau du contenu, on comprend que vous avez surtout utilité la phase préparatoire pour vous mettre au développement iOS et pour faire les premières expériences au niveau de la vidéo. On a l'impression que vous avez bien fait les choses à ce niveau et que vous avez compris comment utiliser ces "briques" pour la suite du projet. 

En ce qui concerne le cadrage du projet, les objectifs et le déroulement de la 2ème phase, on est peu dans le flou. Le cahier des charges initial a simplement été copié-collé, alors qu'on s'attendait à ce que le périmètre soit affiné. Il y une liste d'activités prévue pour la suite, mais il n'y a aucun détail (esquisses, activités précises, estimations de l'effort, priorités, etc.). 

Pour conclure, le rapport est correct mais pourrait être plus "riche" en contenu. Dans certaines parties (notamment l'état de l'art), c'est un peu vite survolé. Sur la base du rapport, c'est un peu difficile de se faire une idée concrète et précise de ce que vous avez fait et délivré.

* Note: 4.7


# Remarques détaillées

## Résumé

* C'est beaucoup trop résumé. Dans le résumé, vous devez clairement dire quelles sont les contributions de votre projet (en d'autres termes, qu'avez-vous fait dans le contexte de RTS Express Live? Est-ce que vous avez tout développé ou bien est-ce que vous avez participé à un effort plus large?). Il faut au moins 2-3 paragraphes pour un rapport de cette taille.

## Table des matières

* Il manque une section **introduction**. Peut-être que c'est le contenu de ce que vous avez appelé "Préambule" (mais alors, renommez). 

* Avant de lire le texte, je m'attendrais plutôt à lire le **cahier des charges** avant de lire l'état de l'art. Si vous avez fait cet état de l'art, c'est parce qu'il vous a aidé à remplir votre cahier des charges. 

* 3.4 Remarque. Un peu bizarre dans une table des matières.

* la partie "Suite du projet" me paraît bien (dans la table des matières)

## Chapitre 1: Préambule

* fait partiE (p.5)
* chose nouvelLLE (p.5)
* retransmissionS (p.5)
* peut-être != peut être (p.5) 
* (j'arrête ici pour le relevé des coquilles... relisez!!)

* Le texte est bien rédigé et vous introduisez bien le contexte. Avec le dernier paragraphe, on rentre dans le vif du sujet (on commence à comprendre ce que VOUS devez faire)... mais vous vous arrêtez tout net. On veut en savoir plus.

* Si vous écrivez une **introduction** (et pas un préambule), il manque aussi une partie très importante. On veut savoir pourquoi vous avez écrit CE rapport (quels sont les objectifs du rapport) et comment il est structuré (je suis lecteur et je veux savoir ce que je vais trouver dans le document, comprendre comment les différents chapitres sont organisés logiquement).


## Chapitre 2: Etat de l'art

* Remarque générale qui fait suite à la remarque précédente. Au début de chaque chapitre, rappelez au lecteur ce qu'il va trouver dans ce chapitre (souvent, c'est aussi bien de le replacer dans l'organisation logique de tout le document). Expliquez aussi comment il est lui-même organisé en sous-sections.

* serveur-clients, client-serveur?
* ceux baséS sur HTTP...
* un prototolE...
* des proxies
 

* Votre paragraphe suivant est incorrect (ou alors, je n'ai pas compris ce que vous voulez dire). Le contenu dynamique généré sur le Web est bien du contenu généré à la volée et n'est pas stocké dans des fichiers intermédiaires...???
> Par exemple, un protocole de diffusion de vidéo basé sur UDP pourraient simplement envoyer le flux de bytes de la vidéo à travers le réseau avec peu de traitements sur les données. Par contre, avec l’utilisation d’HTTP, les données doivent être contenues dans des fichiers. 

* Sur l'état de l'art, c'est bien de passer en revue les différents protocoles. Mais j'aimerais bien savoir **concrètement** ce que cela veut dire pour les développeurs. Par exemple, si je veux utiliser HLS, qu'est-ce que je dois faire? Est-ce que je dois utiliser un SDK, etc.? Développez et donnez plus de détails. En l'état, c'est un peu léger.

* "Une" des problèmes, inconvéniants, ..., les typos!!
* La partie sur le développement iOS n'est pas complètement inutile, mais elle est discutable dans un chapitre "état de l'art". Pour le rapport final, elle devrait plutôt faire partie du chapitre "implémentation" ou alors faire partie d'une annexe.


## Chapitre 3: Cahier des charges

* Ne reprenez pas le cahier des charges tel quel (si vous voulez fournir l'original, mettez le dans une annexe). Dans le document, on veut lire VOTRE interprétation du cahier des charges (pour voir que vous vous l'êtes approprié). Je ne m'attends pas à trouver une liste de "bullet points", mais plutôt du texte et des explications.

* Autre point important: vous avez repris le cahier des charges **initial**, qui était volontaire très large (voir la partie "domaine de recherches"). Mais au terme de la phase préparatoire, vous devriez avoir défini le périmètre de votre projet beaucoup plus précisément avec votre mandant. Et c'est ce qu'on veut lire dans ce rapport.

## Chapitre 4: Approche du problème

* J'aime bien le **contenu** du chapitre, car il montre ce que vous avez fait concrètement. Je suis plus partagé sur le style (au début, c'est une succession rapide d'activités, un peu comme un journal de bord). J'aurais préféré quelque chose d'un peu plus structuré et moins narratif (utiliser le "je" de manière excessive est souvent un signe).

## Chapitre 5: Suite du projet

* en deux groupeS...

* 5.1: vous auriez dû développer cette partie. D'abord, on aimerait mieux comprendre ce qui se "cache" derrière ces deux listes à puces. A quel point avez-vous déjà une idée claire de ce que vous devez faire pour réaliser ces points? Quel est l'effort estimé pour les réaliser? Quelles sont les fonctions les plus prioritaires? En se basant uniquement sur cette liste, on ne peut pas savoir à quel point vous avez la maîtrise sur le cadrage du projet et si vous allez être capable de tout délivrer. On ne voit pas non plus s'il y a un "minimum" à atteindre et si certaines parties sont un "nice to have".

* l'instabilité du logiciel n'est pas un risque de votre projet. C'est une contrainte, un objectif. Un risque, c'est si une libraire que vous allez utiliser est instable et que cela pourrait vous obliger à trouver une alternative.

* risques liés au réseau: ok, surtout que vous donnez des pistes pour mitiger le risque.

* risques liés à la performance... un peu la même remarque que pour l'instabilité. Ici, au moins, vous êtes plus spécifique par rapport au problème. Vous ne parlez pas de batterie, c'est pourtant un sujet d'inquiétude pour une utilisation "pendant plusieurs heures", non?

## Chapitre 6: Conclusion

Non... justement, elle manque!!












 











