## Capítulo III: Navegando entre páginas

NextJS propone una alternativa sencilla a React Router que nos permite navegar entre páginas.

### Componente \<Link/>
Este componente nos permite agregar enlaces en la página. Es parecido al anchor tag \<a/> de HTML.
En la prop "href" podemos definir la página a la que queremos trasladar al usuario.
La ventaja de utilizar estos "Link" es que NextJS puede cargar, además de los datos de la página que se encuentra abierta, la información de las páginas asociadas a esos links. Es decir, los datos de las páginas a las que llevan esos links se cargan con antelación. Esto permite que esas páginas se abran rápidamente cuando el usuario desee visitarlas.
```jsx
<Link href="/about">About</Link>

```
Las páginas a las que conducen los enlaces (como "about.jsx" en el ejemplo de arriba) deben estar almacenadas dentro del directorio **pages/**. Cada página no es más que un componente de React.


### Dynamic routing

Supongamos que tenemos un blog y que cada entrada del blog tiene un ID único. Dado que sería imposible crear una página (un archivo jsx) diferente para cada entrada, podemos crear una página única y asignarle un enlace dinámico.
Por ejemplo, podemos crear el siguiente directorio:

/pages/**post/[id]/index.js**

y vincular esa página con un Link:
```jsx
<Link href="/post/[id]" as="/post/first-post">
    First post
</Link>
```
De esta manera le indicamos a Next que el componente que debe renderizar al clickear en ese Link es el que está en el directorio /post/[id]/index.js, y que **el id que tendrá ese post es el que reemplazamos en la prop "as": first-post**.
Una vez hecho esto, podremos utilizar ese id dentro del componente Post (ver ejemplo en el parrafo siguiente).

### useRouter

El hook useRouter() nos devuelve un objeto del que podemos extraer, entre otras cosas, el valor que se reemplazó en la ruta de la página. Siguiendo con el ejemplo anterior, tenemos:
```jsx
// pages/post/[id]/index.js

const Post = () => {
    const router = useRouter();
    const {id} = router.query; // --> Obtenemos el ID

    return (
        <>
            <h1>Post: {id}</h1>
        </>
    );
};

export default Post;
```

### getInitialProps

getInitialProps es un método de ciclo de vida de los componentes (exclusivo de NextJS) que permite recuperar datos de una fuente externa antes de la renderización.
Por ejemplo, podríamos cargar los datos de una entrada para un componente Post de la siguiente forma:

```jsx
const Post = () => {
    ...

}

// Notar que puede recibir como prop la query que está en la URL (la ID)
Post.getInitialProps = async ({ query }) => {
    const res = fetch(`https://jsonplaceholder.typicode.com/post/${query.id}`);
    const post = res.json();

    return post;
}
```
Una vez que los datos de la entrada fueron recuperados, podemos retornarlos. NextJS se encargará de enviarlo al componente como una prop.
Entonces, si el resultado del fetch (almacenado en "post") es algo como esto: **{title: "...", body: "..."}** podemos aplicar desestructurazión y utilizarlo en el componente:

```jsx
const Post = ({ title, body }) => {
    return(
        <>
            <h1>{tile}</h1>
            <p>{body}</p>
        </>
    )
}
```

### Redireccionamiento

Una manera de redirigir al usuario a otra página es utilizando router.push("...").
```jsx
const router = useRouter();

const handleClick = (e) => {
    router.push("/dashboard");
}
```
Esto es útil si, por ejemplo, queremos enviar al usuario a una pagina determinada después de que ingresa sus datos y da click en un botón para autenticarse.
