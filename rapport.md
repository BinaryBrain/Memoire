# Travail de Bachelor

## Sommaire

- Préambule
- État de l'art
	- Introduction au diffusion vidéo en direct
		- Utilisation d'HTTP
		- RTMP
		- HLS
		- MPEG-DASH
	- Introduction au développement sur iOS
		- Swift
		- Utilisation de bibliothèque Objective-C
		- Utilisation de bibliothèques externes
- Cahier des charges
	- Contexte
	- Objectifs
		- Objectifs principaux
		- Objectifs secondaires
	- Critères d'acceptation
	- Remarque
	- Domaines de recherche
- Approche du problème
	- Capture vidéo
	- Conversion vidéo
	- Envoi de données
- Suite du projet
	- Prochaines étapes
	- Analyse de risques
	- Stratégie de mitigation des risques

## Préambule

Dans le monde d'aujourd'hui, l'information instantanée prend de plus en plus d'ampleur à travers divers vecteurs. Les différents réseaux sociaux soutiennent ce mouvement en incitant son public à partager du texte, des clichés ou encore de la vidéo. En effet, de nombreuses applications et sites web voient le jour chaque année. Parmi eux, les plus connus sont Twitch.tv: un site web de diffusion vidéo en direct utilisé surtout par les amateurs de jeu vidéo, Periscope: une application mobile permettant la diffusion en direct depuis la caméra du smartphone vers d'autres smartphones à travers le monde, et la majorité des grands acteurs du web ont ajouté cette fonctionnalité à leurs sites web: YouTube, Facebook, Snapchat, etc.

Ce phénomène contraint les médias "classiques" à continuer à s'adapter aux nouvelles technologies de communication. La diffusion d'information en direct prend alors une place de plus en plus importante afin de d'atteindre ce nouveau public friand d'instantané. La RTS (Radio Télévision Suisse) fait parti de ces médias dont la popularité est en jeu. Il n'est donc pas étonnant qu'ils souhaitent aussi participer à l'expension de cette nouvelle manière de partager l'information. Bien évidemment, les émissions et retransmission d'évenements en direct n'est pas chose nouvel pour une chaîne de télévision mais la différence réside aussi dans la manière de procéder. En effet, en ayant une application de diffusion en direct sur leurs téléphones, les journalistes ont la libérté de créer du contenu à tout moment et sans préparation. Cela peut-être très pratique pour émettre les images d'un festival de musique, d'un incendie qui vient de débuter ou encore d'interviewer une célébrité que l'on croiserait par hasard.

C'est pourquoi la RTS a proposé à l'HEIG-VD un travail de Bachelor ayant pour sujet la création d'une application pour iPhone permettant la diffusion en direct des images perçue par sa caméra, envoloppé dans une interface donnant la posibilité aux journalistes de s'authentifier, ainsi que d'ajouter des informations utiles concernant la capture.

## État de l'art

Cette section présente divers aspects factuels sur la diffusion de la vidéo en direct et du développement sur iOS.

### Introduction au diffusion vidéo en direct

La diffusion de vidéo en direct reste quelque chose de techniquement difficile à réaliser pour plusieurs raisons.

Tout d'abord, les fichiers vidéo comportent beaucoup de données et sont donc rapidement volumineux. Cela entraîne alors d'autres problèmes: le réseau de communication utilisé doit être capable de gérer un débit minimal afin que le temps de transmission des fichiers vidéos ne soit pas plus long que la durée de la vidéo envoyée.

Pour ce travail, nous nous concentrerons uniquement sur les systèmes de streaming vidéo de type serveur-clients dans lesquels la latence n'est pas une priorité majeure et non les protocoles peer-to-peer et temps réel utilisés, par exemple, pour la vidéoconférence.

#### Utilisation d'HTTP

Les protocoles de streaming vidéo les plus répandus sont sans doute ceux basé sur HTTP.

L'avantage principal d'utiliser HTTP réside dans le fait que c'est un protocol de la couche applicative du modèle OSI. Ce niveau supplémantaire d'abstraction par rapport aux couches plus basses du modèle OSI signifie que le flux vidéo peut passer par des proxys HTTP et passer à travers les les pare-feux permissif à HTTP, contrairement à TCP ou UDP qui se situe sur des couches plus basses du modèle OSI, par exemple.

En outre, ses inconvéniants majeurs sont les contraintes qu'ils présentent quant à la manière de gérer les données. Par exemple, un protocole de diffusion de vidéo basé sur UDP pourraient simplement envoyer le flux de bytes de la vidéo à travers le réseau avec peu de traitements sur les données. Par contre, avec l'utilisation d'HTTP, les données doivent être contenues dans des fichiers. La vidéo doit alors être découpée en une mulitude de fichiers vidéo, aussi appelés fragments, qui seront envoyés un par un sur le réseau. Cette contraite nous oppose à plusieurs choix, dont celui de la durée de ces fragments de vidéo. En effet, si les fragments sont trop longs, la latence entre la capture de l'image et sa récéption va fortement augmenter car le smartphone devra attendre que le fragment soit complet avant de l'envoyer, et son visionage ne pourra commencer qu'à ce moment-là.

#### RTMP

RTMP (Real-Time Messaging Protocol) est un protocol de communication permettant le streaming de vidéo. Il a été développé par Macromedia (aujourd'hui Adobe) et se base sur un client en Flash. Il est basé sur HTTP et utilise des vidéos au format FLV (Flash Video) et de l'audio en MP3 ou AAC.

Les principaux inconvéniants de ce protocol est qu'il est très lié aux clients Flash et que ces derniers sont aujourd'hui de plus en plus remplacés par les technologies HTML5. De plus, même si ce protocol est largement documenté, il est propriétaire.

RTMP est aujourd'hui utilisé par beaucoup de plateforme de streaming vidéo, comme Twitch.tv ou encore Periscope.

#### HLS

HLS (HTTP Live Streaming) est un système de streaming vidéo développé par Apple et basé sur HTTP. Il utilise un conteneur MPEG-2 TS et le codec H.264 pour ses fragments vidéo et supporte le MP3 et le AAC pour le transport du son.

#### MPEG-DASH

MPEG-DASH (MPEG pour Moving Picture Experts Group et et DASH pour Dynamic Adaptive Streaming over HTTP) est un système de streaming vidéo, également basé sur HTTP. Contrairement à RTMP et à HLS, MPEG-DASH ne dépend d'aucun codec. De plus, il supporte plusieurs format de conteneur. Il est alors capable d'envoyer des vidéos en MPEG-2 TS (comme HLS) ainsi que du MPEG-4 et les formats similaires.

### Introduction au développement sur iOS

Le développement sur iOS se fait par le biais de XCode, l’IDE d’Apple constituant l’unique environnement de développement officiel pour le développement d'application. C'est un IDE très complet offrant des outils de création d'interfaces, de gestion de projet, de diagnostique, ainsi qu'un simulateur d'iPhone permettant de tester la majorité des applications.

#### Swift

Swift est un langage de programmation conçu et maintenu par Apple. Sorti il y a environ 2 ans, il est en train de remplacer l'utilisation d'Objective-C pour la programmation sur iOS. C'est un langage moderne à la syntaxe épurée dont on retrouve les concepts dans certains autres langages modernes tel que Scala, C# ou encore Rust. Comme ces derniers, il est multi-paradigm, et permet donc de faire de la programmation orientée objet, de la programmation fonctionelle ou encore impérative.

#### Utilisation de bibliothèque Objective-C

Un des inconvéniants lors du changement de langage de programmation pour une plateforme est le portage de toutes les bibliothèques écrites dans le langage précédant. Pour le développement sur iOS, ce problème a été contourné de manière intelligente: les bibliothèques écrites en Objective-C peuvent être utilisée telle quelle par l'application, à condition de fournir un petit fichier appelé "Bridging Header". Ce fichier permet à Swift de savoir quel type de fonction, d'objet et de classe il peut utiliser. Cela permet donc d'appeler des bibliothèques Objective-C depuis du Swift et éviter de devoir porter de grandes quantités de code.

Une des problèmes de cette méthode est que nous devrions appeler les fonctions Objective-C en leur passant des types Objective-C depuis Swift. Il pourrait être alors problématique de convertir les variables typées en Swift en types Objective-C. Heureusement, Swift est capable de convertir implicitement les types les plus communs. Par exemple, une `String` pourra être implicitement convertie en `NSString` pour que le code en Objective-C puisse l'interpréter correctement.

#### Utilisation de bibliothèques externes

L'utilisation de bibliothèques externes est légèrement plus complexe. En effet, il est d'abord nécessaire de _cross-compilé_ les bibliothèques pour supporter les processeurs des différentes versions de l'iPhone (arm64, armv7, armv7s). Il peut alors être pratique d'utiliser la commande `lipo` disponible sous Mac OS X afin de fusionner les multiples compilations de la bibliothèque en un seul fichier.

Une fois la bibliothèque compilée pour l'iPhone, nous pouvons l'inclure dans XCode et également inclure les en-têtes de la bibliothèque. Ces en-têtes peuvent alors être ajouté au Bridging Header pour être appelé par Swift.

Au niveau des types de variables, Swift est aussi capable de comprendre et convertir les variables issues de C, par exemple.

## Cahier des charges

Ce cahier des charges a été fourni par Sébastien Noir, chef de projet à la RTS.

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

Comme la plupart des technologies susmentionnées m'étaient inconnues avant de commencer ce travail, j'ai commencé par me documenter et faire des recherches sur l'état de l'art ainsi que sur le futur de ces différents systèmes. En effet, ce genre d'application étant relativement moderne, il est utile d'essayer de prédire comment vont se développer les technologies de diffusion vidéo ainsi que leur support. Par exemple, l'abandon progressif des technologies Flash au profit d'HTML5 par les navigateurs constitue un paramètre non négligeable dans la création d'application de demain.

Une fois bien documenté, j'ai commencé à rechercher s'il existait déjà des bibliothèques ou des frameworks libres et/ou gratuit permettant de mettre en place un système de streaming depuis l'iPhone mais la grande majorité de ses systèmes sont payants, très souvent par mois, et incluent tout l'écosystème (application(s), serveurs cloud, parfois même client(s)).  
Je me suis d'abord penché sur les possiblité qu'offre AVFoundation, un framework d'audio-visuel fourni par Apple. Cependant, j'ai trouvé celui-ci relativement incomplet par rapport à l'utilisation particulière de la vidéo pour ce projet.  
J'ai alors choisi d'utiliser FFmpeg pour les transformations sur la vidéo (débit binaire, encodage, conteneur, fusion) car c'est une bibliothèque très largement utilisée, aussi par les grandes entreprises, qu'elle permet de faire toute les opérations désirées. En outre, le projet actif depuis plus de 15 ans, ce qui est signe d'une grande stabilité et qu'il y a beaucoup de chance qu'elle continue à être supportée dans les années à venir.

Comme je ne connaissais ni l'environnement de programmation sur iOS, ni le langage Swift, je me suis documenté et familiarisé avec celui-ci. J'ai ensuite développé des petites applications simple pour mieux comprendre comment utiliser les divers outils offert par Apple. Cela m'a aussi permis de comprendre des subtilité de Swift.

J'ai ensuite développé quelques prototypes d'application afin de tester si la direction dans laquelle je partais étais la bonne.

### Capture vidéo

La première partie que j'ai voulu testé est la capture de la vidéo à l'aide de la caméra du téléphone ainsi que son affichage à l'écran.

La capture vidéo nécessite l'utilisation du framework AVFoundation. Il permet, entre autres, une gestion avancée de la caméra (résolution, balance des blancs, ISO, etc.).

Les fichiers enregistré peuvent l'être au format MPEG-4 (_.mp4_) ou Quicktime (_.mov_). Étant donné que MPEG-DASH semble supporter le MPEG-4, j'ai choisi d'enregistrer dans ce format.

### Conversion vidéo

Le prototype de conversion vidéo est celui qui m'a posé le plus de problème dans ce projet, mais il m'a aidé à comprendre beaucoup de chose par la pratique.

La partie qui m'a posé le plus de difficulté était sans doute d'appeler les différentes fonctions de FFmpeg depuis mon code Swift. En effet, je n'avais jamais essayer de lier des bibliothèques externes à XCode et à Swift. Lorsque j'ai rencontré des erreurs à la compilation lors de l'appel au linker, il m'était impossible de savoir d'où provenait l'erreur. Elle pouvait se trouver sur une multitude de niveaux:

- La cross-compilation
- La fusion des bibliothèques statiques
- Leur inclusion au projet XCode
- La configuration de mon projet XCode (tant au niveau des libs que des headers)
- L'utilisation du Bringing Header
- L'appel aux fonctions depuis Swift

De plus, certaines erreurs du linker provenaient du fait que FFmpeg a besoin des bibliothèques libssl, libcrypto et libiconv.

Finalement, après de nombreux essais et renseignements sur Internet, j'ai pu convertir des vidéos d'un format à l'autre, changeant non seulement le format du conteneur mais aussi le codec utilisé.

Ce prototype m'a pris de nombreuses heures à faire fonctionner parce que l'ensemble du système comporte de nombreuses couches et aussi à cause de mon manque d'expérience sur ces technologies. Cepandant, la gestion de la vidéo est une clé de voute de ce projet et ce prototype et les problèmes qu'il m'a causé m'aideront beaucoup dans la réalisation de l'application finale.

### Envoi de données

Comme mentionné précédement, l'envoi des fragments vidéo se fait via HTTP. Le développement d'une petite application envoyant une requête de type POST sur un serveur et contenant un payload m'a permi de testé cette fonctionnalité.

## Suite du projet

Pour la suite du projet, la partie de prototypage touchera à sa fin assez rapidement et il faudra développer une application stable en se basant sur les connaissances aquises lors des dernières semaines.

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


