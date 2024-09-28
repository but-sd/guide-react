---
hide:
  - navigation
  - toc
---

# react

React est une librairie JavaScript développée par Facebook et Instagram. Elle permet de créer des interfaces utilisateurs interactives et dynamiques. Elle est utilisée par de nombreux sites web et applications, comme Facebook, Instagram, Netflix, Airbnb, Uber, etc.

React est une librairie JavaScript, et non un framework. Cela signifie qu'elle ne fournit pas de structure ou de méthodologie pour organiser votre code. Elle ne fournit pas non plus de fonctionnalités pour gérer les requêtes HTTP, les routes, etc. Elle se concentre uniquement sur la création d'interfaces utilisateurs.

React est une librairie open source, et est donc gratuite. Elle est distribuée sous licence MIT.

## Pourquoi utiliser React ?

React est une librairie très populaire, et est utilisée par de nombreux sites web et applications. Elle est donc très bien maintenue, et dispose d'une grande communauté. Il existe de nombreux tutoriels, articles, vidéos, etc. pour vous aider à apprendre React.

React est également très performant. Il est conçu pour être rapide, et pour gérer efficacement les mises à jour de l'interface utilisateur. Il est également très flexible, et peut être utilisé pour créer des interfaces utilisateurs simples ou complexes.

## Prérequis

Pour pouvoir utiliser React, il faut avoir des connaissances en HTML, CSS et JavaScript.

## Concepts

Une interface utilisateur est composée de plusieurs éléments appelés composants. Un composant est une partie de l'interface utilisateur qui peut être réutilisée plusieurs fois dans l'application.

```text
+-----------------------+
|       App Component   |
|                       |
|   +---------------+   |
|   |   Header      |   |
|   +---------------+   |
|   |   Main        |   |
|   +---------------+   |
|   |   Footer      |   |
|   +---------------+   |
|                       |
+-----------------------+
```

Dans ce schéma, l'application est composée de trois composants : Header, Main et Footer. Chaque composant peut être réutilisé plusieurs fois dans l'application.
Par exemple, le composant Header peut être utilisé dans la page d'accueil et dans la page de contact.

Un composant peut être composé d'autres composants. Par exemple, le composant App est composé des composants Header, Main et Footer.

On peut voir les composants comme des Lego. Chaque composant est un bloc de construction qui peut être réutilisé plusieurs fois dans l'application.

## Installation

React propose deux méthodes pour installer React sur votre machine.

### Installation avec un CDN

La première méthode consiste à utiliser un CDN (Content Delivery Network) pour récupérer les fichiers nécessaires à l'utilisation de React. Pour cela, il suffit d'ajouter les lignes suivantes dans le `<head>` de votre fichier HTML :

```html
<!-- React -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/react/16.8.6/umd/react.production.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/react-dom/16.8.6/umd/react-dom.production.min.js"></script>
```

Cette méthode est la plus simple à mettre en place, mais elle ne permet pas de profiter de toutes les fonctionnalités de React. 

### Installation avec create-react-app

React propose une deuxième méthode pour installer React sur votre machine. Cette méthode consiste à utiliser un outil appelé create-react-app. Cet outil permet de créer une application React en quelques secondes.

Pour installer create-react-app, il suffit d'ouvrir un terminal et de taper la commande suivante :

```bash
npx create-react-app my-app
cd my-app
```

Cette commande va créer un dossier my-app dans le dossier courant. Ce dossier contiendra tous les fichiers nécessaires à l'utilisation de React.

Pour lancer l'application React, il suffit d'ouvrir un terminal et de taper la commande suivante :

```bash
npm start
```

Cette commande va lancer l'application React dans le navigateur par défaut. L'application React est accessible à l'adresse suivante : http://localhost:3000. 

La fonctionnalité de live-reload est activée par défaut. Cela signifie que si vous modifiez un fichier, l'application React sera automatiquement rechargée dans le navigateur.

### Structure d'un projet React

Un projet React créé avec create-react-app contient un ensemble de fichiers et de dossiers qui permettent de développer une application React. Nous verrons dans les prochains chapitres à quoi servent ces fichiers et dossiers.

Voici la liste des fichiers et dossiers d'un projet React créé avec create-react-app :

- `node_modules` : ce dossier contient les dépendances de l'application React. 
- `public` : ce dossier contient les fichiers statiques de l'application React.
- `src` : ce dossier contient les fichiers sources de l'application React. C'est dans ce dossier que nous allons développer notre application React.
- `.gitignore` : ce fichier contient la liste des fichiers et dossiers à ignorer par Git.
- `package.json` : ce fichier contient la liste des dépendances de l'application React.
- `package-lock.json` : ce fichier contient la liste des dépendances de l'application React.
- `README.md` : ce fichier contient la documentation de l'application React. Nous modifierons ce fichier dans les prochains chapitres.

## Outils de développement

React propose un ensemble d'outils de développement qui permettent de développer une application React plus facilement.

### React Developer Tools

React Developer Tools est une extension pour Chrome et Firefox qui permet d'inspecter les composants React d'une application React.

Pour installer React Developer Tools, il suffit d'ouvrir le Chrome Web Store ou le Firefox Add-ons Store et de rechercher React Developer Tools. Une fois l'extension installée, il suffit de l'activer pour qu'elle soit disponible dans le navigateur.
