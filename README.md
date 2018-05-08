# Elixir Image

Docker Images para phoenix construidas con Alpine Linux.

## Generar imagen de docker.

```shell
docker build --tag codigobicentenario/phoenix:latest .
```

## Corremos un contenedor y entramos al shell.

```shell
docker run --rm -ti codigobicentenario/phoenix:latest sh
```
