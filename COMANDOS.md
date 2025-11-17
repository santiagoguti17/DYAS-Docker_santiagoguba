# Guía de Comandos - Taller Docker

## Proyecto hello-world

### Construir la imagen
```bash
cd hello-world
docker build -t helloapp:v1 .
```

### Ver las imágenes
```bash
docker images
```

---

## Proyecto friendlyhello

### 1. Construir la imagen
```bash
cd friendlyhello
docker build -t friendlyhello .
```

### 2. Probar el contenedor individualmente
```bash
docker run --rm -p 4000:80 friendlyhello
```
Visita: http://localhost:4000

### 3. Usar Docker Compose (versión básica)
```bash
docker compose -f docker-compose.yaml up
```
Para detener: `Ctrl+C` y luego `docker compose down`

### 4. Usar Docker Compose con balanceo de carga
```bash
docker compose -f docker-compose-loadbalancer.yaml up -d --scale web=5
```

Ver los contenedores:
```bash
docker ps
```

Visitar la aplicación: http://localhost:4000
Dashboard de Traefik: http://localhost:8080

Para detener:
```bash
docker compose -f docker-compose-loadbalancer.yaml down
```

---

## Compartir imágenes en Docker Hub

### 1. Crear cuenta en Docker Hub
Visita: https://hub.docker.com

### 2. Hacer login
```bash
docker login
```

### 3. Etiquetar la imagen con tu usuario
```bash
docker build -t TU-USUARIO/friendlyhello .
```

### 4. Subir la imagen
```bash
docker push TU-USUARIO/friendlyhello
```

### 5. Hacer logout (recomendado)
```bash
docker logout
```

---

## Ejercicios

### Ejercicio 1: Usar tu imagen en vez de build

1. Sube tu imagen a Docker Hub (ver arriba)
2. Edita `docker-compose-ejercicio1.yaml` y reemplaza `<tu-usuario>` con tu usuario de Docker Hub
3. Ejecuta:
```bash
docker compose -f docker-compose-ejercicio1.yaml up -d --scale web=5
```

### Ejercicio 2: Usar imagen de un compañero

1. Pide a un compañero su usuario de Docker Hub
2. Edita `docker-compose-ejercicio2.yaml` y reemplaza `<usuario-compañero>`
3. Ejecuta:
```bash
docker compose -f docker-compose-ejercicio2.yaml up -d --scale web=5
```

---

## Comandos útiles

### Ver contenedores en ejecución
```bash
docker ps
```

### Ver todas las imágenes
```bash
docker images
```

### Detener todos los contenedores
```bash
docker compose down
```

### Limpiar contenedores detenidos
```bash
docker container prune
```

### Limpiar imágenes no usadas
```bash
docker image prune
```

### Ver logs de un contenedor
```bash
docker logs CONTAINER_ID
```

### Eliminar datos de volúmenes
```bash
rm -rf friendlyhello/data
```
