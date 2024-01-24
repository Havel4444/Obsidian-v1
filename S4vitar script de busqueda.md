[[index]]
[[index_linux]]

# ASD

Base de datos:
- En este caso se usara la base de datos de una pagina que contiene informacion de maquinas. 

Paso a paso:
1. Solicitud http.
```sh
# El siguiente comando es el metodo comun para recupera datos de un servidor.
curl -s -X GET https://htbmachines.github.io/ | batcat
# curl: Herramiente de transferencia de datos.
# -s: Simplificar informacion enviada.
# -X: Seleccion del tipo de metodo.
# GET: Metodo predeterminado para pedir datos.
```
1. Salida de la solicitud http.
```sh
# Estructura de una pagina web. La salida que obtuviste parece ser el contenido HTML de la página web ubicada en la URL https://htbmachines.github.io/.
<!doctype html><html lang="en"><head><meta charset="utf-8"/><meta name="viewport" content="width=device-width,initial-scale=1"/><meta name="description" content="HTB Machines"/><meta name="author" content="rroderickk"/><meta name="author" content="CheatModes4"/><meta name="twitter:site" content="@cheatmodes4"/><meta name="twitter:creator" content="@cheatmodes4"/><meta property="og:site_name" content="github.com/rroderickk"/><meta property="og:site_name" content="rroderickk.github.io"/><meta property="og:type" content="website"/><link rel="icon" type="image/x-icon" href="/public/82fe1035e8b102375254.jpg"><link rel="stylesheet" href="//cdn.jsdelivr.net/npm/hack-font@3/build/web/hack.css"><title>HTB Machines - Search Engine</title><script defer="defer" src="/bundle.js"></script></head><body><main id="root"></main></body></html>
# <meta> y <title>: Estos elementos proporcionan información sobre la página, como el conjunto de caracteres, la descripción, el autor y el título. En este caso, el título es "HTB Machines - Search Engine".
# <link>: Este elemento enlaza recursos externos, como la hoja de estilo y el ícono de la página.
# <script>: Aquí se carga un script llamado `bundle.js` desde la raíz del servidor (`/bundle.js`). Los scripts se utilizan para agregar funcionalidad dinámica a la página.
# <body>: Esta es la sección del cuerpo del HTML, donde se coloca el contenido visible de la página. En este caso, parece estar vacío (`<main id="root"></main>`), y el contenido real puede generarse dinámicamente mediante JavaScript.
```















