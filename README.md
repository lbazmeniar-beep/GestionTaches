# Gestion d'une liste de tâches

## Description

Cette application Vue.js permet de gérer une liste de tâches.

## Fonctionnalités

* Ajouter une tâche.
* Refuser les tâches vides ou composées uniquement d'espaces.
* Marquer une tâche comme terminée.
* Afficher le texte d'une tâche terminée en barré.
* Supprimer une tâche.
* Afficher automatiquement le nombre de tâches restantes.
* Afficher « Aucune tâche pour le moment » lorsque la liste est vide.

## Technologies utilisées

* Vue.js 3
* JavaScript
* Vite

## Installation des dépendances

```bash
npm install
```

## Lancement du projet

```bash
npm run dev
```

Ouvrir ensuite l'adresse locale affichée dans le terminal.

## Explication des éléments Vue.js

* **ref :** permet de créer des données réactives.
* **v-model :** relie un champ de saisie ou une case à cocher à une donnée.
* **v-for :** permet d'afficher toutes les tâches du tableau.
* **:key :** permet d'identifier chaque tâche de manière unique dans la liste.
* **computed :** calcule automatiquement le nombre de tâches non terminées.
* **@submit.prevent :** exécute la fonction du formulaire sans recharger la page.
* **@click :** exécute une fonction lorsqu'on clique sur un bouton.

## Vérification

Pour vérifier le projet, exécuter `npm install`, puis `npm run dev`.
