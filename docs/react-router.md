# react-router

Le router est un composant qui permet de gérer la navigation dans une application React. Il permet de définir des routes qui correspondent à des composants.
Les routes sont les chemins d'accès aux composants. Par exemple, si on veut afficher le composant `Home` à la racine de notre application, on va définir une route `/` qui correspond à ce composant.

Pour installer le router, on va utiliser la commande suivante :

```bash
npm install react-router-dom
```

## Définition des routes

Le router est l'élément le plus haut de notre application. On va donc l'ajouter dans le composant `App` :

```javascript
import { RouterProvider, createBrowserRouter } from 'react-router-dom';
import routes from './routes';

// Create a router that uses the client side history strategy for
const router = createBrowserRouter(routes)

export default function App() {
  return (
    <RouterProvider router={router} />
  );
}
```

On va ensuite définir les routes de notre application dans un fichier `routes.jsx` :

```javascript
const routes = [
    {
        path: "/",
        element: <div>Home</div>,
    },
    {
        path: "/blog",
        element: <div>Blog</div>,
    },
    {
        path: "/contact",
        element: <div>Contact</div>,
    }
];

export default routes;
```

Notre application est maintenant capable de gérer les routes `/`, `/blog` et `/contact`. On peut tester le fonctionnement depuis le navigateur. On constate aussi que l'accès à une route inconnue affiche une page d'erreur.

## Navigation

react-router nous fournit des composants pour gérer la navigation. Ce composant est `Link`, il permet de créer des liens vers nos routes et gère la navigation sans recharger la page.

```javascript
import { Link } from "react-router-dom";

const routes = [
    {
        path: "/",
        element: <div>
            Home
            <nav>
                <Link to="/blog">Blog</Link>
                <Link to="/contact">Contact</Link>
            </nav>
        </div>,
    },
    {
        path: "/blog",
        element: <div>
            Blog
            <nav>
                <Link to="/blog">Blog</Link>
                <Link to="/contact">Contact</Link>
            </nav>
        </div>,
    },
    {
        path: "/contact",
        element: <div>
            Contact
            <nav>
                <Link to="/blog">Blog</Link>
                <Link to="/contact">Contact</Link>
            </nav>
        </div>,
    }
];

export default routes;
```

Il existe également un composant `NavLink` qui permet de gérer les liens actifs. Par exemple, si on est sur la route `/blog`, le lien vers `/blog` sera actif.
Par défaut, le composant `NavLink` ajoute la classe `active` sur le lien actif. On peut modifier cette classe en utilisant la prop `activeClassName`.

```javascript
import { NavLink } from "react-router-dom";

const routes = [
    {
        path: "/",
        element: <div>
            Home
            <nav>
                <NavLink to="/">Home</NavLink>
                <NavLink to="/blog">Blog</NavLink>
                <NavLink to="/contact">Contact</NavLink>
            </nav>
        </div>,
    },
    {
        path: "/blog",
        element: <div>
            Blog
            <nav>
                <NavLink to="/">Home</NavLink>
                <NavLink to="/blog">Blog</NavLink>
                <NavLink to="/contact">Contact</NavLink>
            </nav>
        </div>,
    },
    {
        path: "/contact",
        element: <div>
            Contact
            <nav>
                <NavLink to="/">Home</NavLink>
                <NavLink to="/blog">Blog</NavLink>
                <NavLink to="/contact">Contact</NavLink>
            </nav>
        </div>,
    }
];

export default routes;
```

## Route paramétrée

On peut définir des routes paramétrées. Par exemple, si on veut afficher un article de blog, on va définir une route `/blog/:id` qui correspond à un composant `BlogPost` :

```javascript
import { NavLink } from "react-router-dom";
import BlogPost from "./components/BlogPost";

const routes = [
    {
        path: "/",
        element: <div>
            Home
            <nav>
                <NavLink to="/">Home</NavLink>
                <NavLink to="/blog">Blog</NavLink>
                <NavLink to="/contact">Contact</NavLink>
            </nav>
        </div>,
    },
    {
        path: "/blog",
        element: <div>
            Blog
            <nav>
                <NavLink to="/">Home</NavLink>
                <NavLink to="/blog">Blog</NavLink>
                <NavLink to="/contact">Contact</NavLink>
            </nav>
        </div>,
    },
    {
        path: "/blog/:id",
        element: <BlogPost />,
    },
    {
        path: "/contact",
        element: <div>
            Contact
            <nav>
                <NavLink to="/">Home</NavLink>
                <NavLink to="/blog">Blog</NavLink>
                <NavLink to="/contact">Contact</NavLink>
            </nav>
        </div>,
    }
];

export default routes;
```

On peut ensuite récupérer le paramètre `id` dans le composant `BlogPost`, grâce au hook `useParams` :

```javascript
import { useParams } from "react-router-dom";

export default function BlogPost() {
    const { id } = useParams();

    return (
        <div>
            Article {id}
        </div>
    );
}
```

## Route imbriquée

La route imbriquée permet de définir des comportements communs à plusieurs routes. Par exemple, si on veut afficher un header et un footer sur toutes les pages de notre application, on va définir une route imbriquée.

Le composant `Outlet` permet ensuite d'inclure les routes imbriquées dans notre application.

```javascript
import { NavLink, Outlet} from "react-router-dom";
import BlogPost from "./components/BlogPost";

const routes = [
    {
        path: "/",
        element: <Root />,
        children: [
            {
                path: "blog",
                element: <div>Blog</div>,
            },
            {
                path: "blog/:id",
                element: <BlogPost />,
            },
            {
                path: "contact",
                element: <div>Contact</div>,
            }
        ]
    }
];

function Root() {
    return (
        <>
            <header>
                <nav>
                    <NavLink to="/blog">Blog</NavLink>
                    <NavLink to="/contact">Contact</NavLink>
                </nav>
            </header>
            <div className="content">
                <Outlet />
            </div>
            <footer>
                Footer
            </footer>
        </>
    );
}

export default routes;
```

## Route non trouvée

Afin de gérer les routes non trouvées, on va définir une route `*`. Selon que l'on positionne la route `*` au même niveau que les autres routes ou dans une route imbriquée, on va avoir un comportement différent.

```javascript

import { NavLink, Outlet} from "react-router-dom";
import BlogPost from "./components/BlogPost";

const routes = [
    {
        path: "/",
        element: <Root />,
        children: [
            {
                path: "blog",
                element: <div>Blog</div>,
            },
            {
                path: "blog/:id",
                element: <BlogPost />,
            },
            {
                path: "contact",
                element: <div>Contact</div>,
            },
            {
                path: "*",
                element: <div>Not Found</div>,
            }
        ]
    }
];

function Root() {
    return (
        <>
            <header>
                <nav>
                    <NavLink to="/blog">Blog</NavLink>
                    <NavLink to="/contact">Contact</NavLink>
                </nav>
            </header>
            <div className="content">
                <Outlet />
            </div>
            <footer>
                Footer
            </footer>
        </>
    );
}

export default routes;
```

Si on positionne la route `*` au même niveau que les autres routes, elle va s'afficher à chaque fois qu'une route n'est pas trouvée. Si on la positionne dans une route imbriquée, elle va s'afficher uniquement si aucune route imbriquée n'est trouvée.

## Loader   

La propriété `loader` permet d'executer une action avant d'afficher le composant. Par exemple, si on veut charger des données avant d'afficher le composant, on va utiliser cette propriété.

```javascript
import { NavLink, Outlet} from "react-router-dom";
import BlogPost from "./components/BlogPost";
import Blog from "./components/Blog";

const routes = [
    {
        path: "/",
        element: <Root />,
        children: [
            {
                path: "blog",
                element: <Blog />,
                loader: () => fetch("https://jsonplaceholder.typicode.com/posts?_limit=10"),
            },
            {
                path: "blog/:id",
                element: <BlogPost />,
            },
            {
                path: "contact",
                element: <div>Contact</div>,
            },
            {
                path: "*",
                element: <div>Not Found</div>,
            }
        ]
    }
];

function Root() {
    return (
        <>
            <header>
                <nav>
                    <NavLink to="/blog">Blog</NavLink>
                    <NavLink to="/contact">Contact</NavLink>
                </nav>
            </header>
            <Outlet />
            <footer>
                Footer
            </footer>
        </>
    );
}

export default routes;
```

La récupération des données se fait ensuite dans le composant `Blog` grâce au hook `useLoaderData` :

```javascript
import { useLoaderData } from "react-router";
import { NavLink } from "react-router-dom";

export default function Blog() {
    const posts = useLoaderData();
    return (
        <div>
            Blog
            <ul>
                {posts.map(post => (
                    <li key={post.id}>
                        <NavLink to={`/blog/${post.id}`}>{post.title}</NavLink>
                    </li>
                ))}
            </ul>
        </div>
    );
}
```

La récupération des données pouvant prendre du temps, on peut afficher un loader pendant le chargement des données. 

```javascript
import { Outlet, useNavigation } from "react-router";
import { NavLink } from "react-router-dom";
import BlogPost from "./components/blog-post";
import Blog from "./components/blog";


const routes =  [
    {
        path: "/",
        element: <Root />,
        children: [
            {
                path: "blog",
                element: <Blog />,
                loader: () => fetch("https://jsonplaceholder.typicode.com/posts?_limit=10"),
            },
            {
                path: "blog/:id",
                element: <BlogPost />,
            },
            {
                path: "contact",
                element: <div>
                    Contact
                </div>,
            }
        ],
    },
    {
        path: "*",
        element: <div>Not Found</div>,
    }
]

function Root() {
    const {state} = useNavigation();
    return (
        <>
            <header>
                <nav>
                    <NavLink to="/blog">Blog</NavLink>
                    <NavLink to="/contact">Contact</NavLink>
                </nav>
            </header>
            <div className="content">
                {state === "loading" && "Loading..."}
                <Outlet />
            </div>
            <footer>
                Footer
            </footer>
        </>
    );
}

export default routes;
```

### Lazy loading

L'inconvénient de la méthode précédente est que le composant `Blog` n'est affiché qu'une fois les données chargées. 

On peut utiliser la méthode `defer` pour afficher le composant `Blog` avant le chargement des données. 

```javascript
import { defer, NavLink, Outlet, useNavigation} from "react-router-dom";
import BlogPost from "./components/BlogPost";
import BlogLazy from "./components/BlogLazy";

const routes = [
    {
        path: "/",
        element: <Root />,
        children: [
            {
                path: "blog",
                element: <BlogLazy />,
                loader: () => {
                    const posts = fetch("https://jsonplaceholder.typicode.com/posts?_limit=10")
                        .then(response => response.json());
                    return defer({
                        posts,
                    });
                },
            },
            {
                path: "blog/:id",
                element: <BlogPost />,
            },
            {
                path: "contact",
                element: <div>Contact</div>,
            },
            {
                path: "*",
                element: <div>Not Found</div>,
            }
        ]
    }
];

function Root() {
    const {state} = useNavigation();
    return (
        <>
            <header>
                <nav>
                    <NavLink to="/blog">Blog</NavLink>
                    <NavLink to="/contact">Contact</NavLink>
                </nav>
            </header>
            <div className="content">
                {state === "loading" && "Loading..."}
                <Outlet />
            </div>
            <footer>
                Footer
            </footer>
        </>
    );
}

export default routes;
```

Grâce à la méthode `defer`, on ne retourne pas directement les données mais une promesse qui contient les données. 

Dans le composant utilisant les données, il faut donc faire évoluer le code pour gérer le cas où les données ne sont pas encore chargées.

```javascript
import { Suspense } from "react";
import { Await, useAsyncValue, useLoaderData } from "react-router";
import { NavLink } from "react-router-dom";

export default function BlogLazy() {
    const { posts } = useLoaderData();

    return (
        <div>
            Blog
            <Suspense fallback={<div>loading...</div>}>
                <Await
                    resolve={posts}
                >
                    <PostsList />
                </Await>
            </Suspense>
        </div>
    );
}

function PostsList() {
    const posts = useAsyncValue();

    return (
        <ul>
            {posts.map(post => (
                <li key={post.id}>
                    <NavLink to={`/blog/${post.id}`}>{post.title}</NavLink>
                </li>
            ))}
        </ul>
    );
}
```
