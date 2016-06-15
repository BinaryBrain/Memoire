# Travail de Bachelor

## Sommaire

- Préambule
- État de l'art
	- Introduction au diffusion vidéo en direct
		- Présentation des protocoles existants
		- HTTP-based
		- RTMP
		- HLS versus MPEG-DASH
	- Introduction au développement sur iOS
		- Swift
		- Utilisation de bibliothèque Objective-C
		- Utilisation de bibliothèques externes

- Cahier des charges
	- Contexte
	- Objectifs
		- Objectifs principaux
		- Objectifs secondaires
	- Critère d'acceptation
	- Remarque
	- Domaines de recherche

- Approche du problème

- Problèmes rencontrés

- Suite du projet
	- Étapes pour avancer dans le projet
	- Analyse des risques 
	- Stratégie de mitigation des risques

##  Préambule

Dans le monde d'aujourd'hui, l'information instantanée prend de plus en plus d'ampleur à travers divers vecteurs. Les différents réseaux sociaux soutiennent ce mouvement en incitant son public à partager du texte, des clichés ou encore de la vidéo. En effet, de nombreuses applications et sites web voient le jour chaque année. Parmi eux, les plus connus sont Twitch.tv: un site web de diffusion vidéo en direct utilisé surtout par les amateurs de jeu vidéo, Periscope: une application mobile permettant la diffusion en direct depuis la caméra du smartphone vers d'autres smartphones à travers le monde, et la majorité des grands acteurs du web ont ajouté cette fonctionnalité à leurs sites web: YouTube, Facebook, Snapchat, etc.

Ce phénomène contraint les médias "classiques" à continuer à s'adapter aux nouvelles technologies de communication. La diffusion d'information en direct prend alors une place de plus en plus importante afin de d'atteindre ce nouveau public friand d'instantané. La RTS (Radio Télévision Suisse) fait parti de ces médias dont la popularité est en jeu. Il n'est donc pas étonnant qu'ils souhaitent aussi participer à l'expension de cette nouvelle manière de partager l'information. Bien évidemment, les émissions et retransmission d'évenements en direct n'est pas chose nouvel pour une chaîne de télévision mais la différence réside aussi dans la manière de procéder. En effet, en ayant une application de diffusion en direct sur leurs téléphones, les journalistes ont la libérté de créer du contenu à tout moment et sans préparation. Cela peut-être très pratique pour émettre les images d'un festival de musique, d'un incendie qui vient de débuter ou encore d'interviewer une célébrité que l'on croiserait par hasard.

C'est pourquoi la RTS a proposé à l'HEIG-VD un travail de Bachelor ayant pour sujet la création d'une application pour iPhone permettant la diffusion en direct des images perçue par sa caméra, envoloppé dans une interface donnant la posibilité aux journalistes de s'authentifier, 

## État de l'art

### Introduction au diffusion vidéo en direct

La diffusion de vidéo en direct reste quelque chose de techniquement difficile à réaliser pour plusieurs raisons.

Tout d'abord, les fichiers vidéo comportent beaucoup de données et sont donc rapidement volumineux. Cela entraîne alors d'autres problèmes: le réseau de communication utilisé doit être capable de gérer un débit minimal afin que le temps de transmission des fichiers vidéos ne soit pas plus long que la durée de la vidéo envoyée.

Pour ce travail, nous nous concentrerons uniquement sur les systèmes de streaming vidéo de type serveur-clients dans lesquels la latence n'est pas une priorité majeure et non les protocoles peer-to-peer et temps réel utilisés, par exemple, pour la vidéoconférence.

#### HTTP-based

Les protocoles de streaming vidéo les plus répandus sont sans doute ceux basé sur HTTP.

#### RTMP

RTMP (Real-Time Messaging Protocol) est un protocol de communication permettant le streaming de vidéo. Il a été développé par Macromedia (aujourd'hui Adobe) et se base sur un client en Flash. Il est basé sur HTTP et utilise des vidéos au format FLV (Flash Video) et de l'audio en MP3 ou AAC.

Les principaux inconvéniants de ce protocol est qu'il est très lié aux clients Flash et que ces derniers sont aujourd'hui de plus en plus remplacés par les technologies HTML5. De plus, même si ce protocol est largement documenté, il est propriétaire.

#### HLS

HLS (HTTP Live Streaming) est un système de streaming vidéo développé par Apple et basé sur HTTP. Il utilise un conteneur MPEG-2 TS et le codec H.264 pour ses fragments vidéo et supporte le MP3 et le AAC pour le transport du son.

#### MPEG-DASH

MPEG-DASH (MPEG pour Moving Picture Experts Group et et DASH pour Dynamic Adaptive Streaming over HTTP) est un système de streaming vidéo, également basé sur HTTP. Contrairement à RTMP et à HLS, MPEG-DASH ne dépend d'aucun codec. De plus, il supporte plusieurs format de conteneur. Il est alors capable d'envoyer des vidéos en MPEG-2 TS (comme HLS) ainsi que du MPEG-4 et les formats similaires.

### Introduction au développement sur iOS

#### Swift

Swift est un langage de programmation conçu et maintenu par Apple. Sorti il y a environ 2 ans, il est en train de remplacer l'utilisation d'Objective-C pour la programmation sur iOS. C'est un langage moderne à la syntaxe épurée dont on retrouve les concepts dans certains autres langages modernes tel que Scala, C# ou encore Rust. Comme ces derniers, il est multi-paradigm, et permet donc de faire de la programmation orientée objet, de la programmation fonctionelle ou encore impérative.

#### Utilisation de bibliothèque Objective-C

Un des inconvéniants lors du changement de langage de programmation pour une plateforme est le portage de toutes les bibliothèques écrites dans le langage précédant. Pour le développement sur iOS, ce problème a été contourné de manière intelligente: les bibliothèques écrites en Objective-C peuvent être utilisée telle quelle par l'application, à condition de fournir un petit fichier appelé "Bridging Header". Ce fichier permet à Swift de savoir quel type de fonction, d'objet et de classe il peut utiliser. Cela permet donc d'appeler des bibliothèques Objective-C depuis du Swift et éviter de devoir porter de grandes quantités de code.

#### Utilisation de bibliothèques externes






## Cahier des charges

Ce cahier des charges a été fourni par la RTS.

### Contexte

La RTS (Radio Télévision Suisse) propose à côté de son offre télévision / radio traditionnelle
une large gamme de produits en ligne : Play RTS, RTS Sport, RTS Info, RTS Radio, RTS
Kids.

La publication de contenus vidéos live a profondément changé récemment, avec l'arrivée
d'application mobile telles que Meerkat et Persicope. La RTS souhaite se doter d'un outil
permettant aux journalistes de publier immédiatement en live des vidéos sur le terrain.

### Objectifs

Ce travail consiste à offrir la possibilité aux journalistes de diffuser en direct de la vidéo
depuis leur téléphone.

#### Objectifs principaux

- Diffusion vidéo + audio en direct depuis un smartphone
- Intégration à l'application RTS Express iOS existante
- Authentification des utilisateurs par maRTS
- Possibilité d'ajouter des métadonnées : titre, description, mot clés
- Interface simple
- Possibilité de disposer d'un enregistrement du live.
- La qualité de la vidéo est aussi bonne que possible.
- Intégration dans le workflow vidéo RTS

#### Objectifs secondaires

- Intégration avec le centre de diffusion RTS / SSR
- Optimisation du temps de propagation (latence entre la captation et la diffusion)
- Module indépendant pouvant être intégré dans toutes les apps natives.
- Diffusion en parallèle sur YouTube

### Critères d'acceptation

- L'outil est simple d'utilisation
- L'outil est rapide
- Logiciel de qualité : code commenté et versionné, tests automatisés,...
- Sécurité des données bien maitrisée
- Projet déployé sur l'infrastructure RTS
- Résilience du logiciel aux coupures réseau
- Etude de différentes solutions techniques, notamment encodage de la vidéo en local / sur le serveur

### Remarque

Une bonne connaissance de plusieurs protocoles réseaux est un atout.

### Domaines de recherche

- Développement mobile
- Authentification
- Sécurité
- Programmation Orientée Objet
- UI / UX
- Gestion des médias
- Cloud
- Vidéo
- Compression vidéo
- Réseau






## Approche du problème

Mon approche du problème c'est déroulée de la manière suivante.

## Problèmes rencontrés

## Suite du projet

### Prochaines étapes

Les prochaines étapes de développement du projet peuvent être séparée en deux groupe et sont les suivantes:

**Gestion de la vidéo:**

- Découpe de la vidéo live en fragments à la volée
- Envoi des fragments vidéo sur un serveur distant
- Obtention une base de streaming vidéo fonctionnelle
- Enregitrement de la vidéo complète en haute qualité

**Application:**

- Design de l'interface utilisateur
- Implémentation de l'interface utilisateur
- Implémentation du système d'authenficiation
- Implémentation du système de métadonnées (titre, description, mot clés, etc.)
- Déploiement

### Analyse de risques



### Stratégie de mitigation des risques


