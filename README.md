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

## Imágenes y recursos multimedia

Todo el contenido multimedia que queramos añadir a nuestras páginas debe estar previamente almacenado en un directorio de nuestro repositorio, para adjuntar, por ejemplo, una foto, tenemos que utilizar la url de la foto una vez que esté en el repositorio, ejemplo 

```
![imagen](https://github.com/vaeruiz/iaw-jekyll/blob/main/imagenes/captura1.png?raw=true)
```

En este caso, las imágenes que he utilizado las he cogido directamente de los readme de los repositorios correspondientes a las prácticas.
