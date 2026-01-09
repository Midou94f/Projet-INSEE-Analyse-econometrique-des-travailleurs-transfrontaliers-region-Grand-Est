# Projet INSEE — Mobilité transfrontalière des travailleurs du Grand Est

## **IMPORTANT Accès aux données INSEE (coupe 2022)**

1. Aller sur le site de l’INSEE.  
2. Dans la barre de recherche, taper :  
   **« Logements, individus, activité, mobilités scolaires et professionnelles, migrations résidentielles en 2022 »**  
3. Télécharger les bases suivantes :
   - **« Individus localisés au canton-ou-ville »** (recensement) - Année 2022
   - **« Mobilités professionnelles des individus »** (MOB-PRO) - région grand-est uniquement

Pour travailler sur une autre année, il suffit de modifier l’année dans la recherche.

****

## Objectif du projet
Ce projet vise à analyser les déterminants socio-économiques et géographiques de la **probabilité d’être travailleur transfrontalier** pour les résidents de la région Grand Est, à partir des micro-données du Recensement de la population 2022 (INSEE).

L’ambition est double :
- produire une **base de données harmonisée et économétriquement exploitable** malgré de fortes contraintes de structure et de confidentialité,
- estimer et interpréter rigoureusement les **facteurs individuels, professionnels et familiaux** associés à la mobilité transfrontalière.

---

## Données mobilisées
Le projet repose sur l’appariement de deux fichiers issus du recensement :

- **INDCVI** : fichier individus (population totale),
- **MOBPRO** : fichier mobilité professionnelle (actifs en emploi).

Ces fichiers fournissent des informations détaillées sur :
- caractéristiques socio-démographiques (âge, sexe, diplôme, structure familiale),
- statut professionnel et conditions d’emploi,
- modes de transport et lieu de travail,
- localisation géographique fine (IRIS, département, région),
- pondérations statistiques individuelles (IPONDI).

---

## Enjeux méthodologiques clés

### Appariement MOBPRO – INDCVI
L’appariement constitue le cœur technique du projet et repose sur :
- l’absence de clé individuelle directe,
- des niveaux géographiques hétérogènes (IRIS, commune, pseudo-canton),
- la présence de communes non irisées,
- des pondérations distinctes selon les fichiers.

Les choix méthodologiques sont **explicitement documentés**, notamment les arbitrages conduisant à un **biais de sélection géographique assumé**, traité analytiquement dans l’interprétation des résultats.

### Reconstitution des couples
Une étape spécifique du travail consiste à :
- **reconstituer les couples au sein des ménages** à partir des variables de structure familiale et de liens au sein du ménage,
- identifier les couples bi-actifs et leurs caractéristiques individuelles respectives,
- permettre une analyse conjointe des décisions de mobilité professionnelle.

Cette reconstitution est indispensable pour l’analyse bivariée finale.

---

## Méthodologie

### 1. Préparation et harmonisation des données
- nettoyage et recodage cohérent des variables,
- gestion des modalités résiduelles et valeurs manquantes,
- harmonisation des concepts entre fichiers.

### 2. Appariement déterministe contrôlé
- clés géographiques et socio-démographiques,
- diagnostics ex-ante et ex-post (distributions, écarts, contrôles de cohérence),
- intégration de la reconstitution des couples.

### 3. Sélection de variables
- utilisation de méthodes pénalisées (LASSO / Elastic Net),
- usage strictement exploratoire et **en appui de l’économétrie**,
- aucune substitution aux modèles structurels.

---

## Analyse économétrique finale

L’analyse repose sur des modèles Probit estimant la probabilité d’être travailleur transfrontalier.

### Modèle 1 — Probit simple
- Variable dépendante : être travailleur transfrontalier (oui / non),
- estimation des déterminants individuels, professionnels et territoriaux,
- interprétation des effets marginaux.

### Modèle 2 — Probit avec interactions (genre)
- introduction d’interactions permettant d’analyser le **gap femme–homme**,
- mise en évidence d’éventuelles hétérogénéités de comportement selon le sexe,
- comparaison des effets marginaux conditionnels.

### Modèle 3 — Analyse bivariée au sein des couples
- modèle bivarié portant sur la **décision conjointe des couples**,
- analyse de la corrélation des décisions de travail transfrontalier,
- prise en compte de la structure familiale et des arbitrages intra-ménage.

---

## Finalité du dépôt GitHub

Ce dépôt a pour vocation de :
- garantir la **traçabilité complète** du traitement des données,
- documenter précisément les choix méthodologiques,
- assurer la **reproductibilité** des résultats,
- servir de support académique (mémoire, rapport, présentations).

---

## Remarque importante

Ce projet s’inscrit dans une démarche académique rigoureuse :  
les résultats doivent être interprétés à la lumière des contraintes de données, des choix d’appariement et des biais potentiels explicitement identifiés.
