# Phoenix Image

Docker Images para phoenix construidas con Ubuntu.

## Generar imagen de docker.

```shell
docker build --tag codigobicentenario/phoenix:ubuntu .
```

## Corremos un contenedor y entramos al shell.

```shell
docker run --rm -ti codigobicentenario/phoenix:ubuntu sh
```
