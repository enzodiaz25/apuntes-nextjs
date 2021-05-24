## Section 1 - Introduction

Link to course: https://masteringnextjs.com/ <br/>
Link to video: https://www.youtube.com/watch?v=uQeidE2LA1s&list=PL6bwFJ82M6FXjyBTVi6WSCWin8q_g_8RR <br/>

Next.js es un framework construido sobre la base de la librería React.
En la opinión de Robinson, Next es similar a create-react-app, framework que levanta en un segundo una app nueva sin necesidad de configuración pero Next ofrece más beneficios como un routing más dinámico, integración con Typescript, entre otros.

-> *Beneficios del framework*
- Permite crear sitios estáticos: Escribiendo con la sintáxis de React (JSX) el compilador de Next se va a encargar de convertirlo en HTML, CSS, JS básico. Lo cual nos da como beneficio que es **mucho más rápido** porque evita crear y cargar todo el "ecosistema" de la React App.

- Permite mixear estático con dinámico: Sumado a lo dicho en el punto anterior, nos permite agregar formularios, traer información desde APIS, agregar contadores dinámicos, etc.

- Configuración cero: Evitamos configurar Babel, Webpack, etc. Viene todo listo y soporta todos los navegadores.

- Popularidad: Viene con un crecimiento sostenido desde hace un tiempo.

- Server-Side Rendering: Dos grandes beneficios: En la velocidad y en el SEO. (Existen dos formas de renderizado: desde el lado del cliente -Client Side Rendering- o desde el servidor - Server Side Rendering o SSR-).

- Ruteo / File-System Routing: Para React teníamos que usar React-Router. En este framework es mas simple, creamos un archivo nuevo y el ruteo se hace solo.

-> *Getting started* <br/>

En la consola: npx create-next-app nombreDelArchivo <br/>
yarn dev / npm run dev → para correrla.

-> *Cual me conviene? Next vs Gatsby vs CRA* <br/>

Robinson recomienda Next principalmente porque es el único que cuenta con Server-Side Rendering. <br/>
Gatsby es más popular para páginas estáticas y usa GraphQL.<br/>
Y sobre C.R.A. reconoce que es un muy buen framework, pero no tiene SSR y el routing es más trabajoso.
