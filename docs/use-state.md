# useState

Gestion de l'état dans un composant.

L'état d'un composant est une donnée qui peut changer au cours du temps. Par exemple, dans une application de compteur, l'état du composant est le nombre de clics sur le bouton.

## Déclaration

La fonction `useState` permet de gérer l'état dans un composant. Elle prend en paramètre la valeur initiale de l'état et retourne un tableau contenant la valeur de l'état et une fonction pour modifier la valeur de l'état.

```js
const [state, setState] = useState(initialState);
```

## Exemple

```js
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Vous avez cliqué {count} fois</p>
      <button onClick={() => setCount(count + 1)}>
        Cliquez ici
      </button>
    </div>
  );
}
``` 

Il est possible de ressortir la fonction de l'événement `onClick` dans une fonction à part.

```js
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  const handleClick = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Vous avez cliqué {count} fois</p>
      <button onClick={handleClick}>
        Cliquez ici
      </button>
    </div>
  );
}
```

Si l'on souhaite passer des paramètres à la fonction `handleClick`, il faut utiliser une fonction fléchée. Par exemple si l'on souhaite ajouter 1 à la valeur de l'état, il faut écrire :

```js
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  const handleClick = (value) => {
    setCount(count + value);
  };

  return (
    <div>
      <p>Vous avez cliqué {count} fois</p>
      <button onClick={() => handleClick(1)}>
        Cliquez ici
      </button>
    </div>
  );
}
```

Il est possible de gérer plusieurs états dans un composant. Pour cela, il suffit d'appeler la fonction `useState` plusieurs fois.

```js
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  const [name, setName] = useState('John Doe');

  const handleClick = (value) => {
    setCount(count + value);
  };

  const handleChange = (event) => {
    setName(event.target.value);
  };

  return (
    <div>
      <p>Vous avez écrit: {name}</p>
      <p>Vous avez cliqué {count} fois</p>
      <button onClick={() => handleClick(1)}>
        Cliquez ici
      </button>
      <input type="text" value={name} onChange={handleChange} />
    </div>
  );
}
```

Dans l'exemple du champ de saisie du nom, nous accèdons à l'objet `event` qui contient la valeur de l'input. Pour récupérer la valeur de l'input, il faut utiliser `event.target.value`. Cet objet `event` est passé automatiquement par React à la fonction `handleChange`.

## Mutable vs Immutable

L'état d'un composant est immutable. Cela signifie que l'on ne peut pas modifier directement la valeur de l'état. Par exemple, si l'on souhaite ajouter 1 à la valeur de l'état, il faut écrire :

```js
const handleClick = () => {
  setCount(count + 1);
};
```

et non pas :

```js
const handleClick = () => {
  count = count + 1;
};
```

De même pour un tableau, si l'on souhaite ajouter un élément à un tableau, il faut écrire :

```js
const handleClick = () => {
  setList([...list, 'element']);
};
```

et non pas :

```js
const handleClick = () => {
  list.push('element');
};
```

Pour un objet, si l'on souhaite ajouter une propriété à un objet, il faut écrire :

```js
const handleClick = () => {
  setObj({ ...obj, key: 'value' });
};
```

et non pas :

```js
const handleClick = () => {
  obj.key = 'value';
};
```


<!-- ## TODO 

```js

import React, { useState } from 'react';

function Example() {
    const [name, setName] = useState('');
    const [list, setList] = useState([]);

    const handleChange = (event) => {
        setName(event.target.value);
    };

    const handleAdd = () => {
        setList((prevList) => [...prevList, name]);
        setName('');
    };

    return (
        <div>
            <input type="text" value={name} onChange={handleChange} />
            <button onClick={handleAdd}>Add</button>
            <ul>
                {list.map((item, index) => (
                    <li key={index}>{item}</li>
                ))}
            </ul>
        </div>
    );
}

``` -->
