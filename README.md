# Django-CoreUI

Un par de contenedores docker, corriendo un backend django y frontend coreui

## Comenzando 🚀

Tener en cuenta que el ejemplo usa, **docker** y **docker-compose** para deployar este proyecto.

## Ejecución 📦

Construir las imagenes.

```
$ docker-compose build
```

Deployar los contenedores.

```
$ docker-compose up
```

Tambien puedes usae el siguiente comando si tiene **swarm** instalado.

```
$ docker stack deploy docker_coreui -c .\docker-compose.yml
```

## Construido con 🛠️

* [django](http://www.dropwizard.io/1.0.2/docs/) - El framework web usado
* [coreiu](https://github.com/coreui/coreui) - Libreria Open Source 
* [docker](https://www.docker.com) - Usado para el deploy

## Autores ✒️

* **Moisés Jiménez** - *Trabajo Inicial* - [nanyhel](https://github.com/nanyhel)

---
⌨️ con ❤️ por [nanyhel](https://github.com/nanyhel) 😊