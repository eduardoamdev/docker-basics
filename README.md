# Conceptos de Docker

## ¿Qué es Docker?

Docker es una plataforma de software que le permite crear, probar e implementar aplicaciones rápidamente. Docker empaqueta software en unidades estandarizadas llamadas contenedores que incluyen todo lo necesario para que el software se ejecute, incluidas bibliotecas, herramientas de sistema, código y tiempo de ejecución. Con Docker, puede implementar y ajustar la escala de aplicaciones rápidamente en cualquier entorno con la certeza de saber que su código se ejecutará.

## Instalación de Docker en Fedora:

Para instalar docker en Ferdora seguiremos los siguientes pasos:

- Eliminar versiones antiguas de Docker:

```sh
sudo dnf remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-selinux \
                  docker-engine-selinux \
                  docker-engine
```

- Instalaremos el paquete dnf-plugins-core para manefar nuestros repositorios dnf.

```sh
sudo dnf -y install dnf-plugins-core
```

- El siguiente pasó será agregar el repositorio.

```sh
sudo dnf config-manager \
    --add-repo \
    https://download.docker.com/linux/fedora/docker-ce.repo
```

- Instalar Docker:

```sh
sudo dnf install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

- Arrancar Docker:

```sh
sudo systemctl start docker
```

- Comprobar el estado del contenedor:

```sh
sudo systemctl status docker
```

Podemos obtener información acerca de como instalar Docker en Fedora en el siguiente enlace: < https://docs.docker.com/engine/install/fedora/ >.

## Cómo descargar una imágen:

Si queremos utilizar los contenedores, por lo general, deberemos descargarlos de un repositorio para contenedores.

El repositorio público de contenedores más famoso es Docker Hub. Podemos acceder a él en < https://hub.docker.com/ >.

Una vez estemos en Docker Hub buscaremos la funcionalidad que necesitamos. Para el ejemplo voy a buscar un contenedor de NodeJS.

Una vez hayamos encontrado la imágen que estamos buscando copiaremos el comando docker pull que nos indica. En este caso será < docker pull node >.

Ejecutaremos el comando en nuestra terminal para descargar la imágen de Docker.

Si, después de que termine el proceso ejecutamos de nuevo el comando < docker images >, la nueva imágen del repositorio node aparecerá listada.

Si queremos una versión completa también podemos especificarlo en el mismo comando docker pull. En el caso que estamos utilizando como ejemplo vamos a intalar la versión 16 de node. Para ello ejecutamos < docker pull node:16 >.

## Cómo eliminar una imágen:

Para borrar una imágen ejecutaremos el comando < docker image rm > pasándole como argumento el nombre de la imágen. En el caso de tener varias imágenes procedentes del mismo repositorio especificaremos el TAG de la siguente manera: < docker image rm node:16 >. En caso de que tuviéramos tan solo una imágen de node ejecutaríamos < docker image rm node >.
