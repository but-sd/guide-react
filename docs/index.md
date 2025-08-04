# JSX

**J**ava**S**cript e**X**tension est une extension de JavaScript qui permet de créer des composants React de manière plus simple et plus lisible.

Elle permet de créer des composants React en utilisant une syntaxe proche du HTML et d'utiliser des expressions JavaScript dans le code HTML.

Dans une syntaxe javascript classique, il faut utiliser la fonction React.createElement pour créer un composant React. Cette fonction prend en paramètre le nom du composant React, les attributs du composant React et les enfants du composant React.

Voici un exemple de code React avec la syntaxe javascript classique :

```javascript
import React from "react";

function App() {
  return React.createElement("h1", {}, "Hello World");
}

export default App;
```

Avec la syntaxe JSX, il suffit d'utiliser des balises HTML pour créer un composant React. Il n'est pas nécessaire d'utiliser la fonction React.createElement.

Voici un exemple de code React avec la syntaxe JSX :

```javascript
function App() {
  return (<h1>Hello World from react with JSX</h1>);
}

export default App;
```

JSX permet d'avoir un code plus lisible et plus simple à écrire. Elle mélange la logique JavaScript et la structure HTML.

## Syntaxe

La syntaxe JSX est très proche de la syntaxe HTML. Elle permet de créer des composants React en utilisant des balises HTML.

### Commentaires

Les commentaires HTML ne sont pas valides en JSX. Il faut utiliser les commentaires JavaScript pour commenter du code JSX.

Pour commenter une ligne de code, il faut utiliser `//` :

```javascript
function App() {
  return (
    // Commentaire JSX
    <h1>Hello World</h1>
  );
}

export default App;
```

Si vous souhaitez commenter plusieurs lignes de code, il faut utiliser `/* */` :

```javascript
function App() {
  return (
    <>
      {/* Commentaire JSX */}
      <h1>Hello World</h1>
    </>
  );
}

export default App;
```

### Attributs

La syntaxe JSX permet d'utiliser des attributs HTML dans les composants React. Ces attributs sont utilisés pour définir les propriétés des composants React.

Voici un exemple de code React avec des attributs HTML :

```javascript
function App() {
  return (<h1 id="title">Hello World</h1>);
}

export default App;
```

Les attributs HTML s'écrivent de la même manière que les attributs HTML. Ils sont séparés par des espaces. Cependant il y a quelques différences entre les attributs HTML et les attributs JSX :

- Les attributs HTML sont écrits en minuscules, alors que les attributs JSX sont écrits en camelCase (la première lettre est en minuscule et les lettres suivantes sont en majuscules)
- Les `-` sont remplacés par une majuscule dans les attributs JSX.

Par exemple, l'attribut auto-complete s'écrit autoComplete en JSX.

L'attribut class du HTML à une particularité il s'écrit className en JSX. En effet, class est un mot réservé en JavaScript. Il n'est donc pas possible de l'utiliser en JSX.

Voici un exemple de code React avec l'attribut className :

```javascript
function App() {
  return (<h1 className="title">Hello World</h1>);
}

export default App;
```

### Elément racine

Il n'est pas possible d'utiliser plusieurs balises HTML dans un composant React. Il ne peut y avoir qu'une seule balise HTML racine dans un composant React.

Le code suivant n'est pas valide, car il y a deux balises HTML racines `<h1>` et `<p>`:

```javascript
function App() {
  return (
    <h1>Hello World</h1>
    <p>lorem ipsum</p>
  );
}

export default App;
```

Voici un exemple de code React avec une seule balise HTML racine, la balise `<div>` :

```javascript
function App() {
  return (
    <div>
      <h1>Hello World</h1>
      <p>lorem ipsum</p>
    </div>
  );
}

export default App;
```

Cette syntaxe n'est pas très pratique, car elle ajoute une balise HTML qui peut être inutile dans le DOM.

Si vous souhaitez utiliser plusieurs balises HTML dans un composant React, vous pouvez utiliser la balise React.Fragment. Cette balise permet de créer un composant React sans créer de balise HTML. Dans ce cas, il n'y a pas de balise HTML racine. Il existe une syntaxe raccourcie pour utiliser la balise React.Fragment, qui rend le code plus lisible. Il suffit d'utiliser les balises `<>` la balise fermante associée.

```javascript
function App() {
  return (
    <>
      <h1>Hello World</h1>
      <p>lorem ipsum</p>
    </>
  );
}

export default App;
```

### Balises fermantes

Il n'est pas possible d'utiliser des balises HTML qui ne sont pas fermées dans un composant React.

Voici un exemple de code React non valide avec une balise HTML non fermée :

```javascript
function App() {
  return (<img src="logo.png">);
}

export default App;
```

Afin de rendre le code plus lisible, il est possible d'utiliser la syntaxe raccourcie pour les balises HTML qui ne sont pas fermées. Il suffit d'ajouter un `/` à la fin de la balise HTML.

```javascript
function App() {
  return (<img src="logo.png" />);
}

export default App;
```

### Interpolation

L'interpolation est une fonctionnalité de JSX qui permet d'utiliser des expressions JavaScript dans les composants React. Ces expressions JavaScript sont utilisées pour définir les propriétés des composants React.

Voici un exemple de code React avec des expressions JavaScript :

```javascript

function App() {
  // Définition d'une variable
  const title = "Hello World";

  // Utilisation de la variable dans le composant React
  return (<h1>{title}</h1>);
}

export default App;
```

L'interpolation est aussi utilisée pour écrire le style CSS dans les composants React. Il faut dans ce cas une double accolade, une première accolade pour indiquer que l'on utilise une expression JavaScript et une deuxième accolade pour indiquer que l'on utilise un objet JavaScript.

Le nom des propriétés CSS s'écrit en camelCase. Par exemple, l'attribut background-color s'écrit backgroundColor.

```javascript
function App() {
  return (<h1 style={{color: "red", backgroundColor: "blue"}}>Hello World</h1>);
}

export default App;
```

On peut utiliser des variables pour définir les propriétés CSS.

```javascript

// Définition d'une variable qui contient un objet JavaScript ayant des propriétés CSS
const style = {
  color: "red",
  backgroundColor: "blue"
};

function App() {
  // Utilisation de la variable dans le composant React
  return (<h1 style={style}>Hello World</h1>);
}

export default App;
```

### Evénements

Comme en HTML, il est possible d'ajouter des événements aux composants React. Ces événements sont utilisés pour définir le comportement des composants React. 

```javascript

function App() {
  // Définition d'une fonction qui affiche un message dans la console
  function handleClick() {
    console.log("Hello World");
  }

  // Déclenchement de la fonction au clic sur le composant React
  return (<h1 onClick={handleClick}>Hello World</h1>);
}

export default App;
```

### Condition

Il est possible d'utiliser des conditions dans les composants React. Ces conditions sont utilisées pour afficher ou non des éléments dans les composants React. Ou pour afficher des éléments différents dans les composants React selon une condition.

**Condition binaire**

```javascript
function App() {
  // Définition d'une variable  
  const isLogged = true;

  return (
    <>
      {
        // Condition binaire basée sur la variable isLogged
        isLogged && <h1>Hello World</h1>
    }
    </>
  );
}

export default App;
```

**condition ternaire**

```javascript
function App() {
  const isLogged = true;

  return (
    <>
      {
        // Condition ternaire basée sur la variable isLogged
        isLogged ? <h1>Hello World</h1> : <p>you are not logged</p>
      }
    </>
  );
}

export default App;
```

Dans les deux exemples précédents, la condition est basée sur une variable. Cela sembe inutile car la variable est définie directement dans le composant React. Cependant, dans la plupart des cas, la condition est basée sur une propriété du composant React.

### Boucle

Il est possible d'utiliser des boucles dans les composants React. Ces boucles sont utilisées pour afficher une liste d'éléments dans les composants React.

Dans l'exemple suivant, nous utilisons la méthode map pour afficher une liste d'utilisateurs dans le composant React. Le composant React affiche une balise `<p>` pour chaque utilisateur.

Remarque : il faut ajouter un attribut key pour chaque élément de la boucle. Cet attribut permet à React de savoir quel élément a été modifié.

```javascript

function App() {
  const users = [
    {id: 1, name: "John"},
    {id: 2, name: "Jane"},
    {id: 3, name: "Jack"}
  ];

  return (
    <>
      {users.map(user => <p key={user.id}>{user.name}</p>)}
    </>
  );
}

export default App;
```

### Composants

Créer un composant, c'est créer une fonction qui retourne du JSX. Il faut respecter la convention de nommage des composants React. Le nom des composants React doit commencer par une majuscule.

Le but d'un composant React est de créer un élément qui peut être réutilisé dans d'autres composants React. Cela permet de créer des composants React plus facilement et de rendre le code plus lisible. 

Un composant React peut être utilisé dans un autre composant React en utilisant la syntaxe suivante : `<NomDuComposant />`.

Le composant peut être utilisé plusieurs fois dans le même composant React.

Le composant étant une simple fonction Javascript, il est possible de l'exporter et de l'importer dans un autre fichier. Cela permet de créer des composants React dans des fichiers séparés, qui peuvent être réutilisés dans d'autres composants React. C'est par exemple le cas du composant `<App />` qui est défini dans le fichier App.js et qui est utilisé dans le fichier index.js.

Cela permet de rendre le code plus lisible et de faciliter la maintenance du code. 

```javascript

// Création d'un composant React personnalisé
function Title() {
  return (<h1>Hello World</h1>);
}

function App() {
  return (
    <>
      {/* Utilisation du composant React personnalisé */}
      <Title />
    </>
  );
}

export default App;
```

**Passer des propriétés à un composant**

Un composant React étant une simple fonction JavaScript, il est possible de passer des propriétés à un composant React. 

Par exemple dans le composant `<Title />`, nous pouvons passer une propriété color pour définir la couleur du titre. Les propriétés sont passées au composant React en utilisant la syntaxe suivante : `<NomDuComposant nomDeLaPropriete="valeur" />`.

Comme pour une fonction JavaScript, il est possible de définir une valeur par défaut pour une propriété. 

Dans l'exemple suivant la propriété color a une valeur par défaut rouge. Si la propriété color n'est pas définie, la valeur par défaut sera utilisée.
On peut aussi passer une propriété sans valeur. Dans ce cas, la valeur de la propriété est un booléen qui sera true si la propriété est définie et false si la propriété n'est pas définie.

```javascript
function Title({ color = 'red', hidden = false }) {
  return (<h1 style={{color: color}}>Hello World</h1>);
}

function App() {
  return (
    <>
      <Title color="blue" hidden />
    </>
  );
}

export default App;
```

**La propriété children**

La propriété children est une propriété particulière. Elle permet de définir le contenu d'un composant React. Ce contenu peut être du texte ou d'autres composants React.

```javascript

function Title({ color = 'red', children, hidden = false }) {
  if (hidden) {
      return null;
  }

  return (<h1 style={{color: color}}>{children}</h1>);
}

function App() {
return (
  <>
    <Title color="blue" hidden>Hello World</Title>
  </>
);
}

export default App;
```

**spread operator**

Le spread operator permet de passer toutes les propriétés d'un objet à un composant React. Cela permet de rendre le code plus lisible et de faciliter la maintenance du code.

```javascript
function Title({ color = 'red', children, hidden = false, ...props }) {
  if (hidden) {
      return null;
  }

  return (<h1 style={{color: color}} {...props}>{children}</h1>);
}

function App() {
return (
  <>
    {/* 
        La propriété id et data-demo sont passées au composant Title grâce au spread operator.
        La propriété color est définie dans le composant Title
     */}
    <Title color="blue" id="my-id" data-demo="demo">Hello World</Title>
  </>
);
}

export default App;
```