# Creación de un sitio web estático con MkDocs y GithubPages

## Preparando la máquina

Esto lo podemos hacer en cualquier máquina, debemos tener instaladas las herramientas de github docker y docker-compose.

## Preparando nuestro repositorio y la estructura del directorio

En github, tenemos que crearnos un repositorio con el nombre que queramos. En nuestra máquina debemos crearnos la siguiente estructura de directorios:

```
└── proyecto
    ├── docs
    │   ├── about.md
    │   └── home.md
    └── mkdocs.yml
```

**En la carpeta docs irán las páginas que queremos publicar.**

El archivo mkdocs.yml deberá tener de base el siguiente contenido:

```
site_name: A PLACE FOR PACR

nav:
    - Principal: index.md
    - Acerca de: about.md
    - Pagina-prueba: prueba.md

theme: material
```

- **site name.** Especifica el nombre que tendrá nuestro sitio web.

- **nav:** Este apartado es importante, creará un pequeño menú en el que irán nuestras páginas, como se ve, a excepción de las dos primeras páginas (esas tienen que estar por defecto) primero ponemos un - seguido de el nombre que se mostrará para la página, a continuación se le pone : y se escribe el nombre que tiene el archivo Markdown que representa a la página, este archivo debe estar en la carpeta docs.

- **theme.** Es el tema que vamos a utilizar para nuestra página, podemos desarrollarlo con más opciones que podemos encontrar en la [documentación](https://www.mkdocs.org/#mkdocs) oficial.

## Probando nuestro sitio de forma local

Con toda la estructura creada podemos lanzar un contenedor servidor que nos permita ver en tiempo real los cambios que hagamos. Este servidor nos sirve de forma local, aún no podremos lanzar la página a Github.

Lanzamos el contenedor local:

> docker run --rm -it -p 8000:8000 -v "$PWD":/docs squidfunk/mkdocs-material

Si ingresamos a localhost:8000 podremos ver nuestro sitio y empezar a añadirle contenido.

## Lanzando nuestro sitio a Github Pages

Teniendo nuestro sitio hecho, para lanzarlo a Github haremos lo siguiente:

1. Hacer que nuestro directorio proyecto sea un repositorio local.

> git init

2. Linkear nuestro repositorio local con el repositorio que corresponde a MkDocs en Github.

> git remote add origin url_del_directorio

3. Lanzar el contenedor que nos subirá los archivos a Github. Este contenedor nos pedirá nuestros credenciales de usuario.

> docker run --rm -it -v ~/.ssh:/root/.ssh -v "$PWD":/docs squidfunk/mkdocs-material gh-deploy

Después de iniciar la sesión se subirá nuestra infraestructura convertida al repositorio de Github, es cuestión de tiempo que podamos acceder a nuestro sitio y ver el contenido que hemos creado.

**Los pasos 1 y 2 solo son necesarios hacerlos una vez, a no ser que cambiemos de máquina o perdamos el repositorio que hemos convertido en local.**

## Imágenes y recursos multimedia

Todo el contenido multimedia que queramos añadir a nuestras páginas debe estar previamente almacenado en un directorio de nuestro repositorio, para adjuntar, por ejemplo, una foto, tenemos que utilizar la url de la foto una vez que esté en el repositorio, ejemplo 

```
![imagen](https://github.com/vaeruiz/iaw-jekyll/blob/main/imagenes/captura1.png?raw=true)
```

En este caso, las imágenes que he utilizado las he cogido directamente de los readme de los repositorios correspondientes a las prácticas.
