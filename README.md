# docker-fundamentos
Curso de Docker

## Para construir la imagen con nombre/tag <name>
```
docker build -t sitioweb:latest . 
```

## Listar las imágenes
```
docker images
docker images --filter=reference='*:1.0'
```

## Eliminar una imagen
```
docker rmi -f  <imagen_id>
```

## Ejecutar la imagen de manera interactiva y eliminar (si es que existe) un contenedor creado previamente. Se crea un nuevo contenedor
```
docker run -it --rm -d -p 8080:80 --name <nombre_contenedor> <nombre_imagen>
```

## Listar los contenedores
```
docker ps
```

## Renombrar/reetiquetar imagen
```
docker image tag sitioweb:latest final/sitioweb:1.0
```

Algunos otros comando útiles:
Construir una imagen desde un archivo Dockerfile sin la caché: `docker build -t <nombre_de_imagen> . -no-cache`  
Eliminar todas las imágenes no utilizadas `docker image prune`  
Inicie sesión en Docker `docker login -u <nombredeusuario>`  
Publica una imagen en Docker Hub `docker push <nombre_usuario>/<nombre_imagen>`  
Buscar una imagen en Hub `docker search <nombre_imagen>`  
Extraer una imagen de un Docker Hub `docker pull <nombre_imagen>`  
Detener contenedor: `docker stop <id_contenedor>`  
Eliminar contenedor: `docker rm <id_contenedor>`  

## Crear 2 contenedores a partir de la misma imagen
Flask utiliza el puerto 5000
```
docker run -it --rm -d -p 8081:5000 --name web_api sitio_api
docker run -it --rm -d -p 8080:5000 --name web_api_2 sitio_api
```