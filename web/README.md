
# Source

https://opensource.com/article/18/3/start-blog-30-minutes-hugo

https://dev.to/dgavlock/creating-a-hugo-site-on-github-pages-3cjo


# Hugo documentation

## Install

Para instalar

```
sudo apt-get install hugo
hugo version
```

### Ultima version


[Hugo releases](https://github.com/gohugoio/hugo/releases)

Download example: hugo_extended_0.55.5_Linux-64bit.deb 



## New blog

Para crear un nuevo blog

```
hugo new site awesome-blog
cd awesome-blog
```

### New theme

```
git clone https://github.com/avianto/hugo-kiera themes/kiera
cp themes/kiera/exampleSite/config.toml .
cp themes/kiera/archetypes/* archetypes/
```

### New post

```
mkdir content/posts
hugo new posts/first-post.md
gedit content/posts/first-post.md
```

Luego, editar el archivo `first-post.md` con el siguiente contenido

```
+++
title = "First Post"
date = 2018-03-03T13:23:10+01:00
draft = false
tags = ["Getting started"]
categories = []
+++

Hello Hugo world! No more excuses for having no blog or documentation now!
```

### New menu option


En el archivo `config.toml`, agregar lo siguiente al final del archivo

```
[[menu.main]]
    name = "Home" #Name in the navigation bar
    weight = 10 #The larger the weight, the more on the right this item will be
    url = "/" #URL address
[[menu.main]]
    name = "Posts"
    weight = 20
    url = "/posts/"
```

## Run server


### Local server

Para correr la pagina en el serivor local

```
hugo server -D
```

Open your browser and enter: `http://localhost:1313/`

### External server

Averiguar

