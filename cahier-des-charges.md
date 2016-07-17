
# Cahier des charges

Ce cahier des charges a été fourni par Sébastien Noir, chef de projet à la RTS.

## Contexte

La RTS (Radio Télévision Suisse) propose à côté de son offre télévision / radio traditionnelle
une large gamme de produits en ligne : Play RTS, RTS Sport, RTS Info, RTS Radio, RTS
Kids.

La publication de contenus vidéos live a profondément changé récemment, avec l'arrivée
d'application mobile telles que Meerkat et Persicope. La RTS souhaite se doter d'un outil
permettant aux journalistes de publier immédiatement en live des vidéos sur le terrain.

## Objectifs

Ce travail consiste à offrir la possibilité aux journalistes de diffuser en direct de la vidéo
depuis leur téléphone.

### Objectifs principaux

- Diffusion vidéo + audio en direct depuis un smartphone
- Intégration à l'application RTS Express iOS existante
- Authentification des utilisateurs par maRTS
- Possibilité d'ajouter des métadonnées : titre, description, mot clés
- Interface simple
- Possibilité de disposer d'un enregistrement du live.
- La qualité de la vidéo est aussi bonne que possible.
- Intégration dans le workflow vidéo RTS

### Objectifs secondaires

- Intégration avec le centre de diffusion RTS / SSR
- Optimisation du temps de propagation (latence entre la captation et la diffusion)
- Module indépendant pouvant être intégré dans toutes les apps natives.
- Diffusion en parallèle sur YouTube

## Critères d'acceptation

- L'outil est simple d'utilisation
- L'outil est rapide
- Logiciel de qualité : code commenté et versionné, tests automatisés,...
- Sécurité des données bien maitrisée
- Projet déployé sur l'infrastructure RTS
- Résilience du logiciel aux coupures réseau
- Etude de différentes solutions techniques, notamment encodage de la vidéo en local / sur le serveur

## Domaines de recherche

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